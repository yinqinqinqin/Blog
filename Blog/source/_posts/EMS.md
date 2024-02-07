```
EMS（云服务器）
```



第一步 安装git

目的：使用git 初始化用户和邮箱



安装命令顺序

```
cd /usr/local/src/

#在https://www.kernel.org/pub/software/scm/git/中找到最新的安装包##以xz结尾
[root@localhost test1]#  wget https://www.kernel.org/pub/software/scm/git/git-2.15.1.tar.xz

[root@localhost test1]#  tar -vxf git-2.15.1.tar.xz

[root@localhost test1]#  cd git-2.15.1

[root@localhost test1]#  make prefix=/usr/local/git all

[root@localhost test1]#  make prefix=/usr/local/git install

[root@localhost test1]#  echo "export PATH=$PATH:/usr/local/git/bin" >> /etc/profile

[root@localhost test1]#  source /etc/profile

[root@localhost test1]#  git --version
```

问题一:安装最新的git时缺少依赖库

解决方法

安装对应的安装包

命令行输入：yum install curl-devel expat-devel gettext-devel  openssl-devel zlib-devel

第二步 生成公钥

在windows终端上可以快速登录云服务器

第三步 创建hexo博客框架

1.下载node

进入nodejs的GitHub存储库 选择对应版本的命令下载

node存储库[nodesource/distributions：NodeSource Node.js Binary Distributions (github.com)](https://github.com/nodesource/distributions)

因为

```
sudo yum install https://rpm.nodesource.com/pub_16.x/nodistro/repo/nodesource-release-nodistro-1.noarch.rpm -y
sudo yum install nodejs -y --setopt=nodesource-nodejs.module_hotfixes=1
```

使用 node -v 和npm -v 输出版本信息 即成功

2.使用npm命令安装hexo框架

```
npm install hexo-cli -g
```

问题一：显示npm版本过低

3.初始化hexo

```
hexo init [博客文件名] 
```

第四步 安装screen

让hexo能在后台运行

```
yum install screen
#which screen  --查看是否安装成功
--screen 基本命令
```

