打开配置文件：vi ~/.bash_profile
立即更新配置： source ~/.bash_profile

重要链接：

- http://www.vscoder.net/vscode-lesson/vscodezhongpeizhijavakaifahuanjingwanquanzhinan.html

- https://blog.csdn.net/gisboygogogo/article/details/85138656



# **JDK 版本安装相关**
一些命令：

```
zejianli@~ $ echo $JAVA_HOME
/Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home

zejianli@~ $ ls /Library/Java/JavaVirtualMachines/
adoptopenjdk-11.jdk jdk-11.0.7.jdk      jdk1.8.0_251.jdk

zejianli@~ $ /usr/libexec/java_home -V
Matching Java Virtual Machines (3):
    11.0.7, x86_64:	"Java SE 11.0.7"	/Library/Java/JavaVirtualMachines/jdk-11.0.7.jdk/Contents/Home
    11.0.7, x86_64:	"AdoptOpenJDK 11"	/Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home
    1.8.0_251, x86_64:	"Java SE 8"	/Library/Java/JavaVirtualMachines/jdk1.8.0_251.jdk/Contents/Home

/Library/Java/JavaVirtualMachines/jdk-11.0.7.jdk/Contents/Home

zejianli@~ $ mvn -version
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /usr/local/apache-maven-3.6.3
Java version: 11.0.7, vendor: AdoptOpenJDK, runtime: /Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home
Default locale: zh_CN_#Hans, platform encoding: UTF-8
OS name: "mac os x", version: "10.15", arch: "x86_64", family: "mac"

zejianli@~ $ java -version
openjdk version "11.0.7" 2020-04-14
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.7+10)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.7+10, mixed mode)

```

# **LeetCode for VS Code**
- 链接：
https://zhuanlan.zhihu.com/p/56226189
https://www.jianshu.com/p/3b30c4c846d1

- 安装node.js:
```
zejianli@~ $ brew install node

zejianli@~ $ npm install -g cnpm --registry=https://registry.npm.taobao.org
/usr/local/bin/cnpm -> /usr/local/lib/node_modules/cnpm/bin/cnpm
+ cnpm@6.1.1
added 685 packages from 953 contributors in 15.039s

zejianli@~ $ npm -v
6.13.6

zejianli@~ $ node -v
v13.7.0
```

- Mac node.js安装和环境配置: https://blog.csdn.net/u013400682/article/details/71191658
- 问题：以上步骤完成后 重启电脑 VScode 后尝试 按F1 尝试 sign in leetcode，仍然报错：“LeetCode extension needs Node.js installed in environment path” 
- 解决过程：
https://github.com/jdneo/vscode-leetcode/issues/201
https://juejin.im/post/5d0e0d13e51d4556f76e80bb
"mac 使用code命令打开VSCode
我们在mac的终端可以使用 open .打开文件夹 如果我们想用vs-code打开文件夹,用的命令是 code .,不过你得先按照code
安装code：打开VSCode –> command+shift+p –> 输入shell command –> 点击提示Shell Command: Install ‘code’ command in PATH运行 使用：打开终端，cd到要用VSCode打开的文件夹，然后输入命令code .即可打开"  不能在mac的程序坞里面鼠标点击打开lc插件，要在终端里面用以上方法打开，然后就可以正常登陆lc插件，终于好了，醉了。。
- 使用终端登陆VScode 的命令如下：
```
zejianli@~ $ cd /Users/zejianli/OneDrive\ -\ bupt.edu.cn/公司实习/【LC做题】/test/src/app 
zejianli@app $ ls
App.java  test.java
zejianli@app $ code .
```


- 使用cookie登陆LC插件，现在不支持直接登陆美国站了，只能直接登陆中国站，参考链接：https://github.com/jdneo/vscode-leetcode/issues/478#issuecomment-564757098

![image](https://user-images.githubusercontent.com/54604936/80351488-fe426680-88a4-11ea-9dc8-a42db2bfe3af.png)




# **.bash_profile文件配置语句的备份**
```python
 35 #JAVA JDK 环境配置
 36 #export JAVA_HOME=$(/usr/libexec/java_home)
 37 #export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.0.7.jdk/Contents/Home    
 38 export JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home  
 39 export PATH=$PATH:$JAVA_HOME/bin
 40 export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
 41 
 42 
 43 # Maven 环境配置
 44 export MAVEN_HOME=/usr/local/apache-maven-3.6.3
 45 export PATH=$PATH:$MAVEN_HOME/bin/
 46 export PATH=$M3_HOME/bin:$PATH
 47 export PATH=$PATH:$JAVA_HOME/bin:$M2_HOME/bin
 48 
 49 # Node.js 环境配置
 50 export PATH=$PATH:/usr/local/bin/
 51 

```


# **总结**
- 在VScode里面下载了一堆java插件发现还是Code Runner 最好用，可以直接运行各种语言的代码，方便快捷，可以直接对文件夹中的某一个java文件运行，不需要像eclipse一样创建项目导入包之类的。 链接：https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner