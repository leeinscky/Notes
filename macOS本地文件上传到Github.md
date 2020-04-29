# **使用Git为什么方便有用？**
- [原文](https://juejin.im/post/5abef8356fb9a028df22bd78)
- 备注：
![](https://user-gold-cdn.xitu.io/2018/3/31/1627a3138484ada9?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

- 我们在看Github上的项目时候，点击 history 可以清楚的看到代码在不同时间做的不同修改是什么，这就是版本控制带来的好处。比较笨的版本控制方法：每次修改完代码复制一份上传到云盘或者本地某一个目录，非常占空间不方便，而且容易遗漏。然而，通过git 版本控制工具，我们修改完以后只需要 1.将工作区文件**git add**到储存区，2. 然后从储存区**git commit** 到 本地仓库，3.**git push** 到Github远程仓库完成一次版本上传。远程仓库的服务器就可以永久帮我们记录此次版本。

- #### 本地仓库(版本库)
版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

- #### 本地仓库(版本库)是什么
什么是版本库呢？版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

- #### 暂存区
暂存区：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。

- #### 工作区
工作区：就是你在电脑里能看到的目录。


作者：胜天半子bibi酱
链接：https://juejin.im/post/5abef8356fb9a028df22bd78
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

# **【成功部署代码到github】把本地项目上传到GitHub（过程详细准确）**

- [原文链接](https://blog.csdn.net/weixin_39220472/article/details/82956651)
- 流程：
  1. 本地Git仓库和Github仓库之间的传输通过SSH加密，所以连接时需要先git配置SSH Key
   <br /> 2. 在本地创建一个版本库（即文件夹），通过**git init**把它变成Git仓库；
   <br />3. 把项目复制到这个文件夹里面，再通过git add .把项目添加到仓库；（注意：add . 代表将所在文件夹里所有文件都提交，将点号替换为指定文件名就可以只上传某个文件。add 之后我们可以通过 **git status** 查看文件状态）
   <br />4. 再通过 **git commit -m "注释内容"** 把项目提交到仓库；（注意：引号内的注释内容在github上会显示，第一次提交时推荐写 **"first commit"**，文件有修改后提交时可以些 **"update xxx"** or **"add xxx"**，主要是为了方便我们知道更新的版本做了什么方面的修改。）
   <br />5. 在Github上设置好SSH密钥后，新建一个远程仓库，通过 **git remote add origin https://github.com/GreyWolfCxh/appointment.git** 将本地仓库和远程仓库进行关联；
    <br />6. 最后通过 **git push -u origin master** 把本地仓库的项目推送到远程仓库（也就是Github）上。 
    <br /> 注意：若新建远程仓库的时候在网页上点击了那个自动创建README文件的按钮以后，我们在本地push的时候会报错。就是在上面创建远程仓库的时候，如果你勾选了Initialize this repository with a README（就是创建仓库的时候自动给你创建一个README文件），那么到了你将本地仓库内容推送到远程仓库的时候就会报一个failed to push some refs to https://github.com/GreyWolfCxh/appointment.git的错。这是由于你新创建的那个仓库里面的README文件不在本地仓库目录中。
    <br /> 解决办法：这时我们可以通过以下命令先将内容合并以下：**git pull --rebase origin master** 之后再执行push就好了：**git push -u origin master**  （origin 是用于区分的别名，改成leeincky_leetcode 也可以。如果多个项目都用origin会导致重复报错，我们可以先将原来的origin别名删除：**git remote rm origin**，然后：**git remote add leeinscky_leetcode git@github.com:leeinscky/Leetcode.git**，意思是将这个远程仓库的别名设为：leeinscky_leetcode）
    <br />理解：网页上有一个readme，但是我们本地没有，那么如何同步呢？我们先将网页上的那个文件 拉回/pull 到本地，这样我们本地就有了这个readme文件，然后再 上传/push 到网页上/远程端的版本仓库
    <br />版权声明：本文为CSDN博主「灰太狼_cxh」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。

# **命令行**
```
zejianli@vs $ git add .

zejianli@vs $ git status
On branch master
Your branch is up to date with 'leeinscky_leetcode/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   MainFunction.java

zejianli@vs $ git commit -m "first commit"
[master 27514e8] first commit
 1 file changed, 9 insertions(+)
 create mode 100644 MainFunction.java

zejianli@vs $ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 442 bytes | 442.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:leeinscky/Leetcode.git
   ca06df4..27514e8  master -> master

查看别名是什么，网上一般都写origin，但是如果仓库很多，建议用不同的：
zejianli@vs $ git remote -v
origin	git@github.com/leeinscky/Leetcode.git (fetch)
origin	git@github.com/leeinscky/Leetcode.git (push)

```

# **如果git push 不成功***

[原文链接](https://learnku.com/laravel/t/9642/cant-push-to-the-warehouse)

不成功时会出现以下错误：
```
zejianli@vs $ git push leeinscky_leetcode master
To github.com:leeinscky/Leetcode.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:leeinscky/Leetcode.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```

- 方法1（推荐2）:先将内容合并以下：**git pull --rebase origin master** 之后再执行，push就好了：**git push -u origin master**
- 方法2（强制push 因为没有pull可能会导致远程仓库的某些文件丢失）: **git push -u leeinscky_leetcode master -f**