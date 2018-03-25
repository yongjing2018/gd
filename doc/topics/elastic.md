# ES (elastic-search)
## ES原理
> ES主要通过搜索luce进行按照列进行组织数据，为了快速查询。目前的ES可以解决文档数据和结构化数据。 结构化数据已经超出了lucs的范畴，也不再具有搜索相关的意义。
但是结构化数据的列式存储，却是业务应用中最为常用的方式。

## ES读写流程
1. ES服务启动
> ES服务类型主要分为 masternode, datanode, coordnode三种类型。
2. 创建／删除／修改Index
> client会通过coordnode访问masternode，在masternode进行index的管理，添加的时候会根据replica的数量以及datanode进行资源的分配。
3. 添加数据
> client会访问coordnode，coodnode会查看对应index-type对应的数据放在datanode的位置，包括routing的定义。
数据在datanode中的处理流程：
1. 接收数据写入到WAL日志中，并更加replica数同步到时其他的datanode，等一切ok；
  存储采用：index， type，然后是 property等进行文件等读写
2. 返回结果

## ES收益
1. ES的进行管理数据非常消耗资源，数据replica在5，另外在稍微有点规模应用中，都有单独的metanode和datanode以及coordnode节点。
2. 数据在存储的时候，非常慢，有async和sync两种，一般都采用同步模式；
3. 最大的优势可以解决聚合计算的问题；
4. 可以进行水平的扩展；

