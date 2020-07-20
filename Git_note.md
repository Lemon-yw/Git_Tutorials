# Git概述



## 什么是Git
Git是一个免费、开源的版本控制软件



## 什么是版本控制系统
版本控制是一种记录一个或若干个文件内容变化，以便将来查阅特定版本修订情况的系统。（记录文件的所有历史变化、随时可恢复到任何一个历史状态、多人协作开发或修改错误恢复）



## 什么是Github
Github是全球最大的社交编程及代码托管网站（https://github.com/）。
Github可以托管各种git库，并提供一个web界面（用户名.github.io/仓库名）



## Github和Git是什么关系
Git是版本控制软件
Github是项目代码托管的平台，借助git来管理项目代码



## 为什么学习Github
学习优秀的开源项目
关注行业前辈了解最新的行业动态
借助github托管项目代码

# Git基本工作流程



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200330103343312.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTQxMzUxMQ==,size_16,color_FFFFFF,t_70)



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200330103353851.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTQxMzUxMQ==,size_16,color_FFFFFF,t_70)



# Git初始化及本地仓库创建和操作



## 基础设置

1. 设置用户名

```
git config --global user.name 'Lemon-yw'
```

2. 设置用户名邮箱

```
git config --global user.email '474768654@qq.com'
```

3. 查看设置

```
git config --list
```



## 初始化一个新的Git仓库

1. 创建文件夹

   ```
   mkdir demo
   ```

2. 在文件夹内初始化Git（创建Git仓库）

   ```
   cd demo
   git init
   ```

   

## 向仓库添加文件

1. 在工作区创建文件
	
	```
	touch test.py
	```
	
2. 把文件从工作区添加到暂存区
  
    ```
    git add test.py
    ```
    
3. 将文件从暂存区提交到仓库
  
    ```
    git commit -m '添加描述'
    ```
    
    

## 修改文件

1. 修改文件

   ```
   vim test.py
   ```

2. 把文件从工作区添加到暂存区

   ```
   git add test.py
   ```

3. 将文件从暂存区提交到仓库

   ```
   git commit -m '添加描述'
   ```



## 删除文件

1. 删除本地文件

   ```
   rm test.py
   ```

2. 从Git中删除文件

   ```
   git rm test.py
   ```

3. 提交操作

   ```
   git commit -m '添加描述'
   ```

注意：删除远程仓库文件时需要先把远程仓库里面的项目拉下来再删除

```
# 连接远程仓库后
git pull origin master
# 或者
git pull --rebase origin master
```



## 删除本地仓库

**删除仓库，就是需要删除仓库文件夹下隐藏的 .git 文件夹。**

进入项目所在目录，打开git bash，开始删除本地仓库：

1. 显示所有本地分支（初始化时只有一个master分支）

```
git branch
```

2. 初始化本地版本库（重新初始化一次，可以忽略）

```
git init
```

3. 找到目录下隐藏的 .git

```
ls -a
```

4. 删除 .git

```
rm -rf .git
```

> 关于rm的常用命令：
>
> * 删除当前目录下的所有文件及目录，并且是直接删除，无需逐一确认命令行为：
>
> ```
> rm -rf  要删除的文件名或目录
> ```
>
> * 删除文件名 test.txt:
>
> ```
> rm -rf test.txt
> ```
>
> * 删除目录 test，不管该目录下是否有子目录或文件，都直接删除:
>
> ```
> rm -rf test/
> ```

## Git克隆操作

```
git clone 仓库的url
```



## 将本地仓库同步到Git远程仓库中

连接远程仓库

```
git remote add origin [url]
```

推送内容到仓库

```
# 第一次提交
git push -u origin master

# 之后提交
git push
```

### 解除GitHub上传文件大小限制

1. 首先，打开终端，进入项目所在的文件夹；

2. 输入命令：

   ```
   git config http.postBuffer 524288000
   ```

之前git中的配置是没有这一项的，执行完以上语句后输入`git config -l`可以看到配置项的最下面多出了一行我们刚刚配置的内容。 (52428000=500×1024×1024,即500M)



### 解决git push错误

错误提示：

1. The requested URL returned error：403 Forbidden while accessing

2. 没有权限

原因：私有项目，没有权限，输入用户名和密码，或者远程地址采用这种类型。

解决方法：

> vim .git/config
>
> 将：
> [remote "origin"]
> 	url = https://github.com/用户名/仓库名.git
>
> 修改为：
> [remote "origin"]
> 	url = https://用户名:密码@github.com/用户名/仓库名.git

或者强制推送：

```
git push -u origin master -f
```



# Github Pages 搭建网站



## 个人站点

访问：https://用户名.github.io

搭建步骤：

1. 创建个人站点 ->  新建仓库（注：仓库名必须是 **用户名.github.io**）
2. 在仓库下新建index.html的文件即可

注意：

* github pages 仅支持静态网页
* **仓库里只能有.html文件**



## 项目站点

访问：https://用户名.github.io/仓库名

搭建步骤：

1. 进入项目主页，点击 settings
2. 在settings页面，点击 Launch automatic page generator 来自动生成主题页面
3. 新建站点基础信息设置
4. 选择主题
5. 最后点击 publish page 生成网页



# 团队协作分支开发模式



## 分支开发

1. 创建分支

	```
	git branch [branch id]
	```

2. 切换分支

    ```
    git checkout [branch id]
    ```

> 合并前两个步骤：创建并切换分支
>
> ```
> git checkout -b [branch id]
> ```

3. 提交分支到远端仓库

    ```
git push --set-upstream origin branch [branch id]
    ```



## 分支合并

1. 切换到主干支

   ```
   git checkout master
   ```

2. 更新远程仓库当前情况

   ```
   git pull
   ```

3. 合并分支

   ```
   git merge [branch id]
   ```

4. 提交到仓库

   ```
   git push
   ```

注意：合并不同分支的相同文件可能发生冲突

> 其实git pull包含有两个操作，即：`git pull = git fetch + git merge`。
> 	`git fetch`是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中。
> 	`git pull` 则是将远程主机的最新内容拉下来后直接合并，这样可能会产生冲突，需要手动解决。
>
> 其实git pull还有一个参数可以加，即git pull -rebase，其最终效果和git pull一样，也会fetch到远程代码。
>
> 即git pull默认使用的是merge模式，那么git pull -rebase指定使用rebase模式。

### git merge 和 git rebase 的区别

1. 结果上没有区别

   简单来说，git merge和git rebase从最终效果来看没有任何区别，都是将不同分支的代码融合在一起。

2. 生成的代码树不同

   虽然从最终效果上来说相同，但是git merge和git rebase生成的代码树稍微有些不同。

![image-20200517124822487](C:\Users\Lemon\AppData\Roaming\Typora\typora-user-images\image-20200517124822487.png)

​							git merge（合并）代码树          git rebase（复位基底）代码树

3. git merge会生成一个新的合并点，而git rebase不会。

   比如：当前存在两个分支，master和test分支

    ```
          D---E test
         /
    A---B---C---F master
    ```
   
   如果使用merge合并，将为分支合并自动识别出最佳的同源合并点：并新增合并点G
   
   ```
   	  D--------E
        /          \
   A---B---C---F----G test, master
   ```
   
   如果使用rebase合并，则合并结果为：
   
   ```
   A---B---D---E---C``'---F'`  `test, master 
   ```
   
   **即git rebase可以线性的看到每次提交，而git merge可以更加精确的看到每次提交。**
   
   所以**想要更好的提交树，使用rebase操作会更好一点**。这样可以线性的看到每一次提交，并且没有增加提交节点。
   
   > 这里补充一点： `rebase` 做了什么操作呢？
   >
   > ​	首先， `git`会把`test `分支里面的每个 `commit` 取消掉；
   >
   > ​	其次，把上面的操作临时保存成`patch` 文件，存在 `.git/rebase` 目录下；
   >
   > ​	然后，把`test`分支更新到最新的 `master` 分支；
   >
   > ​	最后，把上面保存的 `patch` 文件应用到 `test` 分支上。
   
   
   
4. 遇到冲突时的处理

   * merge 操作遇到冲突的时候，当前merge不能继续进行下去。手动修改冲突内容后，add 修改，commit 就可以继续往下操作；
   * 而rebase 操作的话，会中断rebase，同时会提示去解决冲突。解决冲突后，将修改add后执行git rebase —continue继续操作，或者git rebase —skip忽略冲突。
   
   > 在任何时候，我们都可以用 `--abort` 参数来终止 `rebase` 的行动，并且分支会回到 `rebase` 开始前的状态。
   >
   > ```
   > git rebase —abort
   > ```

`git rebase`具体使用场景举例：https://www.jianshu.com/p/f7ed3dd0d2d8

* 本地与远端同一分支提交历史不一致
* 不同分支之间的合并

---

# Git详细工作流程



![img](http://kmknkk.oss-cn-beijing.aliyuncs.com/image/git.jpg)

![img](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

图中左侧为工作区，右侧为版本库。在版本库中标记为 "index" 的区域是暂存区（stage, index），标记为 "master" 的是 master 分支所代表的目录树。

图中我们可以看出此时 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。

图中的 objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。

当对工作区修改（或新增）的文件执行 `git add` 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。

当执行提交操作`git commit`时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。

当执行 `git reset HEAD`命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。

当执行 `git rm --cached <file>`命令时，会直接从暂存区删除文件，工作区则不做出改变。

当执行 `git checkout .` 或者 `git checkout -- <file>` 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。

当执行`git checkout HEAD .` 或者 `git checkout HEAD <file>` 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。



## Git中的HEAD和head

1. HEAD指向的是当前的分支，即当前的工作目录所处的位置。

2. HEAD不一定指向一个分支，也可以指向一个commit。

3. 可以使用`git checkout`命令改变HEAD所处的位置。

4. 更具体来说：

   你可以认为 **HEAD(大写)是"current branch"(当下的分支)**。当你用git checkout切换分支的时候，HEAD修订版本重新指向新的分支。有的时候HEAD会指向一个没有分支名字的修订版本，这种情况叫“detached HEAD”

   而**head(小写)是commit对象的引用**，每个head都有一个名字（分支名字或者标签名字等等），但是默认情况下，每个叫master的repository都会有一个head, 一个repository可以包含任意数量的head。在任何时候，**只要这个head被选择成为“current head”，那么这个head就成了HEAD**,总是大写。



# Git 撤销操作

## 撤销已经push上去的操作

通过 `git log` 可以查看近期 commit 的信息：

```

commit bcdfd65ba3f16a0647e7687f92cca25d51738d2e
Author: Barret Lee <barret.china@gmail.com>
Date:   Mon Apr 28 01:22:27 2014 +0800
 
    now post
...
```

commit 后面的一串字符就是 SHA 字符。

```
git reset --hard SHA  
```

这句命令可以回退到指定版本。不过上传的时候要注意了，如果你是：

```
git push -u origin master
```

肯定会出现这样的错误提示：

```
error: failed to push some refs to 'https://github.com/barretlee/barretlee.github.io.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

原因是你本地版本要落后于服务器上的版本（git reset 回退了嘛），如果想覆盖服务器上版本，应该加 `-f` ，强制提交：

```
git push -u origin master -f
```

不过这样的操作要谨慎了，先把修改的位置备份（拿出来，复制到文件夹外），完成上述操作之后再复制回来处理。

更多撤销操作参考：http://www.ruanyifeng.com/blog/2019/12/git-undo.html

# Git常用命令

1. 查看状态

   ```
   git status
   ```

2. 查看历史修改日志

   ```
   git log
   ```

3. 查看某commit的修改

   ```
   git show [commit id]
   ```

4. 状态回滚（从仓库回到暂存空间）

   ```
   git reset [commit id]	
   # 当前空间只留下指定的commit id, 其余commit id将reset到暂存空间
   ```

5. 修改文件的commit message

   ```
   git commit --amend
   ```

6. 查看暂存区有哪些文件

   ```
   git ls-files
   ```

更多参考：http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html



# 解决冲突



## 传统方法

1. 输入 git pull，会提示哪个冲突文件已经合并；
   ![img](https://app.yinxiang.com/FileSharing.action?hash=1/60ad616c74a135e518e5a3670e7ebed4-303478)
2. git status会提示你可以做两个操作，一个是解决冲突conflicts后commit提交，一个是合并git merge；
   ![img](https://app.yinxiang.com/FileSharing.action?hash=1/75baefef360463d84319022fd5618b71-48662)
3. 打开冲突文件，可以看到多了冲突内容，只要删除红框内容保存文件即为解决冲突，按正常流程add →commit→ push即可。
   ![img](https://app.yinxiang.com/FileSharing.action?hash=1/04c3ebd87b3f7d212730d5f2d1157326-58836)



## 使用IDE快速解决

![img](https://app.yinxiang.com/FileSharing.action?hash=1/066bc341a4468e7edbf7daeb7242711f-1244210)



# GitHub Actions

持续集成由很多操作组成，比如抓取代码、运行测试、登录远程服务器，发布到第三方服务等等。GitHub 把这些操作就称为 actions。

很多操作在不同项目里面是类似的，完全可以共享。基于此，GitHub允许开发者把每个操作写成独立的脚本文件，存放到代码仓库，使得其他开发者可以引用。

如果你需要某个 action，不必自己写复杂的脚本，直接引用他人写好的 action 即可，整个持续集成过程，就变成了一个 actions 的组合。这就是 GitHub Actions 最特别的地方。

具体参考：http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html

---

# 遇到的问题记录



## 误删 git stash 文件恢复操作

参考：https://blog.csdn.net/JodenHe/article/details/80962306



## git rm 和 git rm --cached

* 删除本地及仓库中的文件

  ```
  git rm file
  git commit -m "xxx"
  git push origin master
  ```

* 删除仓库中的文件，保留本地的文件

  ```
  git rm --cached file
  git commit -m "xxx"
  git push origin master
  ```



## 如何恢复git rm后的文件

```
git reset
git checkout filename
```

注：此方法适用于未commit的情况。



## git修改历史提交(commit)信息

参考：https://blog.csdn.net/qq_17011423/article/details/104648075



## 避免 git pull 后覆盖本地提交方法

主要是使用git stash命令进行处理，分成以下几个步骤进行处理：

1. 先将本地修改存储起来

   ```
   git stash
   ```

   这样本地的所有修改就都被暂时存储起来 。
   使用`git stash list`可以看到保存的信息：

   `git stash`的作用是暂存修改

   其中stash@{0}就是刚才保存的标记。

2. pull内容

   暂存了本地修改之后，就可以pull了。

   ```
   git pull
   ```

3. 还原暂存的内容

   ```
   git stash pop stash@{0}
   ```

   系统提示如下类似的信息：

   ```
   Auto-merging c/environ.c
   
   CONFLICT (content): Merge conflict in c/environ.c
   ```

   意思就是系统自动合并修改的内容，但是其中有冲突，需要解决其中的冲突。

4. 解决文件中冲突的的部分

   打开冲突的文件，会看到类似如下的内容：

   [git冲突内容]

   其中Updated upstream 和=====之间的内容就是pull下来的内容，====和stashed changes之间的内容就是本地修改的内容。碰到这种情况，git也不知道哪行内容是需要的，所以要自行确定需要的内容。

   解决完成之后，就可以正常的提交了。



## 解决 git pull 之后本地代码被覆盖

1. 查看过去详细提交

   ```
   git reflog
   ```

2. 状态回滚

   ```
   git reset --hard 93c7150	# commit的版本号
   ```

3. 本地代码还原

   ```
   git cherry-pick  93c7150	# 指定 commit的版本号
   ```



## git 只提交部分文件到远程仓库（未实践）

修改或添加了多个文件，但只想提交部分代码的正确方式：

```
git add demo.html			# 提交到暂存区
git stash -u -k  			# 忽略其他修改，关键一步
git commit -m '修改演示文件' 	# 提交暂存区
git pull 				    # 拉取合并
git push origin master 		 # 推到远程仓库
git stash pop 				# 恢复之前忽略的文件（非常重要的一步）
```

另一篇参考：https://blog.csdn.net/u010730126/article/details/100743019



## git如何删除已经提交的文件

```
$ git pull origin master      # 将远程仓库里面的项目拉下来
$ git rm -r --cached .idea    # 删除.idea文件
$ git commit -m '删除.idea'    # 提交,添加操作说明
$ git push -u origin master    # 将本次更改更新到github项目上去
```



## GIT合并错误“由于您有未合并的文件，因此无法提交”

```
git add .
git stash
git checkout <branch id>
```