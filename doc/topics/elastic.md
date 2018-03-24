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



## ES收益
