# .gitignore 的作用  
1.过滤项目里 “自动生成的没用文件”（比如日志、系统文件、临时数据）； 
2.让 Git 仓库只保留代码、文档等有用内容，避免仓库杂乱。

# Windows 下 GitHub SSH 密钥的配置与测试全流程
一. 核心作用
让你的电脑和 Git 仓库（GitHub/Gitee 等）建立安全的免密码连接，拉取 / 推送代码不用反复输账号密码。
二. 原理（简单版）
生成密钥对：包括私钥（存在自己电脑，不能泄露）和公钥（传到 Git 仓库）；
验证逻辑：Git 仓库用你的公钥加密信息，只有你电脑的私钥能解密，以此确认 “是你本人操作”。
三. 优势
免密：配置后不用再输密码，更高效；
安全：密钥加密比明文密码更安全；
稳定：避免 HTTPS 方式的连接超时 / 密码缓存失效问题
四. 如何创建密钥对
1.打开 git bash 输入：ssh-keygen 按回车  
2.查看C:\用户\Administrator\.ssh  
3.第一个是私钥，第二个文件后缀为 .pub 是公钥(需要配置到git hub 账户)  
五. 如何配置git hub 公钥  
1.登录git hub 账号点击 Settings 然后点击SSH and GPG keys 之后点击 new SSH key  
2.把刚才创建的公钥复制到 Key 下面填写处，注意是第二个文件后缀为 .pub 是公钥，用记事本打开全选复制粘贴，之后填写标题比如给小李的公匙，最后添加 SSH 密钥（注意：添加密钥需要验证密码，如有此环节验证即可）  
六.测试连接  
1.测试密钥是否正常：ssh -T git@github.com  

2.然后一般会出现（不出现最好）  ssh: connect to host github.com port 22: Connection timed out 报错，不同协议走的 “网络端口” 不一样，你的网络放行了 HTTPS 的 443 端口，但拦住了 SSH 的 22 端口，所以 SSH 连接不行，但不影响 HTTPS 方式的操作。
解决办法如下：
方法一：
编辑 SSH 的 config 文件
找到本地的 .ssh 文件夹（路径：C:\Users\你的用户名\.ssh）；
打开（或新建）名为 config 的文件（无后缀名，出现是否会损坏文件选是）；
在文件里添加以下内容并保存：
plaintext
Host github.com
  HostName ssh.github.com
  Port 443
  User git
重新测试 SSH 连接
运行
ssh -T git@github.com(测试密钥是否正常)
关键说明
这个配置会让你的 SSH 连接强制走 443 端口（代替被屏蔽的 22 端口），而 GitHub 是支持 SSH 通过 443 端口连接的；  

方法二： 
如果你的网络需要通过代理访问外网，给 SSH 配置代理，（以常用的 Clash 代理为例）：
打开 .ssh/config 文件，添加代理配置（替换成你的代理地址和端口）：
Host github.com
  HostName ssh.github.com
  Port 443
  User git
  ProxyCommand connect -S 你的代理地址:代理端口 %h %p
正常情况会出现：
第一次连接会提示 “是否确认指纹”，输入 yes 回车；
最终返回 Hi 你的GitHub用户名! You've successfully authenticated, but GitHub does not provide shell access. → 公钥连接成功！

3.保持代理工具正常运行（我的 config 依赖代理走 443 端口），如果代理关闭 / 端口变了，需要同步更新 .ssh/config 里的 ProxyCommand 配置；
不要删除 .ssh 文件夹里的密钥文件（id_rsa 私钥、id_rsa.pub 公钥）和 known_hosts 文件，删除后需要重新配置。