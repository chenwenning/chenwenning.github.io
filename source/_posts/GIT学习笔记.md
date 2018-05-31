### GIT项目分支开发流程
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




###GIT冲突实战

冲突场景：

####1.修改相同的项目
A先提交,B再提交，报以下错误：
![Alt text](/image/push-conflict.png)

解决方法：

先   `git pull origin hexo`

再   `git push origin hexo`

#### 2.修改相同的文件，不改向同行

A先提交，B再提交，报以下错误：


