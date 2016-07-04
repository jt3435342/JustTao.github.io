---
title: Android Studio Gradle build 卡住的解决方法
date: 2016-06-28 20:33:46
tags:
 -Android
categories: Android
---
Google推出的Android Studio跟Eclipse相比好用多了，但唯一的缺点就是由于GFW的原因导致下载某些组件的时候特别的慢，就算用了VPN Android Studio下载Gradle也非常的慢。所以经常在Build项目的时候老是卡在Gradle相关的地方，这里分享下我遇到问题和解决方法。
当Android Studio卡住的时候，关闭Android Studio，然后到项目目录下运行cmd命令行工具（Git Bash命令行也可以）。执行以下命令：
`gradlew assembleDebug`
这时会显示（我的gradle版本是2.10）
`Downloading gradle-2.10-all.zip`
这时候按Ctrl+C停止命令执行，这个过程会在`C:\Users\你的用户名\.gradle\wrapper\dists\gradle-2.10-all\a4w5fzrkeut1ox71xslb49gst`生成gradle-2.10-all.zip.lck与gradle-2.10-all.zip.part文件。这时候请到Gradle官网下载相应version的gradle，访问官网可能需要挂VPN，没有VPN请去百度找相应的资源。（注意如果挂VPN访问官网在点击下载链接的时候请断开VPN，否则无法访问）
下载完成后，请将下载的gradle-2.10-all.zip拷贝到`C:\Users\你的用户名\.gradle\wrapper\dists\gradle-2.10-all\a4w5fzrkeut1ox71xslb49gst`目录，并删除gradle-2.10-all.zip.part，同时复制gradle-2.10-all.zip.lck并且改名为gradle-2.10-all.zip.ok。
再次在命令行工具里执行：
`gradlew assembleDebug`
这时候你会发现没有Downloading的提示了，说明已经识别到了我们下载的gradle版本，现在只需等待gradle下载编译所需要的库并build生成debug app了。我建议大家以后第一次build的时候都以命令行方式进行而不要用Android Studio进行编译，因为命令行进行gradle build可以显示build过程的详细信息，比如下载哪些库，编译出现哪些错误，这样就不会出现在Android Studio中build不知道在哪里卡住的情况了。第一次build成功之后以后就可以在Android Studio中进行build了，不用再担心卡住的问题了