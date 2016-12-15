1. 到nodejs官网下载对应包文件
2. 将该tar.gz文件解压至一个固定目录下，如我的：/home/wxhthx/soft/nodejs
```Bash
tar xzvf ~/Downloads/node-v5.9.1-linux-x64.tar.gz /home/wxhthx/soft/nodejs
```
3. 将modejs的路径信息写进/etc/profile的环境变量中
```Bash
export NODE_HOME=/usr/local/node/node-v5.9.1-linux-x64
export PATH=$JAVA_HOME/bin:$GRADLE_HOME/bin:$NODE_HOME/bin:$PATH
```
4. 然后重启系统在任意路径下输入$ node -v 应该都能看到具体的nodejs版本号，这样配置有效解决了全局安装插件不报错但是无效的问题
