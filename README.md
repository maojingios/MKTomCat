# MKTomCat
MAC TomCat配置那点事儿

# MAC TomCat配置流程

## 拓展
### 关于shell

Shell 是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。
Shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。

### 常用
/etc/profile:此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行.并从/etc/profile.d目录的配置文件中搜集shell的设置.
	
/etc/bashrc:为每一个运行bash shell的用户执行此文件.当bash shell被打开时,该文件被读取.
	
~/.bash_profile:每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该
	文件仅仅执行一次!默认情况下,他设置一些环境变量,执行用户的.bashrc文件.
	
~/.bashrc:该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该
	该文件被读取.
	
~/.bash_logout:当每次退出系统(退出bash shell)时,执行该文件.
	
/home/oracle/.bash_profile  oracle用户的配置
	
/etc/skel/.bash_profile 默认配置
	
/root/.bash_profile root用户的配置


## 一、JDK

1、按照jdk`jdk1.7.0_79.jdk`安装指引进行安装（即一系列“next...”操作）。
	
2、打开终端，输入：`/usr/libexec/java_home`密令，将输出java home 路径，如：`/Library/Java/JavaVirtualMachines/jdk1.7.0_79.jdk/Contents/Home`。记住这个路径，下面配置环境变量有用。
	
3、在终端输入：`vim ~/.bash_profile`密令，回车。点击`i`，进入编辑状态。设置路径，如下：
	
	#JDK
	JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.7.0_79.jdk/Contents/Home
	CLASSPAHT=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
	PATH=$JAVA_HOME/bin:$PATH:
	export JAVA_HOME
	export CLASSPATH
	export PATH
	
确保配置信息无误，按`Esc`退出编辑,再按`:`键，输入`wq`,回车。
最后在终端输入：`source ~/.bash_profile` 让上面配置生效。
	
4、在终端输入`java`,随后会显示一系列提示信息(也可输入`java -version` 出现与jdk版本一致的信息)，即表示配置成功。

## 二、Tomcat

关于Tomcat下载，就不赘述。我这里的版本是`apache-tomcat-7.0.78`。

1、打开终端，`cd`到`bin`文件路径;

2、终端输入`./startup.sh`。如果上面配置正常，终端会显示`、、、Tomcat started.`的信息；

3、打开浏览器，输入`http://localhost:8080`，能显示网页，不报错，即表示Tomcat启动成功。

注意：

* 关于运行`./startup.sh`后出现`-bash: ./startup.sh: Permission denied`这种错误，这是权限问题，在终端输入`chmod u+x *.sh`密令，运行，让后按要求输入电脑开机密码，再次输入`./startup.sh`密令启动即可。

* 本人配置完成后，在浏览器输入`http://localhost:8080`报错-无法连接，网上查找解决办法基本上是修改`bin`文件夹下面的`setclasspath.sh`文件，但无法解决问题。

* 出现这种问题，建议首先请检查一二步骤，确保无误；其次，修改在`conf`下`server.xml`里面的端口，避免端口已被占用，切记保存后，关闭tomcat，然后重启，再尝试使用浏览器打开`http://localhost:8080`。



## ApacheTomcat目录结构

bin:存放tomcat命令

conf:存放tomcat配置信息,里面的server.xml文件是核心的配置文件

lib:支持tomcat软件运行的jar包和技术支持包(如servlet和jsp)

logs:运行时的日志信息

temp:临时目录

webapps:共享资源文件和web应用目录

work:tomcat的运行目录.jsp运行时产生的临时文件就存放在这里














   
