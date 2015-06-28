#<div align = center>浏览器内部工作原理</div>
=============================================

***

##浏览器介绍

&emsp;&emsp;目前有五种主流浏览器（IE、Firefox、Safari、Chrome及Opera）

###浏览器的主要功能

&emsp;&emsp;浏览器的主要功能是将用户选择的web资源呈现出来，它需要从服务器请求资源，并将其显示在浏览器窗口中，资源的格式通常是HTML，也包括PDF、image及其他格式。用户用URI（Uniform Resource Identifier统一资源标识符）来指定所请求资源的位置

&emsp;&emsp;HTML和CSS规范中规定了浏览器解释html文档的方式，由W3C组织对这些规范进行维护，W3C是负责制定web标准的组织。
　　
HTML规范的最新版本是HTML5，最新的css规范版本是css3

###浏览器的主要构成

浏览器的主要组件包括：

&emsp;&emsp;1. 用户界面 － 包括地址栏、后退/前进按钮、书签目录等，也就是你所看到的除了用来显示你所请求页面的主窗口之外的其他部分。

&emsp;&emsp;2. 浏览器引擎 － 用来查询及操作渲染引擎的接口。

&emsp;&emsp;3. 渲染引擎 － 用来显示请求的内容，例如，如果请求内容为html，它负责解析html及css，并将解析后的结果显示出来。

&emsp;&emsp;4. 网络 － 用来完成网络调用，例如http请求，它具有平台无关的接口，可以在不同平台上工作。

&emsp;&emsp;5. UI后端 － 用来绘制类似组合选择框及对话框等基本组件，具有不特定于某个平台的通用接口，底层使用操作系统的用户接口。

&emsp;&emsp;6. JS解释器 － 用来解释执行JS代码。

&emsp;&emsp;7. 数据存储 － 属于持久层，浏览器需要在硬盘中保存类似cookie的各种数据，HTML5定义了web database技术，这是一种轻量级完整的客户端存储技术

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![](../images/web-001.png)

##渲染引擎

&emsp;&emsp;渲染引擎的职责就是渲染，即在浏览器窗口中显示所请求的内容。

&emsp;&emsp;默认情况下，渲染引擎可以显示html、xml文档及图片，它也可以借助插件（一种浏览器扩展）显示其他类型数据，例如使用PDF阅读器插件，可以显示PDF格式，将由专门一章讲解插件及扩展，这里只讨论渲染引擎最主要的用途——显示应用了CSS之后的html及图片。

###渲染引擎简介

&emsp;&emsp;本文所讨论的浏览器——Firefox、Chrome和Safari是基于两种渲染引擎构建的，Firefox使用Geoko——Mozilla自主研发的渲染引擎，Safari和Chrome都使用webkit。

&emsp;&emsp;Webkit是一款开源渲染引擎，它本来是为Linux平台研发的，后来由Apple移植到Mac及Windows上，相关内容请参考http://webkit.org。

###渲染主流程

&emsp;&emsp;渲染引擎首先通过网络获得所请求文档的内容，通常以8K分块的方式完成。
　　
&emsp;&emsp;下面是渲染引擎在取得内容之后的基本流程：

解析html以构建dom树 -> 构建render树 -> 布局render树 -> 绘制render树

![](../images/web-002.png)

&emsp;&emsp;渲染引擎开始解析html，并将标签转化为内容树中的dom节点。接着，它解析外部CSS文件及style标签中的样式信息。这些样式信息以及html中的可见性指令将被用来构建另一棵树——render树。
　
&emsp;&emsp;Render树由一些包含有颜色和大小等属性的矩形组成，它们将被按照正确的顺序显示到屏幕上。
　　
&emsp;&emsp;Render树构建好了之后，将会执行布局过程，它将确定每个节点在屏幕上的确切坐标。再下一步就是绘制，即遍历render树，并使用UI后端层绘制每个节点。
　　
&emsp;&emsp;值得注意的是，这个过程是逐步完成的，为了更好的用户体验，渲染引擎将会尽可能早的将内容呈现到屏幕上，并不会等到所有的html都解析完成之后再去构建和布局render树。它是解析完一部分内容就显示一部分内容，同时，可能还在通过网络下载其余内容。

<div align = center>webkit主流程</div>

![](../images/web-003.png)

<div align = center>Mozilla的Geoko渲染引擎主流程</div>

![](../images/web-004.jpg)

&emsp;&emsp;尽管webkit和Gecko使用的术语稍有不同，他们的主要流程基本相同。Gecko称可见的格式化元素组成的树为frame树，每个元素都是一个frame，webkit则使用render树这个名词来命名由渲染对象组成的树。Webkit中元素的定位称为布局，而Gecko中称为回流。Webkit称利用dom节点及样式信息去构建render树的过程为attachment，Gecko在html和dom树之间附加了一层，这层称为内容接收器，相当制造dom元素的工厂。下面将讨论流程中的各个阶段。

***参考文档：http://kb.cnblogs.com/page/129756 ***



