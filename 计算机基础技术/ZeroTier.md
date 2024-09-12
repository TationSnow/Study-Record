## Ubuntu安装

```bash
curl -s https://install.zerotier.com | sudo bash
```



## Ubuntu 配置

安装完成后，我们需要启动Zerotier服务并加入一个网络。在这里，你需要替换<network_id>为你想加入的Zerotier网络ID。

```bash
sudo systemctl start zerotier-one
sudo zerotier-cli join <network_id>
```

加入网络后，你可以查看Zerotier的状态并获取节点ID。

```bash
sudo zerotier-cli info
```

```bash
// 启动
sudo systemctl start zerotier-one.service
 
// 停止
sudo systemctl stop zerotier-one.service
```



可选：为了提高性能，我们可以调整一些配置参数。编辑Zerotier的配置文件/var/lib/zerotier-one/local.conf:

```bash
{
    "settings": {
        "primaryPort": 9993,
        "allowTcpFallbackRelay": false
    }
}
```

primaryPort是Zerotier服务使用的主要端口，allowTcpFallbackRelay设为false可以禁用TCP回退机制，以提高性能。

最后，重启Zerotier服务使配置生效。

```bash
sudo systemctl restart zerotier-one
```



## 自搭建Plante与Moon节点

https://www.bilibili.com/video/BV1Vh411F7Mr



### 创建Moon节点

1. 在Ubuntu（云服务器上）安装Zerotier

2. 防火墙放行9993udp端口

3. 进入Zerotier配置文件夹

   1. ```bash
      cd /var/lib/zerotier-one
      ```

   2. ```bash
      # 导出Moon节点配置信息
      zerotier-idtool initmoon identity.public >>moon.json
      ```

   3. ```bash
      # 修改配置
      nano moon.json
      ```

   4. ```bash
      # 在stableEndpoints中填写公网IP和9993端口如：
      "stableEndpoints": ["47.96.96.115/9993"]
      # 保存退出
      ```

   5. ```bash
      # 创建Moon节点服务器配置文件
      zerotier-idtool genmoon moon.json
      # 会生成一个以00000开头的Moon服务配置文件
      ```

   6. ```bash
      # 创建一个moons.d文件夹
      mkdir /var/lib/zerotier-one/moons.d
      ```

   7. ```bash
      # 将该文件cp到这个文件夹内
      cp 00000xxxxxxxx.moon ./moons.d/
      ```

   8. ```bash
      # 重启Zerotier服务
      systemctl restart zerotier-one 
      ```

4. 加入Moon节点（两中方式）

   1. 客户端中使用orbit加入Moon节点

      1. ```bash
         zerotier-cli orbit 节点ID 节点ID
         ```

      2. Tip：节点ID是云服务器的节点ID，可以在云服务器中使用zerotier-cli info 查看自己的ID

      3. ```bash
         # 可以通过命令查看是否成功
         # 查看role列下是否有Moon一行
         zerotier-cli listpeers
         ```

   2. 手动copy配置文件到客户端中
   
      1. 把刚刚创建出来的00000xxxxx.moon文件下载下来
      2. 手动放到客户端的zerotier配置文件夹中
      3. 不同的操作系统文件夹位置不一致
      4. Linux：/var/lib/zerotier-one/moons.d/
      5. Windows：C:\ProgramData\Zerotier\One\moons.d\
      6. MacOS：/Library/Application Support/ZeroTier/One/moons.d/
      7. 没有文文件夹就创建文件夹
      8. Android 想要加入需要第三方客户端
      9. OS苹果手机暂不支持



### 搭建自己的Plante节点控制器

1.  在云服务器中一步一步执行下列代码

   1. ```bash
      # 1. 将ztncui第三方开源UI下载到文件夹
      curl -O https://s3-us-west-1.amazonaws.com/key-networks/deb/ztncui/1/x86_64/ztncui_0.8.13_amd64.deb
      
      # 2. 解压
      dpkg -i ztncui_0.8.13_amd64.deb 
      
      # 3. 谜之操作
      sh -c "echo ZT_TOKEN=`sudo cat /var/lib/zerotier-one/authtoken.secret` > /opt/key-networks/ztncui/.env"
      
      sh -c "echo HTTP_ALL_INTERFACES=yes >> /opt/key-networks/ztncui/.env" 
      
      sh -c "echo NODE_ENV=production >> /opt/key-networks/ztncui/.env" 
      
      chmod 400 /opt/key-networks/ztncui/.env
      
      chown ztncui.ztncui /opt/key-networks/ztncui/.env
      
      # 4. 设置开机自启
      systemctl enable ztncui
      
      # 5. 重启UI
      systemctl restart ztncui
      ```

   2. 完毕后一定要打开云服务器的3000端口!!!!

   3. 使用公网IP+300端口的方式访问UI界面

   4. 初始账号为admin，密码为password

   5. 重置密码后，上方Add network新增网络

   6. 然后点击该网络 点击EasySetup 为虚拟内网创建网段

   7. 然后就可以正常加入该虚拟网络中了

   8. 将节点控制器加入到该虚拟网络中

   9. 云服务器上 添加网络：zerotier-cli join xxxxxxxxx

   



