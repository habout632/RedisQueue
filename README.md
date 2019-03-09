
redis高并发队列
##### [介绍文档]

* 支持版本: python 3.6


### 下载安装

* 下载源码:

```shell
git clone https://github.com/abo123456789/RedisQueue.git
```

* 安装依赖:

```shell
pip install -r requirements.txt
```

* 配置config.py:

```shell
# config.py 为数据库配置文件

# 配置Redis
redis_host = '127.0.0.1'
redis_password = ''
redis_port = 6379
redis_db = 0


# redis没有设置密码,默认配置''

```

* 启动:

```shell
# 如果你的依赖已经安全完成并且具备运行条件,可以直接运行RedisQueue.py
>>>python RedisQueue.py

# 如果运行成功,会自动启动添加任务和消费任务demo

```

### 运行DEMO说明


```python
    quenen_name = 'test'

    #批量写入队列
    result = [str(i) for i in range(1, 5008)]
    redis_pub = RedisPublish(quenen_name)
    redis_pub.publish_redispy_list(result)

    #单条记录入队列
    for zz in result:
        redis_pub.publish_redispy(zz)

    def _print_(msg):
        print(msg)

    #多线程消费队列
    redis_customer = RedisCustomer(quenen_name, consuming_function=_print_,threads_num=100)
    print(redis_customer.threads_num)
    for i in range(1,100):
        redis_customer._start_consuming_message()


```


### 使用场景说明


```shell
1 . 高并发分布式爬虫

2 . 分布式数据清洗

3 . 其它使用场景扩展中

```
