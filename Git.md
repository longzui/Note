# git如何安全回滚

## 1.常用命令

- 查看全局配置

  ```python
  git config --global -l
  ```

- 设置全局代理设置

  示例7890端口是代理软件端口，按个人情况修改。

  ```python
  git config --global http.proxy 127.0.0.1:7890
  git config --global https.proxy 127.0.0.1:7890
  ```

- 已有设置情况修改代理项

  ```python
  git config --global --unset http.proxy
  git config --global --unset https.proxy
  ```





## 2.本地回滚

- 方法一：git  reset

  ```python
  // 回滚到上次提交状态，保留本地修改。
  git reset HEAD~1
  git reset <commit>
  
  // 回滚,但不保留本地修改
  git reset --hard <commit>
  
  // 从暂存区移除文件
  git reset file
  
  // 重置暂存区
  git reset
  
  ```

  使用 reset 命令时应该格外注意，因为如果你拿它来操作提交历史的话，提交历史是无法恢复的。因此它通常被用来撤销缓存区和工作目录的修改。不管是哪种情况，它应该只被用于本地修改（自己本地的缓存区或者尚未 push 到远程分支的提交历史），**不要用来重设和他人共享的提交历史**。

- 方法二：git revert

  被用来撤销一个已经提交的快照。生成一个撤消了引入的修改的新提交，然后应用到当前分支，并不会删除原来的历史记录。

  实现上和 reset 是完全不同的：** reset 是直接从历史中移除某个提交，而 revert 是生成一个新提交。`git revert`可以将提交历史中的任何一个提交撤销，而`git reset`会把历史上某个提交及之后所有的提交都移除掉。

  ```python
  git revert <commit>
  ```