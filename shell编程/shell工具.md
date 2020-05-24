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

