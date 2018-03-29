# Ubuntu16.04（默认64位）安装jdk9（64位）

## 第一步：去Oracle下载JDK，根据自己的需要选择不同的版本，这里选择的JDK9.0.1

## 第二步：将下载好的压缩包解压

## 解压命令 tar -zxvf jdk-9.0.1_linux-x64_bin.tar.gz  

## 第三步：新建JDK目录，并且将解压好的文件夹移动到新建的JDK目录

如果创建目录的权限不够，可以进入到root用户进行创建：mkdir /usr/lib/jdk  

将解压后的文件移动到/usr/lib/jdk目录下，并查看：mv jdk-9.0.1 /usr/lib/jdk  

## 第四步：配置环境变量

使用下面的命令在/etc/profile文件末尾添加如下几行：gedit /etc/profile  

1. \#----------JDK begin   
2. export JAVA_HOME=/usr/lib/jdk/jdk-9.0.1  
3. export JRE_HOME=$JAVA_HOME/jre  
4. export CLASSPATH=.:\$CLASSPATH:$JAVA_HOME\/lib:$JRE_HOME/lib  
5. export PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin  
6. \#-------------JDK end  

使用下面的命令使配置生效：source /etc/profile  

## 第五步：使用java -version命令对配置的环境变量进行测试

# 可能出现的问题

**配置好环境参数之后。验证是否正常。提示 程序 'java' 已包含在下列软件包中。**

**root@lxm-Inspiron-N4050:/# java程序 'java' 已包含在下列软件包中： \* default-jre * gcj-4.9-jre-headless * gcj-5-jre-headless * openjdk-8-jre-headless * gcj-4.8-jre-headless * openjdk-9-jre-headless请尝试：apt install <选定的软件包>**

**解决办法：**

设置系统默认jdk 版本

**sudo update-alternatives --install /usr/bin/java java /usr/local/jdk1.8.0_121/bin/java 300**

**sudo update-alternatives --install /usr/bin/javac javac /usr/local/jdk1.8.0_121/bin/javac 300**

**sudoupdate-alternatives --config java**

# 已有jdk卸载

1.whereis java

2.which java

3.sudo rm -rf /usr/local/jdk1.8.0_131

4.sudo gedit /etc/profile

删除代码:  

\#set java environment  

export JAVA_HOME=/opt/jdk1.6.0_20

export JRE_HOME=$JAVA_HOME/jre

export CLASSPATH=$CLASSPATH:$JAVA_HOME/lib:$JRE_HOME/lib

export PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin

保存退出。

