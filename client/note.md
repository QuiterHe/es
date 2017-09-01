## ES相关概念

### Cluster(集群)
> 集群由多个节点组成，它们具有相同的cluster.name

### Node(节点)
>  一个节点就是一个es实例
> 集群中的一个节点会被选举为主节点（master）

### Shard(分片)
> 最小级别的的“工作单元”
> 文档存储在分片中
> 是一个Lucene实例，本身是一个完整的搜索引擎
> primary shard(主要分片)－写（固定）
> replica shard(复制分片)－读、容灾（灵活调整）

### Index(索引)
> 用于存储关联数据
> 指向一个或多个分片的“逻辑命名空间”

### 分布式

## 监控

### 集群健康
GET /_cluster/health
三种状态
> green
> yellow
> red

## 面向文档
文档元数据
> _index 文档存储位置（数据库）
> _type 文档代表的对象的类
> _id 文档的唯一标识


## 路由
文档路由到分片
> shard = hash(routing) % number_of_primary_shards
> routing一般取 _id 元数据
> 主分片的数量时固定的


## 分页
深度分页有着较大的性能消耗
