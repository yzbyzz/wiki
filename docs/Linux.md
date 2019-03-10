> 以 CentOS 为准

## mail

- 日志位置 `/var/log/maillog`
- 邮件位置 `/var/mail/USER`、`/var/spool/mail/USER`
  (`/var/mail` 指向了 `/var/spool/mail`)

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

#### Sendmail

#### Exim

#### qmail

### Ref

- [Is Postfix the same thing as Sendmail?](https://serverfault.com/questions/244263/is-postfix-the-same-thing-as-sendmail)
- [postfix 配置详解](http://os.51cto.com/art/201101/243430.htm)

## crontab
