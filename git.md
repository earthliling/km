# Git #
## git 概念
- 工作区（working Directory、working tree）
  - 项目签出后在本地的保存的版本
  - 通过--working-tree参数或GIT_WORK_TREE环境变量指定
- 版本库（.git directory、Repository）
  - Git为项目保存的元信息和对象数据库。
  - 通过--git-dir参数或GIT_DIR环境变量指定
- 暂存区（Staging Erea、Index）
  - 文件在提交到版本库之前存放信息的区域
  - 在工作区修改文件
  - 通过add命令将文件放入暂存区
  - 通过commit命令把暂存区的所有内容提交到当前分支

## git 常用操作命令
- 创建仓库
  - 创建目录，这个目录里面的所有文件都可以被Git管理起来。
- 初始化仓库
  - 在目录中执行命令：git init
- 添加文件到仓库
  - git add files
  - git commit -m "message"
- 查看仓库状态
  - git status
- 对比差异
  - git diff file
- 提交更新
  - 同添加文件的两步：add 和 commit
- 查看历史记录
  - git log
  - 显示每次提交COMMIT ID等信息
- 回退版本
  - git中使用HEAD代表当前版本，HEAD^代表上一个版本，往上第N个版本表示为：HEAD~N
  - git reset --hard HEAD^
  - git reset --hard COMMIT_ID
  - 用git log可以查看提交历史，以便确定要回退到哪个版本
  - 用git reflog查看命令历史，以便确定要回到未来的哪个版本
- 历史命令
  - git reflog
  - 可以通过历史命令找到提交的COMMIT ID
- 撤销修改
  - git checkout -- file其实是用版本库里的版本替换工作区的版本，将文件在工作区的修改全部撤销，包括：
    - 自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
    - 已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
    - 让这个文件回到最近一次commit或add时的状态。
  - git reset HEAD file把暂存区的修改撤销掉（unstage），重新放回工作区。
- 删除文件
  - git rm file
  - 如果误删除了，可以通过git checkout把误删的文件恢复到最新版本
  -

## 远程仓库
- Git是分布式版本控制系统，通过“克隆”获得的版本库与原始库一样，没有主次之分。
- 一般情况下，一台电脑充当服务器的角色，每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。
- 本地仓亏克隆到远程
  - 在远程创建一个仓库，且不用初始化
  - 在本地仓库运行如下命令，关联远程仓库
    - git remote add origin git@github.com:username/test.git
  - 将本地库推送到远程库
    - git push -u origin master
    - 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
  - 推送最新修改
    - git push origin master
- 远程克隆岛本地
  - 在远程创建一个仓库，并初始化
  - 在本地仓库运行如下命令，克隆远程仓库
    - git clone git@github.com:username/test.git

## 分支管理
- 主分支master，无其他分支时，HEAD指向master，master指向提交
- 因为创建、合并和删除分支非常快，所以Git鼓励你使用分支完成某个任务，合并后再删掉分支，这和直接在master分支上工作效果是一样的，但过程更安全。
- 创建分支dev，HEAD指向dev，dev指向提交
- 创建分支：git branch dev
- 切换分支：git checkout dev
- 查看分支情况：git branch，列出所有分支，当前分支前面会标一个*号
- 合并分支：git merge dev，合并指定分支到当前分支，所以操作前切回master分支（git checkout master），可以指定--no-ff参数，表示禁用Fast forward。
- 删除分支：git branch -d dev，合并完成后即可删除指定分支，没有被合并过的分支，可以通过git branch -D name强行删除。
- 当Git无法自动合并分支时，就必须解决冲突：直接修改冲突文件，然后add和commit。
- 通过命令查看分支合并情况：git log --graph --pretty=oneline --abbrev-commit
- 工作现场保存和恢复
  - 保存工作现场：git stash
  - 恢复工作现场：git stash pop 或者 git stash apply 、git stash drop
  - 查看工作现场：git stash list
- 多人协作
  - 查看远程库信息：git remote -v
  - 推送本地分支：git push origin branch-name
  - 获取远程分支：git pull
  - 本地创建和远程分支对应的分支：git checkout -b branch-name origin/branch-name
  - 建立本地分支和远程分支的关联：git branch --set-upstream branch-name origin/branch-name

## 标签
- 标签是容易记住的有意义的名字，与某个commit绑在一起。
- 创建标签
  - 创建前应切换到该分支上
  - git tag tagname [COMMIT_ID]
  - 指定标签信息：git tag -a tagname -m "readme" [COMMIT_ID]
  - PGP签名标签：git tag -s tagname -m "readme" [COMMIT_ID]
- 查看所有标签：git tag
- 查看标签信息：git show tagname
- 删除本地标签：git tag -d tagname
- 删除远程标签：git push origin :refs/tags/tagname>，首先应删除本地标签
- 推送标签：git push origin tagname
- 推送所有标签：git push origin --tags
-

## github with atom #
- Github中创建仓库（项目）
- Github中拷贝Clone/Download的URL
- 命令行：git clone URL
  - git clone https://github.com/username/project.git
- Atom中添加本地项目路径，添加、更新文件
- git Bash命令行：
  - cd至创库路径
  - git status
  - git add file
  - git commit -m "message"
  - git push

## git 配置
- git config --list
- git config --global user.name "username"
- git config --global user.email "emailaddress"
- git config --global color.ui true
- 忽略特殊文件
  - 将.gitignore加入到仓库中
  - 检查：git check-ignore  -v file
- 配置别名
  - git config --global alias.st status
  - 别名生成在配置文件中：.git/config或.gitconfig（全局）

## git ssh配置
- 打开git Bash
- git 配置name和email
- cd ~/.ssh 如果.ssh目录下有三个文件，则密钥已经生成，否则需要生成密钥
- 可通过如下方式生成密钥
  - ssh-keygen -t rsa -C "emailaddress"
  - 生成过程默认方式。（默认路径，默认没有密码登录）
  - 生成成功后，一般在目录：C:/users/name/.ssh/id_rsa
- 使用记事本打开id_rsa.pub，得到ssh key公钥。
- 在github，点开settings，打开“SSH and PGP keys”，点击“New SSH Key”
- 修改remote方式（https或者ssh）
  - 查看当前的remote方式 git remote -v
  - 修改为https
  > git remote set-url origin https://github.com/useranme/test.git
  - 修改为ssh
  > git remote set-url origin git@github.com/username/test.git

## 参考
- [Git教程-廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
