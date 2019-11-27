========
判断缓存
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

	Cache::remove('cfz1');
	$has1 = Cache::has('cfz1');
	var_dump($has1);  //false

	Cache::set('cfz1', 'hello world2!');
	$has2 = Cache::has('cfz1');
	var_dump($has2);  //true
