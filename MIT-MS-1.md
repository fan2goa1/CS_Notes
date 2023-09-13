# MIT Missing Semester - Shell

## Lecture Overview

主要是一些简单的bash指令的介绍。

### basic command

**echo** 返回源的内容。echo $PATH给出所有的环境变量。

**which** 输出location of file

**pwd** print working directory

**--help** print out a bunch of information about the command

**flag & option** 有可选项的是option，只有一个-a这样的是flag

**ls -l** more information about a directory

**mv & cp** move & copy

**rm & rmdir** remove, rmdir只能移除僵尸粉空目录

**man** a manual page for a command

**tee** 不仅写入输出流，还写入标准输出流

### stream

Default input stream & output stream is the terminal

"<" redirect input stream

"<" redirect output stream

">>" append instead of overwrite

**cat** print一个文件的内容

**|** pipe管道符，左侧程序的输出作为右侧程序的输入

> ls -l  / | tail -n1

上述命令指将根目录下的文件详细信息的最后一行输出出来

### sudo

在linux中我们一般以一个用户的方式访问文件，而非root权限，但是对于一些特等的文件，以当前用户的权限我们不能够访问，所以需要用到sudo命令。

比如在sys/class/backlight目录下，能够调整我们当前的亮度，普通的```echo 500 > brightness```不能够完成这个操作(permission denied)。

但是我们用```sudo echo 500 > brightness```也不行，因为这个操作用到了重定向，我们只在echo 500这个命令使用了root权限，但是输出流的时候没有用到root权限，所以仍然permission denied。

所以我们需要使用```sudo su```登陆root才可以。或者使用```# echo ... ``` ，这个指令中的"#"意味着使用root权限执行命令。

### trick: 打开文件

在linux上为xdg-open命令，macos为open命令。

## Exercise

1. For this course, you need to be using a Unix shell like Bash or ZSH. If you are on Linux or macOS, you don’t have to do anything special. If you are on Windows, you need to make sure you are not running cmd.exe or PowerShell; you can use Windows Subsystem for Linux or a Linux virtual machine to use Unix-style command-line tools. To make sure you’re running an appropriate shell, you can try the command ```echo $SHELL```. If it says something like ```/bin/bash``` or ```/usr/bin/zsh```, that means you’re running the right program.
<img width="461" alt="Screenshot 2023-09-13 at 13 18 48" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/b220d399-c38d-49fb-ad9f-31a6be3c230d">

2. Create a new directory called ```missing``` under ```/tmp```.

