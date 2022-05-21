# easySolana
本文记录作者学习Solana合约编程的过程,将环境部署，工具选择，程序开发等过程的操作步骤及思考记录下来。
后续会结合本文，输出一些小工具，方便各位初学者快速搭建环境，直接进入开发阶段

# 系统与账户

目前使用Ubuntu 20.04.2 LTS，我是直接在阿里云无影云桌面申请（新用户有免费试用期限），方便我随时随地移动学习，后续基础环境搭建完，也会直接出一个镜像

主账户：web3 ，授予管理员权限
软件及程序安装：/opt ，目录归属web3


# 科学上网

对学习web3的工程师，这个是必备，不管是学习理论，了解资讯还是下载程序依赖包都是必备的，能大大提升效率

# 科学上网-Shadowosocks-QT5 

Linux 使用 Shadowsocks 设置教程  https://shadowsockshelp.github.io/Shadowsocks/linux.html

# 科学上网-浏览器设置代理

安装 Foxyproxy 插件 

https://github.com/foxyproxy/firefox-extension 

# 科学上网-使用ProxyChain4终端设置代理

1.安装
sudo apt update
sudo apt install proxychains4

2.配置
sudo vim /etc/proxychains4.conf
注释掉socks4 127.0.0.1那一行，在最后加上代理工具的设置，如：
socks5 127.0.0.1 1080

3.使用方法
代理工具正常运行的前提下，在需要走代理的命令前打上proxychains4即可（但要在sudo后），即proxychains4 [命令]，如：
sudo proxychains4 apt update
proxychains4 git clone https://github.com/....

4. 自动补全命令
sudo gedit ~/.bashrc
在末尾增加补全命令：
complete -c proxychains4


# solana 开发环境部署 
https://solanacookbook.com/#contributing

安装NPM包管理工具,因NODEjs自带NPM包管理工具,后续也会依赖node开发dapp前端应用，所以直接安装nodejs
https://nodejs.org/zh-cn/  我安装最新尝鲜版，下载至/opt 目录下并解压 
配置环境变量
NODEJS_HOME=/opt/node-v18.2.0-linux-x64
PATH=$PATH:$NODEJS_HOME/bin
source /etc/profile 

使用npm管理依赖包
npm install --save @solana/web3.js 
npm install --save @solana/spl-token
npm install --save @solana/wallet-adapter-wallets \
    @solana/wallet-adapter-base
    
# install Rust

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
配置环境变量 
CARGO_HOME=/home/web3/.cargo
PATH=$PATH:$CARGO_HOME/bin
source /etc/profile

# 安装solana cli

直接下载编译完版本https://github.com/solana-labs/solana/releases/tag/v1.10.17 
下载 solana-release-x86_64-unknown-linux-gnu.tar.bz2  至/opt 目录下并解压 
配置环境变量 
SOLANA_HOME=/opt/solana-release
PATH=$PATH:$SOLANA_HOME/bin
source /etc/profile



