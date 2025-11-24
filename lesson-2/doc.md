# 技术速记笔记：Linux 与 Git 核心命令

## 一、Linux 基础命令

| 命令    | 功能说明                | 示例                                                                                                                                                |
| ------- | ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mkdir` | 创建文件夹              | `mkdir project`                                                                                                                                     |
| `cd`    | 切换工作目录            | `cd /d/learn-web`（绝对路径）<br>`cd lesson-1`（相对路径）<br>`cd ..`（返回父目录）<br>`cd ~`（切换到用户主目录）<br>`cd -`（切换到上一次工作目录） |
| `ls`    | 罗列当前目录文件/文件夹 | `ls`（罗列正常文件）<br>`ls -a`（罗列所有文件，包括隐藏文件）                                                                                       |
| `pwd`   | 显示当前目录的绝对路径  | `pwd`                                                                                                                                               |
| `rm`    | 删除文件/文件夹         | `rm file.txt`（删除文件）<br>`rm -rf dir/`（强制删除文件夹及内容）                                                                                  |

## 二、Git 版本控制命令

### 1. 仓库初始化与状态查看

- **初始化本地仓库**：

  ```bash
  git init
  ```

  作用：在当前目录创建 `.git` 隐藏文件夹，初始化 Git 版本控制。

- **查看仓库状态**：
  ```bash
  git status
  ```
  作用：查看文件跟踪状态、分支信息、提交记录等。  
  输出说明：
  - `On branch main`：当前处于 `main` 主分支。
  - `No commits yet`：暂无提交记录。
  - `Untracked files`：列出未被 Git 跟踪的文件/文件夹，需通过 `git add` 命令纳入跟踪。

### 2. 文件跟踪与提交

- **跟踪单个文件/文件夹**：

  ```bash
  git add index.html  # 跟踪单个文件
  git add lesson-1/   # 跟踪整个文件夹
  ```

- **跟踪所有文件**：

  ```bash
  git add .
  ```

- **提交跟踪的文件到本地仓库**：
  ```bash
  git commit -m "提交说明：新增登录页面"
  ```
  作用：将暂存区的文件永久保存到本地仓库，生成版本记录。

### 3. 分支管理

- **查看所有分支**：

  ```bash
  git branch
  ```

  作用：列出本地所有分支，当前分支以 `*` 标记。

- **创建并切换分支**：

  ```bash
  git checkout -b 新分支名
  ```

  示例：`git checkout -b feature-login`（创建并切换到 `feature-login` 分支）

- **切换已有分支**：

  ```bash
  git checkout 分支名
  ```

  示例：`git checkout mai
n`（切换到 `main` 主分支）

  ### 4. 版本回退与撤销

- **从跟踪状态撤销文件（
  回到未跟踪）**：

  ```bash
  git reset 文件名
  ```

  示例：`git reset index.html`

- **撤销工作区修改（恢
  复到上次提交状态）**：
  ```bash
  git restore 文件名
  ```
  示例：`git restore index.html`

### 5. 远程仓库交互（拓展）

- **关联远程仓库**：

  ```bash
  git remote add origin 远程仓库地址
  ```

  示例：`git remote add origin https://github.com/yourname/learn-web.git`

- **推送本地分支到远程**：

  ```bash
  git push -u origin 分支名
  ```

  示例：`git push -u origin main`

- **拉取远程仓库更新**：
  ```bash
  git pull origin 分支名
  ```

通过以上整理，你可以更系统地掌握 Linux 目录操作和 Git 版本控制的核心命令，后续在项目开发中可根据场景灵活运用~
