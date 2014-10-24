---
layout: post
title: 「转」【十问十答】对话Go语言开发团队
---

Go是谷歌推出的一门编程语言。熟悉Go语言的开发者都知道其弥补了C语言的不足并且保持了C的极简主义。使用Go编译的程序可以媲美C或C++代码的速度，而且更加安全、支持并行进程（使用Go语言的12个理由）。一些主流的项目包括Docker、Heroku's Force.com以及Cloud Foundry's (Go)Router都是基于Go语言编写而来。有人说，Go为云而生，也正是由于其拥有并发性的操作系统以及完美的架构，使其备受开发者的青睐。 

本文摘译自dotGo，文中采访了Go语言的开发团队，一起来聆听大神们谈Go语言的依赖关系、语言设计及Android平台上的一些新特性。 


<!--more-->

译文如下： 

![GO](http://dl2.iteye.com/upload/attachment/0102/2321/b0345ab4-83a1-3f38-b899-51294adb84c5.jpg)
 

Go语言开发团队成员：Francesc Campoy Flores、Andrew Gerrand、Brad Fitzpatrick、Dave Cheney、Keith Rarick及Blake Mizerany

Q：反模式编程不断出现，特别是当人们在探究使用与复用问题时。你会使用哪种反模式？ 

Dave Cheney：我觉得是包，现在的包实在是太多了。 

Q：坊间有不少第三方的依赖管理工具，如：godep，gpm等。未来这些工具会作为go的核心工具来使用吗？ 

Brad Fitzpatrick：我们不想来定义游戏规则，话语权应交给社区。等每个人都觉得它成熟稳定后，我们才会再考虑。 

Q：Go语言对在Unix环境下的服务器端编程表现不俗。因而现在人们尝试使用Go来进行桌面和内嵌应用的编写？ 

Dave Cheney：我是希望Go能在小型ARM处理器上有所表现。我们需要让编译器能针对不同的ARM生成相应的代码。同时，我也想让它在垃圾回收上做得更好。 

Brad Fitzpatrick：是的。人们现在也尝试在Go里编写GUI库。 

Q：Go语言在对Android支持方面有什么新发展吗？ 

Andrew Gerrand：当然有！David Crawshaw正在跟进该项目。他有几个让Go在Android上运行的办法：1）使用NDK，获取画布，触摸事件，声音等方面的权限；2）使用Java与Go相结合的办法。 

Q：Go语言的垃圾回收器会着眼于长时间低延迟处理方面吗？ 

Brad Fitzpatrick：如果你对程序产生的垃圾在意，答案是肯定的。我们已尝试让dl.google.com产生更少的垃圾。 

Q：类似dlopen的动态载入有什么新动作吗？ 

Andrew Gerrand： Lance Taylor正在整理Go语言执行方式的文档。但是具体的话还没有时间表，文档可以说是要做的第一步吧。 

Brad Fitzpatrick：我想要在连接器重写之后。 

Q：堆压缩会在2.0版本中推出还是处于未来计划中？ 

Brad Fitzpatrick：处于未来计划中。 

Q：采用管理树来销毁goroutines线程似乎需要不少的人工操作。这会在未来的支持库中得到解决吗？ 

Dave Cheney：在今年的GopherCon 会议上，人们觉得打造一个健壮的应用是程序员的天职。所以首先我们得自己做得足够好。 

Q：Go语言在新特性开发上好像较保守，这是一种明智的选择吗？ 

Dave Cheney：是的，这是Go的基础。 

Andrew Gerrand：Go当初是三名成员达成共识后才做的。现在成员比当初更多了，所以也更复杂了。所谓众口难调，对程序的修改很难做到都满足各方的需要。一切都得按着计划进行。 

Q：大型企业对选择新语言显得更为慎重，对于说服他们来使用Go语言有什么建议吗？ 

Dave Cheney：Go语言经常作为具体问题的解决方案来使用。所以说最好的公关说法是：“它能帮助解决一个实际问题。” 

Andrew Gerrand：使用Go语言的大型企业包括苹果、Comcast、Facebook等等。