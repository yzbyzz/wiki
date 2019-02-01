
## ssh

- 生成 ssh 密钥 `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
- [可选]启动 ssh-agent `ssh-agent -s`
- [可选]添加密钥到 ssh-agent `ssh-add ~/.ssh/id_rsa`
  > 如果生成 rsa 时指定了密码，则在添加后无需每次都输入密码。
- 将密钥添加到目标位置
  - 服务器个人目录 `~/.ssh`
  - Git 站点（GitHub、gitee、gogs...）设置面板
- 验证连接 `ssh -T git@your-server-domain`
- 修改密钥密码  `ssh-keygen -p`

## putty

- 将 `id_rsa` 转成 `ppk` 格式
  - 打开 puttygen
  - 选择 `Conversions` - `Import key`
  - 选择 `id_rsa` 导入
  - 点击 `Save public key`、 `Save private key` 生成 `putty.pub`、`putty.ppk`

- 生成 `ppk` 密钥
  - 打开 puttygen
  - 点击 `Generate`，移动鼠标来生成 `ppk`
  - 点击 `Save public key`、 `Save private key` 生成 `putty.pub`、`putty.ppk`
