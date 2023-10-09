# CentOS 7



## 切换用户

```bash
su root
```









## 网络配置

### 设置静态ip

**通过控制台命令修改：**

1. **进入IP配置文件**

```bash
vim /etc/sysconfig/network-scripts/ifcfg-ens33
```



2. **将启动协议由DHCP改成static**，由动态分配IP改为静态分配IP

    需要加上自定义的静态IP地址、网关、域名解析器。

```python
BOOTPROTO="static"

ONBOOT="yes" #系统启动的时候网络接口是否有效（yes/no）

# 在最后要加三项内容
#IP 地址
IPADDR=192.168.201.100
#网关
GATEWAY=192.168.201.2
#域名解析器
DNS1=192.168.201.2

#子网掩码
NETMASK=255.255.255.0 #默认就是这个，可以不加
```

​		

3. **重启当前的网络环境**

```bash
service network restart
```



### 修改主机名称

1. **查看当前的主机名**： `hostname` 



2. **通过文件修改主机名**：文件位置：`/etc/hostname`

    `vim /etc/hostname`

    需要重启生效。



3. **快捷命令**： `hostnamectl`

    会显示出与主机名相关的系统信息。

    修改主机名：

```bash
hostnamectl set-hostname hadoop100(要修改的主机名)
```

