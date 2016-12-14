# linux下使用tar.gz文件安装mysql

## 安装前
1. 安装依赖的插件
```Bash
sudo apt-get install libaio1  
```
2. 创建用户组以及对应用户，都是mysql

```Bash
groupadd mysql
user mysql
```
## 安装步骤
1. 打开终端（ctrl + alt + t）,打开/etc/local路径,在该文件夹下新建tmp目录，将tar.gz文件拷贝到该目录下

```Bash
sudo cp ~/Downloads/mysql-5.5.48.tar.gz /etc/local/tmp/mysql-5.5.48.tar.gz
```

2. 将拷贝后的安装包解压至/etc/local/mysql-5.5.48

```Bash
sudo tar xzvf /etc/local/tmp/mysql-5.5.48.tar.gz
sudo mv  /etc/local/tmp/mysql-5.5.48 /etc/local
```
3. 为当前安装目录创建软连接

```Bash
sudo ln -s /etc/local/tmp/mysql-5.5.48 /etc/local/mysql
```
4.  修改权限给mysql
4.1 进入mysql目录
```Bash
cd mysql
```
4.2 修改权限

```Bash
sudo chown -R mysql .
sudo chgrp -R mysql .
```
5. 执行安装脚本
```bash
scripts/mysql_install_db --user=mysql 
```
如下图，系统会提示需要进行的操作，如拷贝mysql.service
6. 再次设置mysql目录拥有者
```Bash
sudo chown -R root . 
```
7. 设置data目录拥有者
```Bash
sudo chown -R mysql data
```
##配置
1. 初始化 root 用户密码
```Bash
sudo bin/mysqladmin -u root password 'new_password' 
```
2. 复制mysql.server 脚本 
```Bash
sudo cp support-files/mysql.server /etc/init.d/mysql.server
```
3. 安装mysql-client-core插件
```Bash
sudo apt-get install mysql-client-core
```

如果不安装该插件，无法通过mysql.service启动或者停止
4. 把 /usr/local/mysql/bin/mysql 命令加到用户命令中，这样就不用每次都加 mysql命令的路径 
```Bash
sudo ln -s /usr/local/mysql/bin/mysql /usr/local/bin/mysql  
```
然后重新启动系统
