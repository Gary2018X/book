# Freqtrade安装

## Freqtrade

执行以下命名 耐心等待一会

### Linux/MacOS

通过以下三行命令就能完成安装

```bash
git clone -b develop https://github.com/freqtrade/freqtrade.git
cd freqtrade
./setup.sh --install
```

但是一键安装ta-lib可能会出问题 如果报错还是得手动安装

### Windows

打开Cmd，输入命令安装freqtrade以及依赖：

```bash
git clone <https://github.com/freqtrade/freqtrade.git>
cd freqtrade
pip install -r requirements.txt
pip install -e .
freqtrade
```

## 安装ta-lib

可以到这个地址找适合自己的wheel：<https://www.lfd.uci.edu/~gohlke/pythonlibs/#ta-lib>
然后通过wheel安装

```bash
pip install build_helpers/TA_Lib-0.4.24-cp38-cp38-win_amd64.whl
```

输入freqtrade时，显示以下信息说明安装成功：

```bash
(freqtrade) D:\CODE\trader\freqtrade>freqtrade
2022-02-17 19:40:50,174 - freqtrade - ERROR - Usage of Freqtrade requires a subcommand to be specified.
To have the bot executing trades in live/dry-run modes, depending on the value of the `dry_run` setting in the config, run Freqtrade as `freqtrade trade [options...]`.
To see the full list of options available, please use `freqtrade --help` or `freqtrade <command> --help`.
```

## docker-compose方式运行

### 存储docker-compose文件

创建一个新目录并将docker-compose 文件放在此目录中。

```bash
mkdir ft_userdata
cd ft_userdata/
# 下载docker-compose 文件 也可以直接下载好传进去
curl https://raw.githubusercontent.com/freqtrade/freqtrade/stable/docker-compose.yml -o docker-compose.yml

# 获取 freqtrade 镜像
docker-compose pull

# 创建用户目录结构
docker-compose run --rm freqtrade create-userdir --userdir user_data

# 创建配置信息 - 需要回答一些问题
docker-compose run --rm freqtrade new-config --config user_data/config.json

```

上面的代码片段创建了一个名为 的新目录ft_userdata，下载最新的 compose 文件并拉取 freqtrade 镜像。代码段中的最后 2 个步骤使用user_data，然后通过回答的问题结果配置创建目录。

配置文件可以随时修改。修改ft_userdata/user_data下的config.json即可。
也可以修改docker-compose.yml

### 添加自定义策略

1. 确保user_data/config.json可用
2. 将自定义策略复制到目录user_data/strategies/
3. 将策略的类名添加到docker-compose.yml文件中

### 获取UI

如果已在该new-config步骤中选择启用 FreqUI，则您将在 port 处获得 freqUI localhost:8080。

可以通过在浏览器中键入 localhost:8080 来访问 UI。

允许远程访问，参考如下链接
<https://www.freqtrade.io/en/stable/rest-api/#configuration-with-docker>

### 运行

```bash
docker-compose up -d

```

### 查看日志

可以使用docker-compose ps. 这应该将服务freqtrade列为running. 如果不是这种情况，最好检查日志（见下一点）。

日志将写入：user_data/logs/freqtrade.log。
您还可以使用命令查看最新日志docker-compose logs -f。

### 数据库

数据库将位于：user_data/tradesv3.sqlite

### 问题

1. UI界面出不来

## 参考地址

1. 项目github官网：<https://github.com/freqtrade/freqtrade>
2. 基本安装和使用：<https://zhuanlan.zhihu.com/p/468805841>
3. 官网使用教程：<https://www.freqtrade.io/en/stable/docker_quickstart/>
