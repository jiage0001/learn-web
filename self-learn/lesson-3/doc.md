# 网络问题解决笔记（Git代理+浏览器登录）

## 一、问题现象
- Git操作（如`git push`）超时、`ping github.com`请求失败
- 浏览器登录目标平台时出现异常（加载失败、状态错误）


## 二、原因分析
1. 代理配置后，代理工具未启动/端口不匹配
2. 浏览器缓存、DNS解析冲突，或登录状态异常（不同浏览器环境独立）


## 三、解决步骤
### 1. 校验Git代理配置
执行命令查看当前代理：
```powershell
git config --global --get http.proxy
git config --global --get https.proxy