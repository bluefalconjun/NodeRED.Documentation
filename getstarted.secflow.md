
###[**创建进阶流程**](http://nodered.org/docs/getting-started/second-flow)

-----
该例子将要略微复杂, 它将从外部源获取数据并且在本地对其进行处理.

 - 它将访问外部web站点.
 - 获取网站信息.
 - 读取并转换信息为可用的格式.
 - 将其输出为两种格式, 一种是JSON对象来作为后期使用, 另一种是boolean来进行控制开关.


-----
> **详细步骤**

**1. 加入一个输出节点**

在上[一个例子](http://nodered.org/docs/getting-started/first-flow)中, 输出节点在被点击时将驱动工作流程进行. 当前例子中, 该节点被配置为以定时器方式来驱动整个流程.

从面板中选择输出节点到工作区.

双击节点到编辑窗口. 设置重复周期为每天中的每5分钟.

点击OK来关闭窗口.


**2. 加入HeepRequest节点**

**`HttpRequest`**节点可以在触发时用来获取web页面内容.

加入节点后, 编辑设置它的URL属性为:

    http://realtimeweb-prod.nationalgrid.com/SystemData.aspx

可以为节点设置别名.


**3. 增加函数节点**

以以下的代码来增加一个函数节点:

    // does a simple text extract parse of the http output to provide an
    // object containing the uk power demand, frequency and time
    
    if (~msg.payload.indexOf('<span')) {
        var dem = msg.payload.split('Demand:')[1].split("MW")[0];
        var fre = msg.payload.split('Frequency:')[1].split("Hz")[0];
    
        msg.payload = {};
        msg.payload.demand = parseInt(dem.split(">")[1].split("<")[0]);
        msg.payload.frequency = parseFloat(fre.split(">")[1].split("<")[0]);
    
        msg2 = {};
        msg2.payload = (msg.payload.frequency >= 50) ? true : false;
    
        return [msg,msg2];
    }
    return null;

设置该函数节点的输出端口数为**2**.


**4. 增加Debug节点**

增加两个Debug节点.


**5. 连接所有节点**

 - 将输出节点的输出连接至HttpRequest节点的输入.
 - 将HttpRequest节点的输出连接至函数节点的输入.
 - 将函数节点的2个输出分别连接至2个Debug节点的输入.


**6. 部署**

到目前为止, 节点只存在于编辑器中.

点击部署按钮.

在Debug侧边栏中, 点击输出按钮, 可以看到类似以下的条目:

    (Object) { "demand": 34819, "frequency": 50.04 }

另一栏条目类似:

    (boolean) true


**7. 总结**

你已经创建了一个工作流程, 它访问了互联网 - 获取了UK的总用电量 - 转化为JavaScript对象, 以MW(**`million wate? 百万瓦?`**)为需求, 以赫兹为频率作为单位.

以上的对象从函数节点的第一个输出中输出.

频率是总体参考的重要指示 - 当频率低于50HZ时则有可能全局电网产生了过载, 这将从函数节点的第二个输出中输出; 如果荷载时true. 说明电网仍然**`在运行? 有容量?`** 


-----
> **代码**

以上例子中创建的流程可以由下面的json文件来描述. 可以通过编辑器直接导入json文件来加入到工作区中:

    [{"id":"11b032a3.ee4fcd","type":"inject","name":"Tick","topic":"","payload":"","repeat":"","crontab":"*/5 * * * *","once":false,"x":161,"y":828,"z":"6480e14.f9b7f2","wires":[["a2b3542e.5d4ca8"]]},{"id":"a2b3542e.5d4ca8","type":"http request","name":"UK Power","method":"GET","url":"http://realtimeweb-prod.nationalgrid.com/SystemData.aspx","x":301,"y":828,"z":"6480e14.f9b7f2","wires":[["2631e2da.d9ce1e"]]},{"id":"2631e2da.d9ce1e","type":"function","name":"UK Power Demand","func":"// does a simple text extract parse of the http output to provide an\n// object containing the uk power demand, frequency and time\n\nif (~msg.payload.indexOf('<span')) {\n    var dem = msg.payload.split('Demand:')[1].split(\"MW\")[0];\n    var fre = msg.payload.split('Frequency:')[1].split(\"Hz\")[0];\n\n    msg.payload = {};\n    msg.payload.demand = parseInt(dem.split(\">\")[1].split(\"<\")[0]);\n    msg.payload.frequency = parseFloat(fre.split(\">\")[1].split(\"<\")[0]);\n    \n    msg2 = {};\n    msg2.payload = (msg.payload.frequency >= 50) ? true : false;\n\n    return [msg,msg2];\n}\n\nreturn null;","outputs":"2","valid":true,"x":478,"y":828,"z":"6480e14.f9b7f2","wires":[["8e56f4d3.71a908"],["cd84371b.327bc8"]]},{"id":"8e56f4d3.71a908","type":"debug","name":"","active":true,"complete":false,"x":678,"y":798,"z":"6480e14.f9b7f2","wires":[]},{"id":"cd84371b.327bc8","type":"debug","name":"","active":true,"complete":false,"x":679,"y":869,"z":"6480e14.f9b7f2","wires":[]}]


**`[为了小白翻译. 成长为老司机]`**

-----

> update on stackedit.on @ win7
