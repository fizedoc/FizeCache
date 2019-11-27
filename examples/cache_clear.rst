==========
清空缓存
==========

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

	Cache::clear();  //cache 被清空
