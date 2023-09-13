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
<img width="732" alt="2" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/a881904d-f176-445f-b755-ad38c1be7240">

3. Look up the ```touch``` program. The ```man``` program is your friend.
<img width="728" alt="3" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/00e146a2-7ba6-4c4e-8e7b-ed47d991a07b">

4. Use ```touch``` to create a new file called ```semester``` in ```missing```.
<img width="728" alt="4" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/6eb0f2b9-81ee-4994-a50a-866aac9b570e">

5. Write the following into that file, one line at a time:
```
#!/bin/sh
curl --head --silent https://missing.csail.mit.edu
```
<img width="731" alt="5" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/2a7d862b-9ab1-43c6-8550-1b35eaf9ad7e">

6. Try to execute the file, i.e. type the path to the script (```./semester```) into your shell and press enter. Understand why it doesn’t work by consulting the output of ```ls``` (hint: look at the permission bits of the file).
<img width="730" alt="6" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/3ee9a260-77fe-4d78-8a6d-4de1cb8c74d8">

7. Run the command by explicitly starting the sh interpreter, and giving it the file ```semester``` as the first argument, i.e. ```sh semester```. Why does this work, while ```./semester``` didn’t?
<img width="731" alt="7" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/eed03c15-6761-4595-a57b-155d73e7737d">

8. Look up the ```chmod``` program (e.g. use ```man chmod```).
<img width="734" alt="8" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/e1d6d143-17e0-4528-ad2c-b229c854356c">

9. Use ```chmod``` to make it possible to run the command ```./semester``` rather than having to type ```sh semester```. 
<img width="728" alt="9" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/2c875b2c-3d3f-49c2-ae30-7d8b8f3b442f">

10. Use ```|``` and ```>``` to write the “last modified” date output by ```semester``` into a file called ```last-modified.txt``` in your home directory.
<img width="731" alt="10" src="https://github.com/fan2goa1/CS_Notes/assets/31031356/2f038577-b612-42cb-a310-8b60d6723cde">

11. Write a command that reads out your laptop battery’s power level or your desktop machine’s CPU temperature from ```/sys```. Note: if you’re a macOS user, your OS doesn’t have sysfs, so you can skip this exercise.




