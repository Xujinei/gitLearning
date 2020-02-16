### git 简介
#### 1. git 概述 
 **分布式** 版本控制系统
#### 2. 与svn 的区别
1. git 是**分布式**的版本控制系统
    1. 分布式： 没有中央服务器之说，每个人的电脑都是完整的版本库，每次只提交改动点。
    2. ![c2e35e40dfe34bd07ce39830dc8286f6.png](en-resource://database/413:0)

2. svn 是**集中式**的版本控制系统
    1. 集中式 ： 版本库存放在中央服务器，工作前需要先从中央服务器获取最新版本，在开始在自己的电脑上工作。
    2. ![bb42ef3d05ea529e7202c9ef4c88e354.png](en-resource://database/411:0)

#### 3. git 版本库
1. 版本库概念： 仓库，目录

2. 创建空的版本库： `git init`

3. 添加文件到版本库的暂存区(可添加多个文件，用空格分隔)： `git add file` 

4. 提交已添加到暂存区的文件快照到版本库的当前分支 ： `git commit -m 'xxx’`

   ![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

5. 查看版本提交（commit）记录 ： `git log`  输出修改概述，提交时的commit id,提交时间，作者

   1. 查看分支合并线路图 ; `git log --graph`

6. 查看近期历史命令 ： `git reflog`

7. 版本回退到指定版本 ： `git reset --hard commit_id`  commit_id 可通 `git log` 或者 `git reflog`命令进行查看

#### 4. git 远程仓库

1. 远程仓库 如 github , gitlab
2. 本地仓库关联远程仓库 :`git remote add origin git@github.com:userName/respName.git ` 
3. 将本地仓库分支推送并关联到远程仓库分支：`git push -u orgin master`
4. 克隆远程仓库到本地 ： `git clone git@github.com:userName/respName.git`
5. 创建本地分支和远程分支的连接: `git branch --set-upstream-to <branchName> origin/<branchName> `
6. 拉取远程分支到本地 : `git pull`

### 文件操作

1. 查看文件修改的内容 ： `git diff 文件名`
2. 检出工作区已删除，但是版本库中未删除的文件到工作区 / 如果文件在工作区都版本库中都存在，则用版本库中的文件内容覆盖更新工作区的文件内容： `git checkout -- 文件名`
3. 从当前分支中删除文件（工作区的文件也会被删除）： `git rm 文件名`
4. 从暂存区中强行删除文件（工作区的文件也会被删除）： `git rm -f 文件名`

### 分支管理
#### 1. 创建分支
1. 基于当前分支创建新分支
    1. 创建分支： `git branch 分支名`
    2. 创建并切换到新分支：  `git checkout -b 分支名`  不加 `-b` 为切换分支
    3. 创建并切换到新分支（**最新版本支持**）  : `git swtich -c 分支名` ， 不加`-c` 为切换分支

#### 2. 查看分支
1. 查看分支状态 `git status`

2. 检出所有分支 `git branch`


#### 3. 删除分支

1. 删除分支：`git branch -d 分支名 `
2. 强制删除分支： `git branch -D 分支名`
3. 匹配分支名中存在xxx 字符的分支 批量删除分支 ： `git branch |grep 'xxx'|xargs git branch -D`
   1. `git branch` : 输出当前分支列表
   2. `grep` :是对 git branch 的输出结果进行匹配，匹配值当然就是 xxx 
   3. `xargs` : 将参数列表转换成小块分段传递给其他命令

#### 3.合并分支
1. 将master 分支合并到当前分支 : `git merge master`

#### 4. 工作区分支内容暂存

1. 不想提交工作区分支内容到仓库，但是想切换新的分支时，可将当前工作区的内容暂存：`git stash`
2. 查看暂存内容 : `git stash list`
3. 将暂存内容恢复到工作区（**不删除暂存内容**）: `git stash apply`
4. 删除暂存内容 :`git stash drop`
5. 恢复并删除暂存内容: `git stash pop`

#### 5. 标签

1. 概述: 标签是对commit 的标记，相当于commit_id 方便记忆或查询的一个名字
2. 检出所有标签 : `git tag`
3. 在当前分支的当前待commit上创建标签 ：`git tag tagName`
4. 创建对于commitId 的标签 : `git tag tagName commitId`
5. 查看指定标签的说明 ： `git show tagName`
6. 删除本地标签 : `git tag -d tagName`
7. 推送本地标签到远程 ：`git push origin tagName`
8. 删除远程标签 : `git push origin ：refs/tags/tagName`