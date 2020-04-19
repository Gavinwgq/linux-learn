* 新增一个用户

> useradd gavin

执行命令后会在home目录下建一个和用户名相同的目录作为该用户的家目录，该用户登录后默认进入该目录

> useradd -d test gavin

新建用户并为用户指定家目录为test

* 设置密码

> passwd

* 删除用户

> userdel gavin

删除用户后，其家目录还保留

> userdel -r gavin

删除用户，并删除其家目录