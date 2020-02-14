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
3. 添加文件到版本库(可添加多个文件，用空格分隔)： `git add file` 
4. 提交已添加的文件快照到仓库 ： `git commit -m 'xxx’`
5. 查看版本提交（commit）记录 ： `git log`  输出修改概述，提交时的commit id,提交时间，作者
6. 版本回退到指定版本 ： `git reset --hard commit_id`  commit_id 可通 `git log` 命令进行查看

### 分支管理
#### 1. 创建分支
1. 基于当前分支创建新分支
    > git branch 分支名
    > git checkout -b 分支名

#### 2. 查看分支
1. 查看分支状态

    > git status

2. 检出分支

   > git branch

3. 查看文件修改的内容 ： `git diff 文件名`

4. 

#### 3. 删除分支
   > git branch -d 分支名 
   > 1. 强制删除
   >  > git branch -D 分支名
   > 1. 匹配分支名中存在xxx 字符的分支 批量删除分支
   >  > git branch |grep 'xxx' |xargs git branch -D 
   >  > > git branch 输出当前分支列表
   >  > > grep 是对 git branch 的输出结果进行匹配，匹配值当然就是 xxx 
   >  > > xargs 的作用是将参数列表转换成小块分段传递给其他命令

#### 3.合并分支
1. 将master 分支合并到当前分支
    > git merge master
    > 2.