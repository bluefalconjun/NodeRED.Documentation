
###[**创建你的第一个工作流程**](http://nodered.org/docs/getting-started/first-flow)

-----
当Node-RED已经开始运行时, 使用浏览器访问**`http://localhost:1880`**. 如果知道对应Node-RED进程执行机器的ip地址, 也可以在其他机器上通过**`http://{Node-RED-machine-ip-address}:1880`**来访问.


-----
> **详细步骤**

**1. 加入一个输出节点**

输出节点允许你向一个工作流中输入消息, 无论通过点击该节点或者是通过设置定时器进行输入触发均可完成.

从面板中拉取一个输出节点到工作区.

打开侧边栏(Ctrl-Space, 或者通过下拉菜单)来选择**`Info tab`**信息栏.

选择刚加入的节点来查看属性/描述的相关信息.


**2. 加入调试节点**

调试节点将所有获取的信息显示到Debug侧边栏中, 缺省情况下它只显示消息的荷载部分, 但是也可以配置显示所有消息对象内容.


**3. 连接以上两个节点**

将输出和调试节点连接起来, 将输出节点的输出端口连接至调试节点的输入端口.


**4. 部署**

在当前阶段, 节点仅仅存在于编辑器中, 需要将其部署至服务器上.

点击**`Deploy`**部署按钮. 即可完成.

当显示Debug侧边栏时, 点击输出按钮. 可以在侧边栏看到数字. 缺省情况下, 输出节点使用从**`创世日 :)`**到当前时间的毫秒数来作为它的消息负载. 可以通过其他方式来改变它.


**5. 增加函数节点**

函数节点允许使用JavaScript函数来处理消息.

将函数节点插入到输出节点/Debug节点之间, 并且切断原有两个节点间的连线. 

双击函数节点来到编辑窗口. 将以下代码复制到函数区域:

    // Create a Date object from the payload
    var date = new Date(msg.payload);
    // Change the payload to be a formatted Date string
    msg.payload = date.toString();
    // Return the message so it can be sent on
    return msg;

点击OK来关闭编辑器窗口, 然后点击部署按钮.

现在再点击输出按钮, 侧边栏中的信息将成为可读的时间戳信息.


-----
> **代码**

以上例子中创建的流程可以由下面的json文件来描述. 可以通过编辑器直接导入json文件来加入到工作区中:

    [{"id":"58ffae9d.a7005","type":"debug","name":"","active":true,"complete":false,"x":640,"y":200,"wires":[]},{"id":"17626462.e89d9c","type":"inject","name":"","topic":"","payload":"","repeat":"","once":false,"x":240,"y":200,"wires":[["2921667d.d6de9a"]]},{"id":"2921667d.d6de9a","type":"function","name":"Format timestamp","func":"// Create a Date object from the payload\nvar date = new Date(msg.payload);\n// Change the payload to be a formatted Date string\nmsg.payload = date.toString();\n// Return the message so it can be sent on\nreturn msg;","outputs":1,"x":440,"y":200,"wires":[["58ffae9d.a7005"]]}]


**`[为了小白翻译. 成长为老司机]`**

-----

> update on stackedit.on @ win7
