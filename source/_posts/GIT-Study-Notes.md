---
title: GIT项目开发实践
date: 2018-05-38 18:30:16
tags: GIT
category: GIT
---
### 一.GIT项目分支开发流程
#### 1. 创建d-kaifa分支
* `git checkout master && git pull`
* `git checkout -b d-kaifa master`
* `git reset release **/pom.xml`
* `git checkout .`
* `git commit -m 创建开发分支并修改内网版本`

#### 2. 项目开发并合并到develop分支

* `git checkout develop && git pull`
* `git merge d-kaifa`

#### 3. 项目提测并合并到test分支

* `git checkout test && git pull`
* `git merge d-kaifa`

#### 4. 项目验收并合并到release分支

* `git checkout release && git pull`
* `git merge d-kaifa`


#### 5. 项目上线并合并到master分支

* `git checkout master && git pull`
* `git merge d-kaifa `
* `git commit -m xxx功能`
* `git tag vx.x.x-xxxxxxx`
* `git push origin master`
* `git push origin vx.x.x-xxxxxxx`
    * 代码有问题继续改bug
        * `git checkout d-kaifa`
        * `git merge master`
        * 开发。。。
        * 重复上线流程
    * 开发完成
        * `git branch -D d-kaifa`




###二.GIT冲突实战

冲突场景：

####1.修改相同的项目
A先提交,B再提交，报以下错误：
![Alt text](push-conflict.png)

解决方法：

先   `git pull origin hexo`

再   `git push origin hexo`

#### 2.修改相同的文件，不改向同行

A先提交，B再提交，报以下错误：

![Alt text](push-conflict2.png)

解决方法：

先   `git pull origin hexo`

再   `git push origin hexo`

####3.修改相同的文件，改相同行
A先提交，B再提交，报以下错误：

![Alt text](push-conflict3.png)

解决方法：

先    `git pull origin hexo`

![Alt text](push-conflict4.png)

再手动合并：

![Alt text](push-conflict5.png)

手动合并好后：

执行   `git add .`

执行   `git commit -m " 提交hexo"`

执行   `git push origin hexo`

问题解决

####4.修改相同的文件，改相同行；A:先提交；B:把文件add到暂存区，但不commit; 这时B 进行pull

解决方法：

B先执行   `git commit -m " 提交hexo"`

执行   `git pull origin hexo`

###三.GIT 文件状态示意图

![Alt text](git-status.png)

1.暂存区：执行 git add 文件 后 该文件就到了暂存区

2.修改区：就是之前有这个文件 但是现在修改文件内容

3.未追踪区：就是刚刚添加  还没有执行 git add 操作

![Alt text](git-status2.png)

###四.GIT 命令小图

![Alt text](git-quantu.png)

