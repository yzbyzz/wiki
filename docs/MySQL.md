
## 安装

### Windows

- 下载软件并解压到 `INSTALL_PATH`（根据自己喜好）

[MySQL 官网](https://dev.mysql.com/downloads/mysql/)

- 设置环境变量
  - `MYSQL_HOME` 设为 `INSTALL_PATH`
  - `PATH` 添加 `%MYSQL_HOME%/bin`

- **以管理员权限**启动`命令提示符`
  - `Win` + `R` 或者
  - 在`文件资源管理器`的地址栏输入 `cmd` 并回车
  
- 生成 `data` 目录
 在`命令提示符`中输入 `mysqld --initialize-insecure --user=mysql`，在 `INSTALL_PATH` 目录下生成 `data` 目录

- 启动服务
`net start mysql`

- 登录并设置密码

```
# 不用输入密码，直接回车
mysql -uroot -p

use mysql;

# 查看已有的用户
select host,user,authentication_string from user;

# 设置密码
update mysql.user set authentication_string=password("YOUR_PASSWORD") where user = "root";

# 刷新权限
flush privileges;
```

### macOS

### Linux


## 参考
- [windows下安装Mysql—图文详解](https://www.cnblogs.com/reyinever/p/8551977.html)
