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

## 数据类型
在es中，数据大致分为两种类型：
> 1. 确切值
> 2. 全文文本（非结构化数据）

## 倒排索引
对于全文文本，es在对文本分析后建立了一个倒排索引

## 分析过程
> 1. 字符过滤器 （去除HTML标签，将 &  转化为 and）
> 2. 分词器 （形成token或terms）
> 3. 标记过滤 （过滤token）
以上三种处理器可以自定义使用

## 分析器
内建的分析器

## 测试分析器
GET /_analyze?analyzer=standard&text=Text to analyze

## 字段类型
核心简单字段类型
String | string
Whole number | byte, short, integer, long
Floating point | float,double
Boolean | boolean

复合核心字段类型
Date | date