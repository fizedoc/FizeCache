==========
创建新实例
==========

.. code-block:: php

	use fize\cache\Cache;

	$cache = Cache::getInstance('File');

	// 使用 cache 的实例方法进行操作

	$cache->set('key', 'value');
	$val = $cache->get('key');
	var_dump($val);
