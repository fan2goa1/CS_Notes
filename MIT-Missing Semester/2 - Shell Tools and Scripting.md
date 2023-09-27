# Shell Tools and Scripting
## Lecture overview

### 保留关键字 reserved word
在写脚本的时候，形如```$1```指一条命令的第一个参数，在写脚本的时候我们可以利用它化简脚本中重复出现的内容。

```$#``` 是命令的参数数量。

```$$``` 是运行该命令的进程ID。

```$@``` 是展开命令中的所有参数。

```$_``` 指上一次命令中的最后一个参数。

```$?``` 指上一次命令执行完成后的错误代码(0表示正确执行没有错误，非0则有错误)。

```!!``` 指上一条命令。

### 逻辑运算符
```A || B``` 当前者错误运行后才会执行B，否则只执行A。

```A && B``` 当A正确运行后才会执行B，否则只执行A。

```A ; B``` 执行完A再执行B，没有约束。

### 替换 Substitution
#### 命令替换
```foo=$(pwd)``` 会将pwd得到的输出(也就是当前路径)存储到变量foo中。

```echo "we are at $(pwd)"``` (**注意是双引号**)会输出we are at [当前路径]。

#### 进程替换 process substitution
```cat <(ls) <(ls ..)``` 的作用是将上一层目录的内容存在一个临时文件中，将当前目录的内容存在一个临时文件中，然后将file handle交给cat命令，拼接后输出。所以得到的内容是当前目录和上一级目录的内容。

### 通配符 Wildcard
```ls *.sh``` 查找后缀为.sh的文件

```ls project?``` "?"只展开一个字符进行搜索

```convert image.png image.jpg```可以写成```convert image.{png,jpg}```

```touch {foo,bar}/{a..j}``` 可以进行一个笛卡尔积式的展开

```find . -name src -type d``` 这条指令的意思是在当前目录下使用find，找名字为src，type为目录(directory)的路径；```find . -path "**/test/*.py -type f"```即使在当前目录下使用find，找路径是xxx的python文件。

```fd```命令用正则表达式来搜索相关内容。

### Shellcheck
```shellcheck```可以帮助分析shell脚本中的语法错误等。

## An example .sh script
```bash
#!/bin/bash
echo "Starting program at $(date)" # Date will be substituted

echo "Running program $0 with $# arguments with pid $$"

for file in "$@"; do
  grep foobar "$file" ? /dev/null 2> /dev/null
  # When pattern is not found, grep has exit status
  # We redirect STDOUT and STDERR to a null register place

  if [["$?" -ne 0]]; then
    echo "File $file does not have any foobar, adding one"
    echo "# foobar" >> "$file"
  fi
done
```

The program above is to find the word "foobar" in those files, and if a file don't contain "foobar", then add "# foobar" to the end of the file.

## An example .py script
```python
#!/usr/bin/env python
import sys
for arg in reversed(sys.argv[1:]):
  print(arg)
# foobar
```
将参数倒序输出。

## Some Trivial Things
可以使用```tldr```去查看一些命令的使用例子，它不像```man```命令列出了所有文档内容，而是举例形式给出。
