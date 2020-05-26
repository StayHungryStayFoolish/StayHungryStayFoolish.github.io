---
    title: Hexo 多环境同步管理
---

# Hexo 简易教程

## 部署到 GitHub Page

### 1. 创建与 GitHub 同名的 Repo

- `Github` 用户名以 `io` 结尾 
    
    - github-username.github.io

- Git clone
    
    - 克隆到本机，执行 **Hexo Install** 步骤
    
### 2. 备份到分支

- 创建分支，并提交到分支

- 保证分支提交以下目录

        source
        themes
        _config.yml
        db.json
        package.json
        .deploy_git
 
- 在 `Github` 的 `Repo` 进入 `Settings -> Branches`，将分支修改为 `default`。    
    
    
# Hexo Install

### 1. 安装 Hexo

```bash
npm install hexo-cli -g
```

### 2. 在指定文件夹生成 Hexo 文件

```bash
mkdir blog
cd blog
hexo init
```

   > 生成文件夹
   
        .
        ├── _config.yml  # 配置文件
        ├── package.json
        ├── scaffolds
        ├── source
        |   └── _posts  # Markdown 文章位置
        └── themes      # 主题下载及存放位置      
        
### 3. 安装 Hexo git 工具

```bash
npm install hexo-deployer-git --save
```         

### 4. 安装主题

```bash
cd themes
git clone 主题地址
cd 主题
ls -a
# 删除主题下的 .git 文件夹
rm -rf .git
```

### 5. 配置 GitHub 仓库

- 在 `_config.yml` 文件配置 `Git`，使用 `https` 在每次执行 `hexo d` 命令需要输入用户名和密码，如果不需要请按照 `SSH Key` 配置。

```bash
deploy:
  type: git
  repo: https://github.com/***/***.github.io.git
  branch: master # master 用来保存 hexo 根据 md 文件生成的静态页面，分支保存源文件进行多环境协同工作
```

### 6. 本地测试及远程部署

```bash
# 清除 hexo generate 生成的 public 文件
hexo clean  

# 生成静态文件
hexo generate

# 本地调试
hexo server

# 部署到 GitHub Page 独立域名
# _config.yml 文件指定的 git 地址
hexo deploy

# 简写
hexo g -d
```    
