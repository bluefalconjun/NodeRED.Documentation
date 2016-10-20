
###[**添加节点**](http://nodered.org/docs/getting-started/adding-nodes)

-----
Node-RED安装时已经包含有一套核心的可用节点组合, 但同时也有越来越多的节点可以通过Node-RED项目, 以及广泛的社区中进行安装.

你可以通过npm库或者是Node-RED库来搜索可用的节点.


-----
> **使用编辑器**

从0.15版本开始, 你可以直接通过编辑器进行节点的安装操作. 从菜单栏(上右)中选择**`Manage Palette`**(管理控制面板). 然后在面板中选择**`install`**(安装). 目前可以在这里搜索新的可安装节点, 同时也可以对已安装节点进行允许/禁止的管理.


-----
> **安装npm包节点**

可以通过直接在Node-RED的用户存储数据目录下安装新节点:(缺省目录为, **`$HOME/.node-red`**):

    cd $HOME/.node-red
    npm install <npm-package-name>

或者通过sudo进行全局安装:

    sudo npm install -g <npm-package-name>

在Node-RED能够使用新节点之前需要对其进行重启.


-----

> **安装单独文件的节点**

同样也可以通过将节点的 .js / .html 文件拷贝至用户存储目录中的节点目录中来安装. 如果该节点存在有npm依赖, 对应依赖也必须被安装至对应目录中. 该方法只推荐给开发者使用.


**`[为了小白翻译. 成长为老司机]`**

-----

> update on stackedit.on @ win7
