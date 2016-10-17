
###[**安装**](http://nodered.org/docs/getting-started/installation)

-----
> **安装Node.js**

Node-RED支持Node.js 0.10.x或者更新的版本.

注意:  Node.js 5.x 和 npm 3.x 版本处于活动开发阶段, 并不推荐使用它们作为稳定的基线版本. 目前很多第三方的节点包并不能完整的支持Node 5.x或者更新的版本. 尤其是它们包含二进制运行组件时. 如果出现该情况, 请同支持包的开发者确认.

可以在以下位置获取 Node4.x 的长期支持版本(LTS):

 - Linux安装包: [32-bit](https://nodejs.org/dist/latest-v4.x/node-v4.5.0-linux-x86.tar.gz) or [64-bit](https://nodejs.org/dist/latest-v4.x/node-v4.5.0-linux-x64.tar.gz)
 - Max OS X安装包r: [Universal](https://nodejs.org/dist/latest-v4.x/node-v4.5.0.pkg)
 - Windows安装包: [32-bit](https://nodejs.org/dist/latest-v4.x/node-v4.5.0-x86.msi) or [64-bit](https://nodejs.org/dist/latest-v4.x/node-v4.5.0-x64.msi)

更简单的方法是使用为你当前使用操作系统定制的[安装包版本](https://nodejs.org/en/download/package-manager/).

同时也存在针对特定硬件平台的安装指南:

 - [树莓派(Raspberry Pi)](http://nodered.org/docs/hardware/raspberrypi)
 - [BeagleBone Black](http://nodered.org/docs/hardware/beagleboneblack)

针对Node.js的其他下载选项在[这里](https://nodejs.org/dist/latest-v4.x/)


-----
> **安装Node-RED**

最简单的安装Node-RED的方法是使用node的包管理器, npm. 使用它将命令行的node-red以公共模块的方式安装到系统路径中:

    sudo npm install -g --unsafe-perm node-red

-----

    注意: 
    不要使用npm1.x的版本来安装Node-RED. 可以使用以下命令更新到最新的npm版本: sudo npm install -g npm@2.x
    
    注意: 
	以非root用户的方式在Linux/OS X系统上安装是需要sudo命令的. 如果在Windows上安装, 需要以管理员权限在命令行模式中运行. 则不需要sudo命令(**`小白连这都不知道么!`**).
	
    注意:
    安装过程中, node-gyp命令可能会报告一些错误. 这些是一些常见的非致命性错误, 是由于某些选项依赖需要由对应的编译器来完成而引起的. Node-RED可以不需要这些选项依赖而工作, 但是有可能你额外需要的node模块需要这些功能以编译本地代码. 你可以在[以下位置](https://github.com/TooTallNate/node-gyp#installation)查看如何安装node-gyp的依赖.

下一步:

安装完成之后,你就可以开始[使用Node-RED](http://nodered.org/docs/getting-started/running)了.


-----
> **其他安装方法**

**下载发行版本**

你可以在**[以下](https://github.com/node-red/node-red/releases/latest)**位置下载最新的发行版本. 下载的zip文件包含有名为node-red-X.Y.Z的顶级目录, 其中X.Y.Z为版本号. 当下载并解压完成后, 在该目录中运行以下命令:

    npm install --production

为开发而使用 - 从[GitHub](https://github.com/)中获取

从Github中获取和运行代码仅对基于node-red的开发者和希望对其进行贡献的开发者有用.

可以从Github的以下代码库中直接克隆代码:

    git clone https://github.com/node-red/node-red.git

克隆完成之后, node-red核心依赖模块必须被先行安装:

    cd node-red
    npm install

**注意:**基于git仓库的克隆版本进行安装时, 所有的依赖模块都必须安装, 而不仅限于产品级别的依赖. 这就是为什么最好不要使用--production选项的原因(**`基于production? 是因为开发模型对于依赖的调用会随着依赖库的升级而改变吗?`**)

同时需要安装**`grunt-cli`**以使得在使用应用前能够编译出应用. 该工具需要全局安装.

    sudo npm install -g grunt-cli

完成之后可以编译和运行基于node-red的应用.

    grunt build
    node red

-----

> **串口节点支持**

当使用Node.js v0.10.x或者 v0.12.x时, 如果需要使用串口节点的支持, 你需要手动的安装串口节点的早期版本, 操作如下:

    cd $HOME/.node-red
    npm install node-red-node-serialport@0.0.5


> **Next steps**

完成安装动作后, 就可以开始运行Node-RED.

**`[为了小白翻译. 成长为老司机]`**

-----

> update on stackedit.on @ win7



