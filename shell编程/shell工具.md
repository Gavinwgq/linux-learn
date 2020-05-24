* cut  cut命令从文件的每一行剪切字节、字符和字段并将这些数据进行输出

> 基本用法:cut[选项参数] filename

常用选项;

选项|功能
---|---
-f|列号，提取第几列，下标从1开始
-d|分隔符，默认分隔符为制表符

示例：

准备一个测试文件cut.txt,内容如下
```
zhang san
li si
wang     wu
zhao  liu
```
执行以下指令
> cut -d " " -f 1 cut.txt

输出结果为：
```
zhang
li
wang
zhao
```
获取多列(不连续用逗号，连续的用短横线)

> cut -d " " -f 1,2 cut.txt

打印出wang

> cat cut.txt |grep wang |cut -d " " -f 1

选取系统PATH变量值第2个“:”后的所有路径

> echo $PATH|cut -d : -f 3-

* sed 

> sed是一种流编辑器，它一次处理一行内容。处理时，把当前处理的行存储在临时缓冲区中，称为“模式空间”，接着用sed命令处理缓冲区中的内容，处理完成后，把缓冲区的内容送往屏幕。接着处理下一行，这样不断重复，直到文件末尾。文件内容并没有改变，除非你使用重定向存储输出。

> 基本用法：sed[选项参数] 'script' filename

选项参数：
参数|功能
---|---
-e|以选项中指定的script来处理输入的文本文件
-f<script文件>|以选项中指定的script文件来处理输入的文本文件
-h或--help|显示帮助
-V或--version|显示版本信息

常用命令：
命令|功能
---|---
a|新增， a 的后面可以接字串，而这些字串会在新的一行出现(目前的下一行)
d|删除
i|插入， i 的后面可以接字串，而这些字串会在新的一行出现(目前的上一行)
s|替换，通常这个命令可以搭配正规表达式

示例：

准备一个测试文件sed.txt,内容如下
```
zhang san
li si
wo wo men
wang wu
```

(1)在第二行后面添加一行内容'zhaoliu'

> sed '2a zhaoliu' sed.txt

(2)删除第二行

> sed '2d' sed.txt

(3)删除含有'wo'的行

> sed '/wo/d' sed.txt

(4)将'wo'替换为'ni'

> sed 's/wo/ni/g' sed.txt

其中g代表全局替换

(5)删除第二行并将'wo'替换为'ta'

> sed -e '2d' -e 's/wo/ta/g' sed.txt

* awk 

> awk是一个强大的文本处理工具，把文件逐行的读入，以空格为默认分隔符将每行进行切片，切开的部分再分别进行处理

> 基本用法：awk [选项参数] 'pattern1{action1} pattern2{action2}...' filename


pattern表示要查找处理的内容，即匹配模式

action表示对匹配的内容所作的处理

常用的选项参数：
选项|功能
---|---
-F|指定分隔符
-v|赋值一个用户定义变量

