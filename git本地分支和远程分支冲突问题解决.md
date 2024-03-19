# git本地分支和远程分支冲突问题解决

## 1、failed to push some refs 报错

```
git push -u origin main
To https://github.com/xxxx.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/xxxx.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

### 解决方案：

错误消息表明本地分支位于远程分支后面，并且 Git 阻止我推送更改以避免覆盖远程更改。如果其他人已将提交推送到本地没有的远程分支，则可能会出现这种情况。若要解决此问题，需要先将远程更改集成到本地分支中，然后才能推送更改。以下是步骤：

#### 1.**Fetch the Remote Changes**: 

First, you need to fetch the changes from the remote repository without merging them into your local branch. This ensures that you have the latest changes from the remote repository but keeps your local branch unchanged.
获取远程更改：首先，你需要从远程存储库获取更改，而无需将它们合并到本地分支中。这可确保你拥有来自远程存储库的最新更改，但保持本地分支不变。

```
git fetch origin
```

#### 2.**Merge or Rebase**: 

After fetching the changes, you have two main options to integrate the remote changes into your local branch:
合并或变基：获取更改后，你有两个主要选项将远程更改集成到本地分支中：

```
- **Merge**: This will create a new merge commit in your local branch that combines your changes with the changes from the remote branch.
git merge origin/main
```

- **Rebase**: 
- This will replay your local commits on top of the remote changes, creating a linear history. This is a cleaner approach but can be more complex if there are conflicts.
  变基：这将在远程更改之上重放你的本地提交，从而创建线性历史记录。这是一种更简洁的方法，但如果存在冲突，可能会更复杂。

```
git rebase origin/main
```

If you choose to rebase and encounter conflicts, you'll need to resolve them manually. After resolving conflicts, continue the rebase with `git rebase --continue`.
如果选择变基并遇到冲突，则需要手动解决它们。解决冲突后，继续使用 `git rebase --continue` .

#### 3.**Push Your Changes**: 

Once you've integrated the remote changes into your local branch, you can push your changes to the remote repository. If you've rebased, you might need to force push, but be cautious as this can overwrite history on the remote repository.
推送更改：将远程更改集成到本地分支后，可以将更改推送到远程存储库。如果已变基，则可能需要强制推送，但要小心，因为这可能会覆盖远程存储库上的历史记录。

```
git push origin main
```

If you've merged and there are no conflicts, a simple push should work. If you've rebased and need to force push, use:
如果已合并并且没有冲突，则简单的推送应该可以工作。如果你已重新定位并需要强制推送，请使用：

```
git push -f origin main
```

Remember, force pushing (`git push -f`) should be used with caution, especially in shared repositories, as it can overwrite history and potentially cause issues for other collaborators. Always communicate with your team before force pushing.
请记住，应谨慎使用强制推送 （ `git push -f` ），尤其是在共享存储库中，因为它可能会覆盖历史记录并可能给其他协作者带来问题。在强制推动之前，请务必与你的团队沟通。



---



## 2、Empty reply from server报错 or Timed out报错

```
$ git push -u origin main
fatal: unable to access 'https://github.com/HuuuuuuO/blog.git/': Empty reply from server
```

或者为：

```
$ git push -f origin main
fatal: unable to access 'https://github.com/HuuuuuuO/blog.git/': Failed to connect to github.com port 443: Timed out
```

### 解决方案：

#### 1.检查 SSH 访问：

如果使用 SSH 连接到 GitHub，请确保将 SSH 密钥正确添加到 GitHub 帐户。您可以使用命令 `ssh -T git@github.com` 测试 SSH 连接。如果您收到成功的身份验证消息，则您的 SSH 设置是正确的。

```
ssh -T git@github.com
```



#### 2.使用 SSH 而不是 HTTPS：

如果当前使用 HTTPS 推送到 GitHub，请尝试切换到 SSH。这有时可以绕过与 HTTPS 连接相关的问题。您可以将远程 URL 更改为通过命令 `git remote set-url origin git@github.com:HuuuuuuO/blog.git` 使用 SSH。

```
`git remote set-url origin git@github.com:HuuuuuuO/blog.git`
```



#### 3.进行push

```
$ git push origin main
```

成功。