> 以 CentOS 为准

## mail

- 日志位置 `/var/log/maillog`
- 邮件位置 `/var/mail/USER`、`/var/spool/mail/USER`
  (`/var/mail` 指向了 `/var/spool/mail`)

- 查看邮件
  - 使用 `vi/tail/head/cat` 等命令直接查看 `/var/mail/USER` 文件
  - `mail` 查看当前用户的邮件
  - `mail -f /var/mail/USER` 查看指定用户的邮件

### 邮件客户端

#### Postfix

- 配置文件

  - 所在目录 `/etc/postfix/`
  - 主要包括
    - `mail.cf`：是 postfix 主要的配置文件。
      - `inet_interfaces`：指定邮件系统接收的邮件的网络地址。不在指定范围内的邮件不会接收。
      - ...
    - `master.cf`：是 postfix 的 master 进程的配置文件，该文件中的每一行都是用来配置 postfix 的组件进程的运行方式。
    - ...

- 控制 `systemctl status/start/stop postfix`

#### Sendmail

#### Exim

#### qmail

### Ref

- [Is Postfix the same thing as Sendmail?](https://serverfault.com/questions/244263/is-postfix-the-same-thing-as-sendmail)
- [postfix 配置详解](http://os.51cto.com/art/201101/243430.htm)

## crontab

- 日志位置 `/var/log/cron`
- 记录位置 `/var/spool/cron/USER`
- 控制 `systemclt status/start/stop crond`
- 修改
  - 直接编辑 `/var/spool/cron/USER` 文件
  - 使用 `crontab -e`

### Ref

- [Linux 工具快速教程 - 19. crontab 定时任务](https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/crontab.html)

## 目录结构

[每天一个 linux 命令（23）：Linux 目录结构](https://www.cnblogs.com/peida/archive/2012/11/21/2780075.html)
