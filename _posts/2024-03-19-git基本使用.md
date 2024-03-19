# git基本使用

Git是一个分布式版本控制系统，用于跟踪文件的更改，协作开发，以及管理项目的版本。

![v2-3bc9d5f2c49a713c776e69676d7d56c5_r](git基本使用.assets/v2-3bc9d5f2c49a713c776e69676d7d56c5_r.png)

index：暂存区

workspace：工作区

respository：本地仓库

remote：远程仓库

---

## 一个完整的简单的git推送流程

```
ssh -T git@github.com
git init
```

```
git add .
git commit -m “update”
git push -u origin main
```

---

以下是Git的基本操作：

## 创建仓库

- **初始化仓库**：`git init` 用于在当前目录下创建一个新的Git仓库。
- **克隆仓库**：`git clone <repository>` 用于从远程仓库克隆一个项目到本地。

## 基本操作

- **添加文件到暂存区**：`git add <file>` 或 `git add .`（添加所有文件）。
- **提交更改**：`git commit -m "commit message"` 将暂存区的更改提交到本地仓库。
- **查看状态**：`git status` 显示工作区和暂存区的状态。
- **查看差异**：`git diff` 显示工作区与暂存区的差异。
- **查看提交历史**：`git log` 显示提交历史。

## 分支与合并

- **创建分支**：`git branch <branch-name>` 创建一个新分支。
- **切换分支**：`git checkout <branch-name>` 切换到指定分支。
- **合并分支**：`git merge <branch-name>` 将指定分支合并到当前分支。

## 远程仓库操作

- **添加远程仓库**：`git remote add <remote-name> <repository>` 添加远程仓库。
- **推送到远程仓库**：`git push <remote-name> <branch-name>` 将本地分支推送到远程仓库。
- **从远程仓库拉取**：`git pull <remote-name> <branch-name>` 从远程仓库拉取指定分支的更改。

## 配置Git

- **配置用户信息**：`git config --global user.name "your name"` 和 `git config --global user.email "youremail@example.com"` 设置全局用户名和邮箱。
- **配置差异分析工具**：`git config --global merge.tool vimdiff` 设置差异分析工具。
- **配置彩色输出**：`git config --global color.ui auto` 配置Git命令输出为彩色。

## 其他操作

- **删除文件**：`git rm <file>` 从工作区和暂存区删除文件。
- **重命名文件**：`git mv <old-name> <new-name>` 在工作区和暂存区中重命名文件。
- **查看未跟踪文件**：`git status --ignored` 显示未跟踪的文件。

## 高级操作

- **撤销提交**：`git revert <commit>` 撤销指定提交。
- **重置到指定提交**：`git reset --hard <commit>` 将当前分支重置到指定提交。
- **查看差异**：`git diff <commit1>..<commit2>` 查看两个提交之间的差异。

这些是Git的基本操作，可以帮助你更好地管理项目的版本控制。