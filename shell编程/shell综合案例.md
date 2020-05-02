### 综合案例

需求：
```
1)每天凌晨 2:10  备份 数据库 atguiguDB 到 /data/backup/db
2)备份开始和备份结束能够给出相应的提示信息
3)备份后的文件要求以备份时间为文件名，并打包成 .tar.gz 的形式，比如：
2018-03-12_230201.tar.gz
4)在备份的同时，检查是否有 10 天前备份的数据库文件，如果有就将其删除。
```

1、在/usr/sbin编写备份脚本,名称定义为mysql_db_backup.sh

脚本内容：
```
#!/bin/bash

#设定备份文件地址和名称

BACKUP=/data/backup/db
DATETIME=$(date +%Y_%m_%d_%H%M%S)

echo "======开始进行数据库备份========="
echo "备份文件地址$BACKUP/$DATETIME.tar.gz"

#数据库相关信息
HOST=localhost
USER=root
PWD=root
DATABASE=atguiguDB

#检查备份路径是否存在，如果不存在创建之

[! -d "$BACKUP/$DATETIME" ] && mkdir -p "$BACKUP/$DATETIME"

# 执行数据库的备份

mysqldump -u${USER} -p${PWD} --host=${HOST} $DATABASE | gzip > $BACKUP/$DATETIME/$DATETIME.sql.gz

#打包
cd $BACKUP

tar -zcvf $DATETIME.tar.gz  $DATETIME 

#删除临时目录
rm -rf $DATETIME

#删除10天前的备份
find $BACKUP -mtime +10 -name "*.tar.gz" --exec rm -rf {} \;

echo "=====备份成功======"
```

2、执行crontab -e 添加一个定时任务

> 10 2 * * * /usr/sbin/mysql_db_backup.sh