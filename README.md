# VOS
>The operating system based on Blockchain technology.<br>
基于区块链技术的操作系统


## VOS 是什么?
* `VOS`是一个基于区块链技术的`开源`操作系统，`VOS`安装完毕后，不需要依赖任何中心服务器就可以与其他`VOS`安全通讯(包括不依赖域名服务、数字证书颁发机构)。
* `VOS`像`Mac OS`、`Linux OS`、`Windows OS`、`iOS`、`Android`一样，操作系统对开发者提供API，开发者可以给操作系统开发应用程序。
* `VOS`可作为一个应用程序运行于`Mac OS`、`Linux OS`、`Windows OS`、`iOS`、`Android`操作系统之内，开发者开发的应用程序运行在`VOS`提供的容器之内。

## 为什么需要 VOS
* `VOS`可以取代域名服务，解决域名服务的如下缺点：
    * 单点故障。DNS采用层次化的树形结构，由树叶走向树根可以形成—个全域名（Fully Qualified Domain Name，FQDN），DNS服务器作为该FQDN对外的域名数据库和对内部提供递归域名查询的系统，因而其安全和稳定存在单点故障风险。
    * 无认证机制。DNS没有提供认证机制，查询者在收到应答时无法确认应答信息的真假，容易导致DNS欺骗。
    * DNS面临的网络威胁——内部攻击、序列号攻击、信息插入攻击、缓存（cache）中毒、信息泄漏。
    * 不能够按照Web服务器的处理能力分配负载。
    * 修改DNS记录后，不能立即生效。
* `VOS`可以取代数字证书颁发机构，解决如下缺点：
    * 数字证书由可信第三方机构颁发，会出现失信情况。
        >2017年3月份谷歌和火狐的调查人员发现赛门铁克打破了行业规则误签发127张SSL证书随着调查进一步开展发现误签发的证书数量达到惊人的3万多张。
* `VOS`实现支持非中心化web服务的操作系统。
    * 现在的网络体系结构过于依赖域名服务、数字证书颁发机构等中心化节点。
        >互联网精神：对等、开放、容错、共享、去中心、自组织、非商业、等等。
    * 避免中心化机构分析用户数据，进行精准的广告推荐。
    * web程序可以用分布式+集群的方式运行在所有的终端设备，节省服务器成本。
* 开发去中心化应用时，需要开发各种版本，兼容各种不同的操作系统。
    * `VOS`兼容各大主流操作系统，仅需开发`VOS`应用程序，即可运行在各种系统内。
## VOS 可行性说明
* 所有功能依赖于几项技术：
    * 共识机制
    * 分布式技术和集群技术
    * 点对点技术
    * 分布式账本
    * 去中心化的云存储
    * 搜索技术(非搜索引擎技术)
    * 路由技术
    * 非对称加密技术
* 每台安装`VOS`的设备，是客户端，同时也是所有其他`VOS`的服务器，与全网中的随机N台`VOS`建立TCP连接，并存储部分其他`VOS`地址信息，使用UDP交换数据。
* 安装`VOS`后，会自动生成私钥、公钥、地址(向比特币一样)，公钥、地址公开；每个公钥可以绑定一个名字(名字全网唯一，代替域名)，由于每个私钥和公钥是一一对应的、私钥不公开，所以不需要CA证书就可以进行加密通讯。
    >直接用对方公开的公钥进行加密，就可以保证，信息只有对方能够正确解密。(公钥加密的信息只有私钥能解密)<br/>
    用自己的私钥把自己的公钥加密，对方通过验证公钥密文，就可证明自己的身份。(公钥明文被密钥加密=公钥密文，公钥密文用公钥解密=公钥明文。)
## 系统架构
![image](https://raw.githubusercontent.com/freemanpeng/VOS/master/VOS.jpg)
* 应用部分
    * 桌面应用(Home)：使用前端技术html、css、js，提供的一个桌面应用程序。
    * 通讯应用(Phone)：使用框架层提供的API，编写的一个应用程序，可以通过文字、图片、语音、视频交流的一个社交应用。
    * 浏览器应用(Browser)：一个可以查看其它`VOS`发布内容的应用程序。
    * 应用商店(App Store)：用户可以使用该应用下载并安装其它开发者开发并发布的应用程序。
    * 发布应用(Publish)：用户使用该用户可以发多种类型式的内容，包括：网页、文件、应用程序等内容，发布后网页和文件可被其它`VOS`浏览器应用搜索并查看，应用程序可以其它`VOS`应用商店搜索，并安装使用。
    * ……：其它开发者开发的应用程序。
* 核心部分
    * 可视化模块：为用户提供可交互界面。
    * 客户端容器：所有需要使用其他`VOS`作为服务器的应用，将运行在该容器内。
    * 服务端容器：所有给其他`VOS`提供服务器功能的容器，将运行在该容器内。
    * 收件箱模块：一个核心基础服务，开启该服务后，可以在其他`VOS`离线时，帮其接收信息。
    * 核心模块：
        * 控制模块：`控制模块`控制`通信模块`和`存储模块`互相协作，每个`VOS`的`控制模块`也互相协作，从而保证全网`VOS`节点的通信稳定。
        * [通信模块(P2P Modules)](https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/P2PModules(zh-CN).md)：使用P2P技术，实现无中心服务器的点对点通信。
        * [存储模块(Storage Modules)](https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/StorageModules(zh-CN).md)：使用分布式账本技术和去中心化的云存储技术，为`VOS`系统提供存储功能。
        * 安全模块：保证传输数据、存储数据及系统的安全。
* 底层部分
    * 根据开源JVM开发一款适用于`VOS`的JVM，为`VOS`提供运行环境。

## 模块技术文档
* 核心模块
    * [通信模块(P2P Modules) https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/P2PModules(zh-CN).md](https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/P2PModules(zh-CN).md)
    * [存储模块(Storage Modules) https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/StorageModules(zh-CN).md](https://github.com/freemanpeng/VOS/blob/master/TechnicalDocument(zh-CN)/StorageModules(zh-CN).md)

## 系统信息
* 编程语言：Java
    > Java开发者数量众多，TIOBE排行第一</br>
    Java8的Nashorn提供了对js较好的支持(运行模块将使用Nashorn解释执行js)</br>
    JVM可运行在Mac、Linux、Windows平台，并可以对开源JVM进行改进，使其更适合运行`VOS`</br>
    Java有较多的开发框架(本人也较喜欢C/C++，C/C++也更适合开发系统，但学习、开发成本高于Java，不利于更多的开发者加入项目)</br>
* 系统运行的操作系统：Mac、Linux、Windows、iOS、Android
    > 使用Java开发，先开发Mac、Linux、Windows版本，并进行测试</br>
    由于iOS不支持Java，需要使用Object-C或Swift，需单独开发</br>
    Android主要使用于移动设备，虽然是Java开发，其DVM与JVM略有不同，需特殊处理</br>
    移动设备还需要考虑耗电量、不稳定的网络环境等问题，所以先对Mac、Linux、Windows版本进行开发。
* 界面交互：使用现在较为流程的前端技术VUE.js
    可视化模块，提供系统的界面交互。

## 开发计划
* 编写各个模块的技术文档
* 将文档翻译为英文
* 解决部分技术问题