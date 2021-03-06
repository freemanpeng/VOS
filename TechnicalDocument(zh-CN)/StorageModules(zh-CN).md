## 存储模块技术文档 (Storage Modules Technical Document)

### 存储模块简介
* 该模块完成`VOS`存储数据的任务。
* 存储类型分为三种：
    * 1.本地存储。负责为`VOS`提供最基础的数据存储功能，存储方式包括：文件系统，NoSQL，关系型数据存储。
    * 2.区块链存储。利用公式算法，把所有信息使用区块链的结构存储，每台设备都有数据的一份拷贝。
    * 3.去中心化云存储。将数据冗余存储在其他N台设备上，需要时，可将数据还原至本地。

### 本地存储技术概述
* 该技术已经非常成熟，可采用现有的技术即可。
    * 文件系统：直接采用宿主机的文件系统和内置mongodb。
    * NoSQL：在`VOS`系统内置mongodb。
    * 关系型数据存储：在`VOS`系统内置一个SQLite数据库。

### 区块链存储技术概述
* 该存储方式，存储一些不可被篡改的、全网节点需要保持一致的数据。
* 比特币的存储技术已经历长达9年的验证，所以采用该技术存储。
    简单的来讲，就是所有节点遵守同一个规则(这个规则叫做共识算法)，就能保证所有节点存储的一致，并很难篡改。比特币采用了POW算法,
    在比特币系统中因为获得记账权就可以获取到比特币，全网部分节点为了争夺记账权，需要消耗大量的算力来计算新生成区块的hash值，计算出hash值后将生成一个区块，通知全网节点对其结果进行验证，
    每个节点验证成功后将该区块存储，每个区块内包含了近10分钟的所有交易记录 和 拿到记账权自己给自己添加的一定数目比特币。
    如果需要将区块内的某一条数据修改，就必须重新计算该区块(及该区块之后的所有区块)的hash值，并获得51%的节点认可，才能达到修改数据的目的。
    因为计算量很大，所以很难篡改数据。时间越早的区块，数据就越难被篡改。
* 除了POW以外，还有POS，DPOS，PBFT等，`VOS`对其都分别实现。

### 分布式云存储技术概述
* 将数据切分N份，每份冗余存储在其他节点。本地保存所有数据存储地址的索引。
* 参考:http://www.sohu.com/a/120373108_502610

### 模块功能
* 提供以下api：
    * 本地api：文件系统api、NoSQL相关api、关系型数据存储相关api
    * 区块链存储api
    * 去中心化云存储：文件系统api、NoSQL相关api、关系型数据存储相关api