========
初始化
========

.. code-block:: php

	use fize\cache\Cache;

	//使用 Cache 静态方法前必须先 Cache 初始化

	$config = [
		'host'    => '192.168.56.101',
		'port'    => 6379,
		'timeout' => 10,
		'expire'  => 0,
		'dbindex' => 15
	];
	new Cache('Redis', $config);

	//可以开始使用 Cache 静态方法