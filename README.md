# VOS
>The operating system based on Blockchain technology.<br>
基于区块链技术的操作系统


## VOS 是什么?
* `VOS` 是一个基于区块链技术的`开源`操作系统，在网络中 `VOS` 系统不依赖任何中心服务器就可以与其他 `VOS` 安全通讯(包括不依赖域名服务、数字证书颁发机构)。
* `VOS` 像 `Mac OS`、`Linux OS`、`Windows OS` 一样，开发者可以给操作系统开发应用程序，操作系统对开发者提供 `分布式存储API` ，`点对点网络传输API`。`VOS` 的 `控制模块` 会对运行程序占用的资源进行控制，以保证全网系统稳定流畅。
* `VOS` 运行于其他操作系统之上，使用其他操作系统已有的底层API。
* `VOS` 内置四个基础服务程序，`通讯服务`、`发布服务`、`搜索服务`、`存储服务`。
    * `通信服务` 可以与任意一台VOS进行点对点全双工通讯。
    * `发布服务` 可以发布内容(发布类型包括：文本、图片、音频、视频、可执行程序等)，发布后可以被其它 `VOS` 搜索到，发布后数据使用 `存储服务` 存储。
    * `搜索服务` 可以搜索到网络中的任意节点和节点发布的数据。
    * `存储服务` 可将数据存储到本地 或 加密并分布存储在其它VOS节点中。
## 为什么需要 VOS
* `VOS` 可以取代域名服务，解决域名服务的如下缺点：
    * 单点故障。DNS采用层次化的树形结构，由树叶走向树根可以形成—个全域名（Fully Qualified Domain Name，FQDN），DNS服务器作为该FQDN对外的域名数据库和对内部提供递归域名查询的系统，因而其安全和稳定存在单点故障风险。
    * 无认证机制。DNS没有提供认证机制，查询者在收到应答时无法确认应答信息的真假，容易导致DNS欺骗。
    * DNS面临的网络威胁——内部攻击、序列号攻击、信息插入攻击、缓存（cache）中毒、信息泄漏。
    * 不能够按照Web服务器的处理能力分配负载。
    * 修改DNS记录后，不能立即生效。
* `VOS` 可以取代数字证书颁发机构，解决如下缺点：
    * 数字证书由可信第三方机构颁发，会出现失信情况。
        >2017年3月份谷歌和火狐的调查人员发现赛门铁克打破了行业规则误签发127张SSL证书随着调查进一步开展发现误签发的证书数量达到惊人的3万多张。
* `VOS` 实现支持非中心化web服务的操作系统。
    * 现在的网络体系结构过于依赖域名服务、数字证书颁发机构等中心化节点。
        >互联网精神：对等、开放、容错、共享、去中心、自组织、非商业、等等。
    * 避免中心化机构分析用户数据，进行精准的广告推荐。
    * web程序可以用分布式+集群的方式运行在所有的终端设备，节省服务器成本。
## VOS 可行性说明
* 所有功能依赖于几项技术：
    * 共识机制
    * 分布式技术和集群技术
    * 点对点技术
    * 分布式账本
    * 搜索技术(非搜索引擎技术)
    * 路由技术
    * 非对称加密技术
* `VOS` 系统由四大基础服务构成，并对 `VOS应用开发者` 提供API。四大服务包含所有VOS的功能。
* 每台安装 `VOS` 的设备，是客户端，同时也是所有其他 `VOS` 的服务器，与全网中的随机N台 `VOS` 建立TCP连接，并存储部分其他 `VOS` 地址信息，使用UDP交换数据。
* 安装 `VOS` 后，会自动生成私钥、公钥、地址(向比特币一样)，公钥、地址公开；每个地址可以绑定一个名字(名字全网唯一，代替域名)，由于每个私钥和公钥是一一对应的、私钥不公开，所以不需要CA证书就可以进行加密通讯。
    >直接用对方公开的公钥进行加密，就可以保证，信息只有对方能够正确解密。(公钥加密的信息只有私钥能解密)<br/>
    用自己的私钥把自己的公钥加密，对方通过验证公钥密文，就可证明自己的身份。(公钥明文被密钥加密=公钥密文，公钥密文用公钥解密=公钥明文。)
* `通信服务` ：因为每个 `VOS` 都与其他几台 `VOS` 保持长连接，使用路由选择算法，与要通信的 `VOS` 直接建立长连接，并完成通信。
* `发布服务` ：使用存储服务技术，将数据存储；使用分布式账本技术，在账本中加入索引。
* `搜索服务` ：使用搜索技术对分布式账本(索引)进行搜素，并获取数据。
* `存储服务` ：将数据存储到本地或使用分布式技术技术和集群技术将数据存储在其它 `VOS` 系统中，系统会根据(`控制模块`)来限制用户对全网资源的使用情况。
* `控制模块` ：在一个阈值内，提供资源越多，可在全网使用的资源就越多；超过阈值后，提供资源越多，就越容易被搜索到，阈值由系统动态计算得出，全网通过共识机制来统一阈值。
* 界面开发，使用宿主机的可视化类库。
## 系统架构
![image](https://raw.githubusercontent.com/freemanpeng/VOS/master/VOS.jpg)
* 应用层
    * 通讯应用(Phone)：使用框架层提供的API，编写的一个应用程序，可以通过文字、图片、语音、视频交流的一个社交应用。
    * 浏览器应用(Browser)：一个可以查看其它 `VOS` 发布内容的应用程序。
    * 应用商店(App Store)：用户可以使用该应用下载其它开发者开发出来的应用程序。
    * ……
* 框架层
    * 通信服务(Communication)：在核心模块的基础上封装API，提供给应用层使用。
    * 发布服务(Publish)：在核心模块的基础上封装API，提供给应用层使用。
    * 搜索服务(Search)：在核心模块的基础上封装API，提供给应用层使用。
    * 存储服务(Storage)：在核心模块的基础上封装API，提供给应用层使用。
* 核心模块
    * [通信模块(P2P Modules)](https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/P2PModules(zh-CN).md)：实现P2P通信。
    * 控制模块(Control Modules)：维持整个 `VOS` 节点网络的稳定。
    * 存储模块(Storage Modules)：本地存储、去中心化的云存储、区块链存储。
    * 运行模块(Run Modules)：运行后台程序，让每个 `VOS` 可以作为其他 `VOS` 的后台服务器。
* Java虚拟机
    * 根据开源JDK开发一款适用于 `VOS` 的JDK
## 系统信息
* 编程语言：Java
    > Java开发者数量众多，TIOBE排行第一</br>
    Java8的Nashorn提供了对js较好的支持(运行模块将使用Nashorn解释执行js)</br>
    JVM可运行在Mac、Linux、Windows平台，并可以对开源JVM进行改进，使其更适合运行 `VOS`</br>
    Java有较多的开发框架(本人也较喜欢C/C++，C/C++也更适合开发系统，但学习、开发成本高于Java，不利于更多的开发者加入项目)</br>
* 系统运行的操作系统：Mac、Linux、Windows、iOS、Android
    > 使用Java开发，先开发Mac、Linux、Windows版本，并进行测试</br>
    由于iOS不支持Java，需要使用Object-C或Swift，需单独开发</br>
    Android主要使用于移动设备，虽然是Java开发，其DVM与JVM略有不同，需特殊处理</br>
    移动设备还需要考虑耗电量、不稳定的网络环境等问题，所以先对Mac、Linux、Windows版本进行开发。
* 界面交互：直接使用宿主机系统的可视化API或Java Swing、Java FX
    >目前 `VOS` 系统并未设计可视化API，系统开发时先使用Swing，或宿主机的API。</br>
    ### 关于界面交互，谁有更好的建议？
## 开发计划
* 编写各个模块的技术文档
* 将文档翻译为英文
* 开发 `通信模块` (P2P Modules)