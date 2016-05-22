## 安装 hexo

```linux
sudo npm i -g hexo # 全局安装hexo

hexo init # 初始化项目
```

## 更改配置文件
项目对应文件为 <code>_config.yml</code>

```linux
npm i hexo-deployer-git --save
```

## hexo 常用命令

```linux
hexo new"postName" #新建文章

hexo new page"pageName" #新建页面

hexo generate #生成静态页面至public目录

hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）

hexo deploy #将.deploy目录部署到GitHub

hexo help # 查看帮助

hexo version #查看Hexo的版本
```

## 部署步骤

```linux
hexo clean

hexo generate

hexo deploy
```

## 其他
有时需要执行以下命令
```linux
npm i hexo-server --save
```

