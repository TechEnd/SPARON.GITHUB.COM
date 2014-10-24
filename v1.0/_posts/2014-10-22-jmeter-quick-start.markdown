---
layout: post
title: JMeter 使用入门
---


最近基于[FusionPBX](http://www.fusionpbx.com/)做[FreeSWITCH](https://www.freeswitch.org/)配置管理系统时，需要做性能测试，于是在网上搜了一下关于性能测试相关的工具，发现JMeter时Apache的一个开源项目，并且是基于java开发，便对其感兴趣了，根据网上的描述了解到JMeter是目前性能测试工具中的佼佼者。

于是先到官方网站[下载最新版本](http://jmeter.apache.org/download_jmeter.cgi)，目前最新版是jakarta-jmeter-2.11。

<!--more-->

<br/>

运行bin/jmeter.bat后，先来了解几个术语：

1. 线程组：测试里每个任务都要线程去处理，所有我们后来的任务必须在线程组下面创建。可以在“测试计划->添加->线程组”来建立它，然后在线程组面板里有几个输入栏：线程数、Ramp-Up Period(in seconds)、循环次数，其中Ramp-Up Period(in seconds)表示在这时间内创建完所有的线程。如有8个线程，Ramp-Up = 200秒，那么线程的启动时间间隔为200/8=25秒，这样的好处是：一开始不会对服务器有太大的负载。

2. 取样器（Sampler）：可以认为所有的测试任务都由取样器承担，有很种，如：HTTP 请求。

3. 断言：对取样器返回的请求结果给出判断，是否正确。

4. monitor：它的功能是对取样器的请求结果显示、统计一些数据（吞吐量、KB/S……）等。

先这些概念。下面来试用一下：

添加线程组，右击测试计划->添加->线程组，线程数为2，Ramp-Up=0，循环次数=5；添加取样器：右击线程组->添加->Sample->HTTP 请求，Web服务器localhost，端口8080，协议http，路径/index.jsp；添加monitor，右击线程组->添加->monitor->图形结果（第二个），然后再添加一个Summary report monitor。

然后，运行->启动，在两个monitor中都可以看到一些内容，如：

![JMeter]({{ site.url }}/assets/rage-comic/jmeter_quick_star_01.jpg)   

JMeter 的主要测试组件总结如下：

1. 测试计划是使用 JMeter 进行测试的起点，它是其它 JMeter 测试元件的容器。

2. 线程组代表一定数量的并发用户，它可以用来模拟并发用户发送请求。实际的请求内容在Sampler中定义，它被线程组包含。

3. monitor负责收集测试结果，同时也被告知了结果显示的方式。

4. 逻辑控制器可以自定义JMeter发送请求的行为逻辑，它与Sampler结合使用可以模拟复杂的请求序列。

5. 断言可以用来判断请求响应的结果是否如用户所期望的。它可以用来隔离问题域，即在确保功能正确的前提下执行压力测试。这个限制对于有效的测试是非常有用的。

6. 配置元件维护Sampler需要的配置信息，并根据实际的需要会修改请求的内容。

7. 前置处理器和后置处理器负责在生成请求之前和之后完成工作。前置处理器常常用来修改请求的设置，后置处理器则常常用来处理响应的数据。

8. 定时器负责定义请求之间的延迟间隔。

<br/> 

可以参考资料：

[中文 Jmeter 手册](http://www.ibm.com/developerworks/cn/opensource/os-pressiontest)

[官方资料](http://jakarta.apache.org/jmeter/usermanual/index.html)

<br/> 

