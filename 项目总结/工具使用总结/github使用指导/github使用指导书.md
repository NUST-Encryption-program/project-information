#<div align = center>github使用指导书</div>
===========================================

***

##github介绍

##github服务端

##github客户端

###windows下使用介绍

####准备工作

**windows下git工具**

1.tortoisegit

tortoisegit是类似于tortoisesvn的工具

下载地址：http://download.tortoisegit.org/tgit/1.8.14.0/

执行默认安装操作即可，右击后会发现多出几个快捷键（无法截图）

2.msysgit

github是服务端，要想在自己电脑上使用git我们还需要一个git客户端，我这里选用msysgit，这个只是提供了git的核心功能，而且是基于命令行的。

下载地址：http://msysgit.github.io/

执行默认安装操作即可，dos下执行git测试是否安装成功，如果执行不成功，需要设置一下环境变量path=C:\Program Files (x86)\Git\bin

然后执行git命令，如下图表示安装成功

![](../images/git-001.PNG)

3.git for windows

下载地址：https://windows.github.com/

默认操作安装即可，安装完后双击打开成功，表示安装成功


####方法一

使用tortoisegit和msysgit工具

####方法二

只使用msysgit工具

####方法三

使用git for windows工具

**1.下载github服务端工程**

双击打开github工具，需要登录github账号，登录后页面如下

![](../images/git-002.PNG)

然后要下载github上的工程，操作如下图

![](../images/git-003.png)

然后点击clone，然后选择clone路径

![](../images/git-004.png)

下载过程如下

![](../images/git-005.png)

下载完成后

![](../images/git-006.png)

**上传修改内容**

如果有修改的会类似下图显示

![](../images/git-007.png)

commit之后如下图显示

![](../images/git-008.png)

然后点击sync同步键，显示如下图，表示上传ok

![](../images/git-009.png)

####注意

github服务端工程管理，存在父子工程关系，

譬如我们的主工程是：https://github.com/NUST-Encryption-program/project-information

在使用此工程时，需要fork工程，防止工程修改的冲突

譬如fork的工程是：https://github.com/gaoyanshou/project-information

后续所有的操作需要在fork的工程中进行：包括下载，上传

######需要补充













