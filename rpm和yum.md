### rpm和yum

* rpm 

一种用于互联网下载包的打包及安装工具，它包含在某些 Linux 分发版中。它生成具有.RPM 扩展名的文件。RPM 是 RedHat Package Manager（RedHat 软件包管理工具）的缩写，类似 windows 的 setup.exe，这一文件格式名称虽然打上了 RedHat 的标志，但理念是通用的。

Linux 的分发版本都有采用（suse,redhat, centos 等等），可以算是公认的行业标准了。

rpm 包的常用指令

> rpm	–qa|grep <软件名>  

查询已安装的rpm列表（按名称过滤了）

> rpm -qa  

查询所安装的所有 rpm 软件包

> rpm -qi <软件包名>   

查询软件包信息

> rpm -ql <软件包名>   

查询软件包中的文件

> rpm -qf <文件全路径名> 

查询该文件所属的软件包

> rpm -e <RPM包的名称>

卸载 rpm 包 ，特别说明：-e后带上--nodeps就是强制删除（不建议使用）

> rpm -ivh	<RPM包全路径名称>

安装rpm包 

参数说明：

参数|含义
---|---
-i|install 安装
-v|verbose 提示
-h|hash 进度条

rpm 包名基本格式

一个 rpm 包名：firefox-45.0.1-1.el6.centos.x86_64.rpm 

项|名称
---|---
名称|firefox
版本号|45.0.1-1
适用操作系统|el6.centos.x86_64 表示 centos6.x 的 64 位系统如果是 i686、i386 表示 32 位系统，noarch 表示通用

* yum

Yum 是一个 Shell 前端软件包管理器。基于 RPM 包管理，能够从指定的服务器自动下载 RPM 包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。使用 yum 的前提是可以联网。

常用指令

> yum list|grep <软件名> 

列举可用的软件包

> yum install <软件名>

安装软件（默认安装最新版本，软件名完整包含版本号时安装指定的版本）

