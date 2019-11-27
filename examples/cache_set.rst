========
设置缓存
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

	Cache::set('cfz', '我想在里面填什么都可以', 100);
	$cache1 = Cache::get('cfz');
	var_dump($cache1);

	Cache::set('cfz2', '我想在里面填什么都可以2');
	$cache2 = Cache::get('cfz2');
	var_dump($cache2);
