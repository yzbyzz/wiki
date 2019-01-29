# Git

## 设置

### 查看配置，并显示读取配置文件的位置

```shell
git config --show-origin --get user.email
```

### 免密操作

#### SSH
- 生成 ssh 密钥 `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
- 启动 ssh-agent `ssh-agent -s`
- 添加密钥到 ssh-agent `ssh-add ~/.ssh/id_rsa`
- 将密钥添加到 Git 站点（GitHub、gitee、gogs...）设置面板
- 验证连接 `ssh -T git@your-git-server-domain`
- 修改密钥密码  `ssh-keygen -p`
- 切换现有Git仓库地址

    ```shell
    git remote -v 
    git remote set-url origin your-git-repository-address 

    url sample：
    https://git.oschina.net/yzbyzz/hx_book_spider.git
    git@git.oschina.net:yzbyzz/hx_book_spider.g 
    ```

#### HTTP

- 让 git 记住密码 `git config credential.helper store`

- 首次 pull、push 仓库时，会提示输入账号密码

- 密码的保存位置

    - Linux/macOS 保存在 `~/.git-credentials`。每个网站用单独一行来记住密码，格式如下

    ```shell
    http://user:pass@example.com
    http://username%40company.com:abcdef@gogs.huxiao.com
    (username@company.com  abcdef)
    （邮箱使用 base64 编码。密码是否使用待定。）
    ```

    - Windows7、Windows10 搜索凭证管理器并设置正确的账号密码

       [参考链接](https://blog.csdn.net/qq_34665539/article/details/80408282)

### 区分文件大小写

```sheshellll
git config core.ignorecase false
```

### 忽略行末换行符
```sheshellll
git config --global core.whitespace cr-at-eol
```

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
  - 在 `~/work/` 下的 **Git 仓库目录** 中时 `git config [user.name](http://user.name)` 才会显示 `foo-work`
  - \- 在 `~/work/` 下的 **非** Git 仓库目录中时 `git config [user.name](http://user.name)` 会显示 `foo`

### 推送的文件大小

```shell
# 本地 push 的包体大小
git config --global http.postBuffer 52428800, 改为最大 50M)

# 服务器的包体大小限制
比如 Nginx 的 http.client_max_body_size  50M
```

> 设置过小时会报错 `“HTTP 413 curl 22 The requested URL returned error: 413 Request Entity Too Large”`

## 查看

### 查看仓库中每个人的提交统计

```shell
git shortlog -sne
```

### 查找版本库中的大文件

```shell
git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"

git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"
```

### 提交记录

```shell
# 最基本日志
git log

# 一行展示日志
git log  --oneline

# 带分支改变记录
git log --graph --decorate --oneline

# 每次提交的改动
git log --patch

# ?
git show COMMIT_ID/HEAD/BRANCH
```

### 暂存区

```
# 将当前的改动存入临时储藏区的(仅记录，已提交到版本库的文件)
git stash

# 临时保存未追踪的文件
git stash --include-untracked

git stash pop
git stash list
```

### 标签

```
# 推送指定 tag
git push origin <tag_name>

# 推送所有 tag
git push --tags
```

### 分支

#### 推拉

```shell
git fetch/pull/push origin REMOTE_BRANCH:LOCAL_REMOVE
```

- fetch
- pull
- Push

#### 建立联系

```
git branch --set-upstream-to=origin/dev dev
```

## 增删

### 合并分支上的某个提交

```shell
git checkout master
git cherry-pick 62ecb3
```

### 修改最近一次提交

```
# 删除上一次提交，重新写 `commit message`
git commit --amend
```

### 从版本库中彻底删除文件

> 通过文件名删除文件 使用下面的步骤来删除大文件：

- 使用下面的命令来删除你找到的第一个大文件：

  ```
  // git filter-branch --index-filter 'git rm --cached --ignore-unmatch filename' HEAD
  
  git filter-branch -f --prune-empty --index-filter 'git rm -rf --cached --ignore-unmatch FILE_NAME' --tag-name-filter cat -- --all
  ```

- 再次压缩:

  ```
  git gc  --prune=now
  ```

- 提交

  ```
  git push origin --force --all
  ```

### 删除不在版本库中的文件

```shell
# To remove directories, run 
git clean -f -d
# or 
git clean -fd

# To remove ignored files, run 
git clean -f -X
# or
git clean -fX

# To remove ignored and non-ignored files, run 
git clean -f -x
# or
git clean -fx
```

