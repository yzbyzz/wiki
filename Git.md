# Git

## 设置

### 免密操作

- 生成ssh密钥 `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
- 启动 ssh-agent `ssh-agent -s`
- 添加密钥到 ssh-agent `ssh-add ~/.ssh/id_rsa`
- 将密钥添加到 Git 站点（GitHub、gitee、gogs...）设置面板
- 验证连接 `ssh -T git@your-git-server-domain`
- 修改密钥密码  ``` ssh-keygen -p`
- 切换现有Git仓库地址

```shell
git remote -v 
git remote set-url origin your-git-repository-address 

url sample：
https://git.oschina.net/yzbyzz/hx_book_spider.git
git@git.oschina.net:yzbyzz/hx_book_spider.g 
```

### 区分文件大小写

```sheshellll
git config core.ignorecase false
```

### 配置使用 HTTP 协议时的账号密码

Windows7、Windows10 搜索凭证管理器并设置正确的账号密码

[参考链接](https://blog.csdn.net/qq_34665539/article/details/80408282)

### 不同目录使用不同的用户名、邮箱

- 创建文件
  - 文件 `~/.gitconfig`

    ```shell
    [user]
        name = foo
        email = foo@bar.com
    [includeIf "gitdir: ~/work/"]
        path = .gitconfig-work
    ```

  - 文件 `~/.gitconfig-work`

    ```shell
    [user]
        name = foo-work
        email = foo-work@bar.com
    ```

- 注意点
  - `[includeIf]` 中的目录不要漏了最后的 `/`
  - 在 `~/work/` 下的 **Git 仓库目录**中时 `git config [user.name](http://user.name)` 才会显示 `foo-work`
  - \- 在 `~/work/` 下的**非** Git 仓库目录中时 `git config [user.name](http://user.name)` 会显示 `foo`

## 查看

### 查看仓库中每个人的提交统计
```shell
git shortlog -sne
```