# Node.js安装

node.js 是 js 在服务端运行的环境基础,从而使得 js 从浏览器端延伸到服务端领域,而 gitbook 则是运行在 node.js 基础之上的命令行工具,因此必须先安装好 node.js 开发环境.

如果打印出 node.js 版本信息,则表示本机已安装 node.js 环境,跳过此步骤.

```bash
node --version
```

## 安装node

Node.js 安装包及源码下载地址为：<https://nodejs.org/en/download/>。
可以根据不同平台系统选择你需要的 Node.js 安装包。
Node.js 历史版本下载地址：<https://nodejs.org/dist/>

### Linux 上安装 Node.js

#### Ubuntu apt-get 命令安装 （推荐）

```bash
sudo apt-get install nodejs
sudo apt-get install npm
```

#### 直接使用已编译好的包

Node 官网已经把 linux 下载版本更改为已编译好的版本了，我们可以直接下载解压后使用：

```bash
wget https://nodejs.org/dist/v10.9.0/node-v10.9.0-linux-x64.tar.xz    // 下载
tar xf  node-v10.9.0-linux-x64.tar.xz       // 解压
cd node-v10.9.0-linux-x64/                  // 进入解压目录
./bin/node -v                               // 执行node命令 查看版本
v10.9.0
```

解压文件的 bin 目录底下包含了 node、npm 等命令，我们可以使用 ln 命令来设置软连接：

```bash
ln -s /usr/software/nodejs/bin/npm   /usr/local/bin/ 
ln -s /usr/software/nodejs/bin/node   /usr/local/bin/
```

#### Ubuntu 源码安装 Node.js

以下部分我们将介绍在 Ubuntu Linux 下使用源码安装 Node.js 。 其他的 Linux 系统，如 Centos 等类似如下安装步骤。

在 Github 上获取 Node.js 源码：

```bash
sudo git clone https://github.com/nodejs/node.git
Cloning into 'node'...
```

修改目录权限：

```bash
sudo chmod -R 755 node
```

使用 ./configure 创建编译文件，并按照如下顺序执行：

```bash
cd node
sudo ./configure
sudo make
sudo make install
```

### Mac OS 上安装

可以通过以下两种方式在 Mac OS 上来安装 node：
1、在官方下载网站下载 pkg 安装包，直接点击安装即可。
2、使用 brew 命令来安装：

```bash
brew install node
```

### Windows 上安装 Node.js

可以采用以下两种方式来安装。安装完成后可以将node加入环境变量 方便使用

#### 1、Windows 安装包(.msi)

在官网找到适合自己的系统的msi文件下载到本地
然后双击运行一路next就行

#### 2、Windows 二进制文件 (.exe)安装

在官网找到适合自己的系统的二进制文件下载到本地
双击运行 点击run出现命令行界面表示成功

## 参考链接

<https://www.runoob.com/nodejs/nodejs-install-setup.html>
