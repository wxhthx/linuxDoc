# service启动mysql报错的解决办法

```Bash
/usr/local/mysql/bin/mysqld: File './mysql-bin.~rec~' not found (Errcode: 13)
161214 17:48:40 [ERROR] MYSQL_BIN_LOG::open_purge_index_file failed to open register  file.
161214 17:48:40 [ERROR] MYSQL_BIN_LOG::open_index_file failed to sync the index file.
161214 17:48:40 [ERROR] Aborting
```
##原因分析：
    提示./mysql-bin.index无法找到（由于mysql开启了bin日志功能），到数据库根目录查看该文件是存在的，那就应该文件权限的问题，查看了数据库根目录的权限是700，所有者和用户组都是root，将其改为mysql(当前mysql的用户)。
    
```Bash
chgrp -R mysql /usr/local/mysql/data && chown -R mysql /usr/local/mysql/data
```
    重新启动mysql就可
