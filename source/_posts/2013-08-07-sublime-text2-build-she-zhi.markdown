---
layout: post
title: "sublime text2 build 设置"
date: 2013-08-07 18:11
comments: true
categories: 中文  mac sublime 
---
sublime text2 是一款优秀的编辑器，在mac，linux，window平台上都能用。sublime平台拥有很多优秀的插件，而且安装非常方便。
	command + shift+ p
能够召唤出强大无比的命令行，让你摆脱鼠标，摆脱一大波需要记的快捷键。官方网站上有[视频教程](https://tutsplus.com/course/improve-workflow-in-sublime-text-2/)，教程看起来非常赏心悦目，是的，赏心悦目。

Mac平台下sublime没有预设C的build配置，虽然直接用C++（据说国内某大型清新约炮网站有一程序萌妹子，人称C++）编译也行，但总归不舒服。stackoverflow等社区也没现成的方法，遂查了下sublime的[build配置方法](http://docs.sublimetext.info/en/latest/reference/build_systems.html),是熟悉的JSON结构。

下面是mac下面编译与运行一起执行的配置方法，并且能使编译时的错误一起到sublime里。
<pre>
{
    "cmd" : ["gcc",  "-o", "$file_base_name", "$file_name"],
    "selector" : "source.c",
    "shell" : false,
    "working_dir" : "$file_path"
}
</pre>

cmd就是执行的命令。尝试用 
	gcc -o test test.c && ./test
来编译和运行，发现sublime无法对&&进行解析。之后尝试使用两个cmd指令，发现只有第二个cmd是有效的。所以光配置sublime是无法达到一个build同时完成编译和运行的任务。要达成这个目的得翻阅zsh的文档自己写个能传参的命令，并且能输出gcc编译的结果和代码运行结果。
selector属性是选择自动build时候，当文件后缀是.c的时候自动选择这个build文件。

顺便记下windows平台下配置方法,还没测试过。
<pre>
{
  "cmd" : ["gcc", "$file_name", "-o", "${file_base_name}.exe", "&&", "${file_base_name}.exe"],
  "selector" : "source.c",
  "shell" : true,
  "working_dir" : "$file_path"
}
</pre>
