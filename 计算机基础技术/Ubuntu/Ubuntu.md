# Ubuntu 从入门到入土

## 内置指令文档

### Man

语法：man [页编号] [命令或者配置]

```shell
man ls
man ll
...
```

### Help

语法：help 命令

```shell
help cd
```

## 常用快捷键

| 快捷键   | 功能                    |
| -------- | ----------------------- |
| Ctrl + C | 停止进程                |
| Ctrl + L | 清屏（彻底清屏是reset） |
| Ctrl + Q | 退出                    |
| Tab键    | 提示（可以防止敲错）    |
| 上下键   | 查找执行过的语句        |
| Ctrl + U | 清楚当前敲得命令        |
| Home     | 回到当前输入的头部      |
| End      | 回到当前输入的尾部      |



## FinalShell 设置连接信息

SSH连接默认端口22

Ubuntu系统默认会开启一个22端口

主机IP地址

认证方法

账户名与密码

## SSH 连接

### 安装SSH

在Ubuntu中打开终端，安装SSH连接

```shell
sudo apt install -y ssh
```

### 启动SSH服务

```Shell
service ssh start
```

### 检测SSH服务是否成功启动

出现sshd即说明启动成功！

```Shell
ps -e | grep ssh
```

### 启用SSH命令

```shell
systemctl enable
```

## APT包管理器 

APT是Debian及其派生Linux的软件包管理器，可以自动下载，配置，安装二进制或者源代码格式的软件包，因此简化了Unix系统上管理软件的过程

```shell
# 查看apt的所有命令(包括查看软件包，移除卸载等)
apt
# apt install
# apt remove 
# apt update
```



## Ubuntu 系统服务设置

### 关闭防火墙

默认开启防火墙的情况下除了22端口之外的所有端口都是用不了的



操作：start、stop、restart、status

```shell
systemctl 操作 服务名
systemctl start test.service
```

Tip：查看服务的方法 -> /users/lib/systemd/system目录下的文件列表，该目录下每个文件都对应一个服务

```shell
cd /usr/lib/systemd/system
ls
```

#### 查看网络服务

```shell
# 查看网络服务
sudo systemctl status NetworkManager
# 停止网络服务
sudo systemctl stop NetworkManager
# 启动网络服务
sudo systemctl start NetworkManager
# 停止网络服务
sudo systemctl restart NetworkManager 

```

#### 后台自启配置

```shell
# 查看服务开启启动状态
systemctl list-unit-files
# 关掉指定的服务的自动启动
systemctl disable service_name 
# 开启指定服务的自动启动
systemctl enable service_name 

```



#### 设置防火墙

```shell
# 查看防火墙状态
sudo systemctl status ufw
# 临时关闭防火墙
sudo systemctl stop ufw
# 设置开机时启动防火墙
sudo systemctl enable ufw
# 设置开机时关闭防火墙
sudo systemctl disable ufw
# 查看开机是否自启动服务
sudo systemctl is-enabled ufw
```



## Ubuntu常用命令

### 修改主机名

```shell
sudo hostnamectl --static set-hostname 要修改成的主机名
```

#### Host映射

在Windows中打开C:\Windows\System32\drivers\etc，打开其中的hosts文件

在末尾添加IP地址以及要映射的名称即可

```txt
192.168.25.21    ubuntu
```

### 用户管理命令

#### 新增用户

语法：adduser 用户名

```Shell
sudo adduser snow
```

#### 设置或更改用户密码

语法：password 用户名

```shell
sudo password snow
```


#### 查看创建了哪些用户

```shell
cat /etc/passwd
```



#### 切换用户

语法：su 用户名

```shell
# 切换用户 只能获取当前用户的执行权限 不能获取环境变量
su snow
# 切换用户 可以获得该用户的执行权限和环境变量
su - snow
```

 

#### 删除用户

语法：userdel 用户名

```shell
# 删除用户但保存用户主目录
userdel snow
# 用户和用户主目录都删除
userdel -r snow
```





#### 修改用户

语法：usermod -l 新用户名 老用户名

```shell
usermod -l snow tation
```



### 文件与路径相关内容

#### 查看当前路径

打印工作目录（显示当前工作目录的绝对路径）

```shell
pwd
```



#### 切换目录

语法：cd [路径]

```shell
# 前往桌面
cd /Desktop/
# 根目录
cd /opt/
# 回退到上一级目录
cd ..
# 回到默认路径
cd ~
cd
# 返回到上一次的目录（并不是上一级）
cd -
```

#### 查看当前目录下所有文件

语法：ls

```shell
# 查看所有文件
ls
# 查看所有文件（包含隐藏文件）
ls -a
# 查看所有文件详情信息
ls -l
ll
```

#### 创建目录与创建文件

语法：mkdir [属性] [路径]

```shell
# 在当前桌面下创建一层文件夹
mkdir test
# 创建多层文件夹
mkdir -p test/test01/test02
```

语法：touch [文件名称]

```shell
# 在当前目录下创建一个空目录
touch text
# 在指定路径下创建一个空目录
touch test/test01/test02
```



#### 复制文件

语法：cp [选项] 源文件 路径

```shell
# 复制单个文件到桌面
cp test.txt ~/Desktop/
# 递归复制整个文件夹到桌面
cp -r test/ ~/Desktop/
```

#### 删除文件

语法：rm [选项] 要删除的文件 

```shell
# 递归删除目录中的所有内容
rm -r test01/test02/test03.txt
# 强制执行删除操作，而不用提示进行确认
rm -f test01/test02/test03.txt
# 显示指令的详细执行过程
rm -v test01/test02/test03.txt
# 递归删除桌面目录所有内容
rm -rf ~/Desktop/
```

#### 查看文件

语法：cat [选项] 要查看的文件

查看文件内容 ,从第一行开始显示

```shell
# 显示所有行的行号 包括空行
cat -n test01/test02/test03.txt
```

Tip：一般用来查看比较小的文件，一个屏幕能够显示完全的

#### 移动文件

语法：mv

```shell
# 重命名文件
mv test01/test02/oldFileName test01/test02/newFileName
# 移动文件
mv test01/test02/text.txt ~/Desktop
```



### 搜索查找类指令

#### 查找指令

基本语法：find [搜索范围] [选项]

```shell
# 根据名称查找当前目录下所有一.txt结尾的文件
find ./ -name  "*.txt"
# 在当前目录下查找大于200字节的文件 +n 大于 -n小于 n等于
find ./ -size  +200c
# 查找当前目录下用户名称为-user的文件
find ./ -user atguigu
# 
```

#### 过滤查找与管道符

| 管道符表示将前一个命令的处理结果传递给后面的命令处理

基本语法：grep [选项] [查找内容] [源文件]

```shell
# 例如列出名称为mysql的文件
ll | grep mysql
# 例如列出名称不为mysql的文件（反向过滤）
ll | grep -v mysql
# 查看文件中带有if的语句段落
cat text.txt | grep -n if
```



### 压缩与解压缩

#### gzip / gunzip压缩（不好用）

基本语法：

gzip 文件 （只能压缩文件为*.gz文件）

gunzip 文件.gz （解压缩文件命令）

Tip：只能压缩文件不能压缩目录 ， 不保留原来文件

#### tar包（常用）

基本语法：tar [选项] XXX.tar.gz 将要打包进去的内容 （打包目录，压缩后的文件格式.tar.gz）

| 选项 | 功能               |
| ---- | ------------------ |
| -c   | 产生.tar 打包文件  |
| -v   | 显示详细信息       |
| -f   | 指定压缩后的文件名 |
| -z   | 打包同时压缩       |
| -x   | 解包.tar文件       |

Tip：当我们需要压缩文件的时候 zcvf，解压的时候使用zxvf

```shell
# 压缩多个文件 压缩后名称为 zipfile.tar.gz
tar -zcvf zipfile.tar.gz text01.txt text02.txt text03.txt 
# 压缩目录
tar -zcvf zipfile.tar.gz text01.txt text02.txt text03.txt xiyou/
# 解压文件（直接解压到当前目录下）
tar -zxvf ceshi.tar.gz
# 解压文件（解压到指定目录下）
tar -zxvf ceshi.tar.gz -C ~/Desktop/ceshi/
```





#### More文件内容分屏查看器

more指令是一个基于VI编辑器的文本过滤器，她以全屏幕的方式按页显示文本文件的内容。More指令中内置了若干快捷键。

语法：more 要查看的文件

```shell
more ~/Desktop/text.txt
```

| 操作     | 功能说明                         |
| -------- | -------------------------------- |
| Space    | 向下翻页                         |
| Enter    | 向下翻一行                       |
| Q        | 立即离开more，不在显示该文件内容 |
| Ctrl + F | 向下滚动一屏                     |
| Ctrl + B | 返回上一屏                       |
| =        | 输出当前行行号                   |
| :f       | 输出当前名和当前行的行号         |

#### Less 文件内容分屏查看器

功能比More更加强大，语法类似



#### tail 输出文件尾部内容

通常程序报错时可以用tail查看最后的几行的日志信息来快速定位错误


```shell
# 查看尾部文件（默认10行）
tail ~/Desktop/text.txt
# 查看尾部5条信息，5可以是任意行数
tail -n 5 ~/Desktop/text.txt
# 实时追踪该文档的实时更新
tail -f ~/Desktop/text.txt
```

#### echo 输出与重定向

语法：echo [选项] [输出内容]

```shell
echo "HelloWorld"
```

```shell
# 列表的内容写入文件a.txt中（覆盖写入）
ls -l > ~/Desktop/text.txt
# 列表的内容追加到文档aa.txt的末尾
ls -al >> ~/Desktop/text.txt
# 将文件1的内容覆写到文件2
cat ~/Desktop/text01.txt >> ~/Desktop/text02.txt
```

#### History查看历史命令

```shell
history
```

#### Date时间命令

基本语法：date [选项] [输出格式]

```shell
# 显示时间
date
# 显示当前时间粘年月日
date +%Y%m%d
# 显示当前时间年月日时分秒
date "+%Y年%m月%d日 %H:%M:%S" 
# 显示前一天时间
date -d '1 days ago'
# 显示明天时间
date -d '-1 days ago'
# 设置系统时间
date -s "2024-01-01 20:17:28"
```



#### 软链接

类似Windows中的快捷方式

语法：ln -s [原文件或目录] [软连接名称] 

```shell
# 创建软连接
ln -s t.txt ./test.txt
# 删除软连接 注意：rm -rf test/ 这样是删不掉的 不能在软连接后面加 /
rm -rf test
# 查看软连接 列表属性第一位是1 尾部会有位置指向的就是软连接
ll
# 进入软连接实际物理路径
cd -P test/
```



#### 在命令行中打开当前目录的资源管理器

```shell
nautilus
```





### 文本编辑器

#### vi & vim

```shell
sudo apt install vim
```

测试数据准备

```shell
cp /etc/profile ./
```

| 操作         | 功能                                |
| ------------ | ----------------------------------- |
| Alt + d数字d | 删除当前行（含）后多少行            |
| Alt + dd     | 删除当前行                          |
| Alt + x      | 剪切一个字母，当前光标（相当于DEL） |
| Shift + X    | 剪切光标前一个位置的字母            |
| Shift + zz   | 保存并退出                          |
| :w           | 保存                                |
| :q           | 退出                                |
| :!           | 强制执行                            |
| ...          | ...                                 |

## Ubuntu非常用命令



### 数据同步

适用于旧版本的Linux系统 ，新版系统如Ubuntu22.04已经不需要在每次关机或者重启时输入该命令了

```shell
sync
```

### 关机重启

```shell
# 挂起
halt
# 关闭系统并断电
poweroff
# 重启
reboot
```

``` shell
# 定时关机 (1分钟后关闭)
sudo shutdown -h 1
# 取消定时关机
sudo shutdown -c
```











## Ubuntu 安装常用软件







## Ubuntu 安装工作软件

### VSCode 2024

1. 官网下载deb安装包

2. 在命令行中打开该安装包所在位置

3. ```shell
   sudo dpkg -i c 安装包文件名.deb
   ```

4. 

### Intellij IDEA 2024



### PyCharm 2024



### Mysql 8.0



## 常见Ubuntu问题解决方案

### 等待缓存锁

```shell
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```



