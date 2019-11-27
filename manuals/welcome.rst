========
欢迎使用
========

FizeCache 是一个易于扩展的缓存类库。

FizeCache 允许您将缓存存放在任意的位置，无论是数据库、文件、Memcached 还是 Redis。

FizeCache 可以进行处理器选择，因此您可以根据系统环境自行选择 Cache 处理器。

FizeCache 有非常完善的参考文档，且其功能追求简洁明了，相信您会喜欢上这样的缓存类库。


数据库支持
==========

目前 FizeCache 已支持的处理器如下：

-  :doc:`Database </configs/database>` : 数据库，具体可以参考 `FizeDb <https://fizedb.readthedocs.io/zh_CN/latest/configs/index.html>`_ 。
-  :doc:`File </configs/file>` : 文件形式 。
-  :doc:`Memcache </configs/memcache>` : Memcache 形式 。
-  :doc:`Memcached </configs/memcached>` : Memcached 形式 。
-  :doc:`Redis </configs/redis>` : Redis 形式 。


入门三部曲
==========

1.配置参数
----------

根据 :doc:`参数配置 </configs/index>` 进行FizeCache 配置。

2.设置默认连接或者设置新连接
----------------------------

使用 `new Cache($handler, $config);`进行默认缓存设置，或者 `Cache::getInstance($handler, $config)` 方法获取新缓存实例

3.进行缓存操作
----------------

FizeCache 简化了缓存的操作，日常您使用的方法如下。

- `Cache::get()` : 获取缓存。
- `Cache::set()` : 设置缓存。
- `Cache::has()` : 判断指定缓存是否存在。
- `Cache::remove()` : 删除指定缓存。
- `Cache::clear()` : 清空缓存。


入门示例
========

.. code-block:: php

	use fize\cache\Cache;

	$config = [
		'host'    => '192.168.56.101',
		'port'    => 6379,
		'timeout' => 10,
		'expire'  => 0,
		'dbindex' => 15
	];
	new Cache('Redis', $config);

	Cache::set('cfz', 'hello world!');
	$cache1 = Cache::get('cfz');
	var_dump($cache1);  //hello world!

	Cache::remove('cfz2');
	$cache2 = Cache::get('cfz2');
	var_dump($cache2);  //null
		

