
###[**运行**](http://nodered.org/docs/getting-started/running)

-----
当使用npm包管理器全局安装Node-RED后, 你可以使用以下node-red命令:

    $ node-red
    
    Welcome to Node-RED
    ===================
    
    25 Feb 22:51:09 - [info] Node-RED version: v0.14.6
    25 Feb 22:51:09 - [info] Node.js  version: v4.6.0
    25 Feb 22:51:09 - [info] Loading palette nodes
    25 Feb 22:51:10 - [warn] ------------------------------------------
    25 Feb 22:51:10 - [warn] [rpi-gpio] Info : Ignoring Raspberry Pi specific node
    25 Feb 22:51:10 - [warn] ------------------------------------------
    25 Feb 22:51:10 - [info] Settings file  : /home/nol/.node-red/settings.js
    25 Feb 22:51:10 - [info] User Directory : /home/nol/.node-red
    25 Feb 22:51:10 - [info] Server now running at http://127.0.0.1:1880/
    25 Feb 22:51:10 - [info] Creating new flows file : flows_noltop.json
    25 Feb 22:51:10 - [info] Starting flows
    25 Feb 22:51:10 - [info] Started flows

在此时, 可以通过**http://localhost:1880**来访问Node-RED编辑器.

同时针对特定硬件平台, 也存在定制的指导, 参见:

**[Raspberry Pi](http://nodered.org/docs/hardware/raspberrypi)**
**[BeagleBone Black](http://nodered.org/docs/hardware/beagleboneblack)** (**`该平台没玩过, 老司机不翻译了...`**)

**下一步**

此时可以开始创建你的首个[工作流程](http://nodered.org/docs/getting-started/first-flow).

-----
> **从本地安装中运行Node-RED -- 基于Linux Mac OS X平台**

即使Node-RED没有通过全局npm包管理器安装, 相关命令仍然是可以访问的.

如果通过npm来安装Node-RED, 在运行npm安装的相关路径中存在有脚本为 **`node_modules/node-red/bin/node-red`**. 如果是通过zip文件进行解压缩获得, 脚本路径为: **`node-red-X.Y.Z/bin/node-red`**.

第一步将node-red启动脚本设置为可执行属性:

    chmod +x <node-red-install-directory>/bin/node-red

然后通过以下命令执行Node-RED:

    <node-red-install-directory>/bin/node-red


-----
> **从本地安装中运行Node-RED -- 基于Windows平台**

在windows中,从你执行npm安装或者是解压缩zip文件的目录路径中执行对应js脚本:

    node node_modules/node-red/red.js


-----

> **命令行使用方法**

    Usage: node-red [-v] [-?] [--settings settings.js] [--userDir DIR] [flows.json]
    
    Options:
      -s, --settings FILE  use specified settings file
      -u, --userDir  DIR   use specified user directory
      -v                   enable verbose output
      -?, --help           show usage

**存储用户数据**

缺省情况下, Node-RED在目录**`$HOME/.node-red.`**中存储你的数据. 为了向前的兼容性, 如果Node-RED在当前安装路径中检测到了用户数据, 那么它将转而使用该数据(**`及目录 ?`**).  升级文档中包含有专门的章节描述如何从Node-RED安装路径之外进行数据迁移动作.

可以通过使用**`--userDir`**命令行选项来覆盖使用那个目录作为用户数据存储的设置.

**向底层node.js进程传递参数**

某些情况下Node-RED需要向底层node.js进程传递参数. 例如在**Raspberry Pi**或者是其他内存存储受限的设备上运行的时候.

为了完成该功能, 需要使用**`node-red-pi`**脚本来代替node-red脚本进行启动. 注意该脚本在windows中不可用.

另外, 在使用命令行模式运行Node-RED时, 需要先向node进程(**`node.js进程 ?`**)提供参数, 然后才能指定red.js和定义希望传递给Node-RED的参数.

以下命令说明这两种方法:

    node-red-pi --max-old-space-size=128 --userDir /home/user/node-red-data/
    node --max-old-space-size=128 red.js --userDir /home/user/node-red-data/


-----
> **启动时自动执行Node-RED**

启动时执行进程有许多中方法. 强烈建议**`Raspberry Pi`**用户使用[**推荐方法**](http://nodered.org/docs/hardware/raspberrypi).

**`如何配置推荐方法PM2略`**



-----

> **替代选项**

对于以上方案有多种替代选项,以下列出社区成员提供的方法.

 - [A systemd script (used by the Pi pre-install)](https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/nodered.service) by @NodeRED (linux)
 - [A systemd script](https://gist.github.com/Belphemur/3f6d3bf211b0e8a18d93) by Belphemur (linux)
 - [An init.d script](https://gist.github.com/bigmonkeyboy/9962293) by dceejay (linux)
 - [An init.d script](https://gist.github.com/Belphemur/cf91100f81f2b37b3e94) by Belphemur (linux)
 - [A Launchd script](https://gist.github.com/natcl/4688162920f368707613) by natcl (OS X)
 - [Running as a Windows service using NSSM](https://gist.github.com/dceejay/576b4847f0a17dc066db) by dceejay
 - [Running as Windows/OS X service](http://www.hardill.me.uk/wordpress/2014/05/30/running-node-red-as-a-windows-or-osx-service/) by Ben Hardill

**`[为了小白翻译. 成长为老司机]`**

-----

> update on stackedit.on @ win7




