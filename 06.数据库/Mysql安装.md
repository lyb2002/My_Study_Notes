# Mysql安装

## MySQL RPM 软件包结构

**表 2.7 MySQL Community Edition 的 RPM 包**

| 软件包名称                        | 总结                                                         |
| :-------------------------------- | :----------------------------------------------------------- |
| `mysql-community-client`          | MySQL 客户端应用程序和工具                                   |
| `mysql-community-client-plugins`  | MySQL客户端应用程序的共享插件                                |
| `mysql-community-common`          | 服务器和客户端库的通用文件                                   |
| `mysql-community-devel`           | MySQL数据库客户端的开发头文件和库 应用                       |
| `mysql-community-embedded-compat` | MySQL服务器作为嵌入式库，<br />与应用程序兼容 使用库的版本 18 |
| `mysql-community-icu-data-files`  | MySQL正则表达式所需的ICU数据文件的MySQL打包                  |
| `mysql-community-libs`            | MySQL 数据库客户端应用程序的共享库                           |
| `mysql-community-libs-compat`     | 以前MySQL安装的共享兼容性库;<br />只 如果以前的MySQL版本受 平台 |
| `mysql-community-server`          | 数据库服务器和相关工具                                       |
| `mysql-community-server-debug`    | 调试服务器和插件二进制文件                                   |
| `mysql-community-test`            | MySQL服务器的测试套件                                        |
| `mysql-community`                 | 源代码 RPM 类似于 <br />mysql-community-8.2.0-1.el7.src.rpm，<br />取决于 在选定的操作系统上 |
| 其他 *debuginfo* RPM              | 有几个包： mysql-community-client-debuginfo，<br /> mysql-社区-libs-debuginfo <br />mysql-社区-服务器-调试-调试信息 <br />mysql-community-server-debuginfo 和 <br />mysql-community-test-debug信息。`debuginfo` |



## 安装

1、检查当前系统是否安装过MySQL

```bash
[root@mysql ~]# yum list | grep mariadb
mariadb-libs.x86_64                         1:5.5.56-2.el7             @anaconda
mariadb.x86_64                              1:5.5.68-1.el7             base     
mariadb-bench.x86_64                        1:5.5.68-1.el7             base     
mariadb-devel.i686                          1:5.5.68-1.el7             base     
mariadb-devel.x86_64                        1:5.5.68-1.el7             base     
mariadb-embedded.i686                       1:5.5.68-1.el7             base     
mariadb-embedded.x86_64                     1:5.5.68-1.el7             base     
mariadb-embedded-devel.i686                 1:5.5.68-1.el7             base     
mariadb-embedded-devel.x86_64               1:5.5.68-1.el7             base     
mariadb-libs.i686                           1:5.5.68-1.el7             base     
mariadb-libs.x86_64                         1:5.5.68-1.el7             base     
mariadb-server.x86_64                       1:5.5.68-1.el7             base     
mariadb-test.x86_64                         1:5.5.68-1.el7             base     
```

卸载mariadb,按Y确认。

```bash
[root@mysql ~]# rpm -qa|grep mariadb
mariadb-libs-5.5.56-2.el7.x86_64
[root@mysql ~]# yum remove mariadb-libs.x86_64
```



2、下载mysql社区版

```bash
[root@mysql ~]# wget https://dev.mysql.com/get/Downloads/MySQL-8.0/mysql-8.0.35-1.el7.x86_64.rpm-bundle.tar
```



3、解压mysql安装包：

```bash
[root@mysql ~]# tar -xvf mysql-8.0.35-1.el7.x86_64.rpm-bundle.tar -C /opt/mysql
```



4、安装

rpm 不会考虑包之间的依赖关系，因此要注意安装顺序。

注意：按照依赖关系依次安装rpm包 依赖关系依次为 ==common→libs→client→server==

```bash
cd /opt/mysql

# 安装MySQL依赖
rpm -ivh mysql-community-common-8.0.35-1.el7.x86_64.rpm 

rpm -ivh mysql-community-client-plugins-8.0.35-1.el7.x86_64.rpm 

rpm -ivh mysql-community-libs-8.0.35-1.el7.x86_64.rpm

# 安装mysql-client
rpm -ivh mysql-community-client-8.0.35-1.el7.x86_64.rpm 

# 安装mysql-server
sudo yum install libaio

rpm -ivh mysql-community-icu-data-files-8.0.35-1.el7.x86_64.rpm

rpm -ivh mysql-community-server-8.0.35-1.el7.x86_64.rpm
```



**5、启动MySQL服务**

```bash
systemctl start mysqld
systemctl restart mysqld
systemctl stop mysqld
```

**8、查询自动生成的root用户密码**

```bash
grep 'temporary password' /var/log/mysqld.log
```

命令行执行指令：

```bash
mysql -u root -p
```

然后输入上面查询到的自动生成的密码，完成登录。

**9、修改root用户密码**

登录到MySQL之后，需要将自动生成的不便记忆的密码修改了，修改成自己熟悉的便于记忆的密码。

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
```

会报错，密码不满足规则

将密码校验登记设置为最低

```mysql
set global validate_password.policy = 0;
set global validate_password.length = 6;
```

**10、创建用户**

==**默认的root用户只能当前节点localhost访问，是无法远程访问的，我们还需要创建一个root账户，用户远程访问**==

```mysql
create user 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
```

**11、给root用户分配所有权限**

```mysql
grant all on *.* to 'root'@'%';
```





# 更改UUID

问题描述：集群搭建时克隆主服务的镜像导致所有节点的服务UUID都一致，此时在集群中添加节点时会提示UUID冲突报错。



解决方案：

```mysql
# 1、利用uuid函数生成新的uuid
mysql> select uuid();
+--------------------------------------+
| uuid()                               |
+--------------------------------------+
| b07e3f5b-85e4-11ee-810c-000c29b8d243 |
+--------------------------------------+
1 row in set (0.01 sec)

# 2、查看配置文件目录
mysql> show variables like 'datadir';
+---------------+-----------------+
| Variable_name | Value           |
+---------------+-----------------+
| datadir       | /var/lib/mysql/ |
+---------------+-----------------+
1 row in set (0.00 sec)

# 3、编辑配置文件目录
vim /var/lib/mysql/auto.cnf

# 4、uuid修改新生成的uuid
server-uuid=b07e3f5b-85e4-11ee-810c-000c29b8d243

# 5、重启服务
systemctl restart mysqld
```



















