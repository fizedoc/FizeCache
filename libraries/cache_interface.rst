==================
简易缓存接口
==================


+-------------+---------------------------------+
|属性         |值                               |
+=============+=================================+
|命名空间     |fize\\cache                      |
+-------------+---------------------------------+
|类名         |CacheInterface                   |
+-------------+---------------------------------+
|实现接口     |Psr\\SimpleCache\\CacheInterface |
+-------------+---------------------------------+


:方法:


+--------------------+-----------------------------------------------------------------------------------------------+
|方法名              |说明                                                                                           |
+====================+===============================================================================================+
|`__construct()`_    |构造函数                                                                                       |
+--------------------+-----------------------------------------------------------------------------------------------+
|`get()`_            |Fetches a value from the cache.                                                                |
+--------------------+-----------------------------------------------------------------------------------------------+
|`set()`_            |Persists data in the cache, uniquely referenced by a key with an optional expiration TTL time. |
+--------------------+-----------------------------------------------------------------------------------------------+
|`delete()`_         |Delete an item from the cache by its unique key.                                               |
+--------------------+-----------------------------------------------------------------------------------------------+
|`clear()`_          |Wipes clean the entire cache's keys.                                                           |
+--------------------+-----------------------------------------------------------------------------------------------+
|`getMultiple()`_    |Obtains multiple cache items by their unique keys.                                             |
+--------------------+-----------------------------------------------------------------------------------------------+
|`setMultiple()`_    |Persists a set of key => value pairs in the cache, with an optional TTL.                       |
+--------------------+-----------------------------------------------------------------------------------------------+
|`deleteMultiple()`_ |Deletes multiple cache items in a single operation.                                            |
+--------------------+-----------------------------------------------------------------------------------------------+
|`has()`_            |Determines whether an item is present in the cache.                                            |
+--------------------+-----------------------------------------------------------------------------------------------+


方法
======
__construct()
-------------
构造函数

.. code-block:: php

  abstract public function __construct (
      array $config = []
  )


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |config |配置   |
  +-------+-------+
  
  


get()
-----
Fetches a value from the cache.

.. code-block:: php

  abstract public function get (
      string $key,
      mixed $default = null
  ) : mixed


:参数:
  +--------+---------------------------------------------------+
  |名称    |说明                                               |
  +========+===================================================+
  |key     |The unique key of this item in the cache.          |
  +--------+---------------------------------------------------+
  |default |Default value to return if the key does not exist. |
  +--------+---------------------------------------------------+
  
  

:返回值:
  The value of the item from the cache, or $default in case of cache miss.


set()
-----
Persists data in the cache, uniquely referenced by a key with an optional expiration TTL time.

.. code-block:: php

  abstract public function set (
      string $key,
      mixed $value,
      null|int|\DateInterval $ttl = null
  ) : bool


:参数:
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |名称   |说明                                                                                                                                                                       |
  +=======+===========================================================================================================================================================================+
  |key    |The key of the item to store.                                                                                                                                              |
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |value  |The value of the item to store, must be serializable.                                                                                                                      |
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |ttl    |Optional. The TTL value of this item. If no value is sent and
  the driver supports TTL then the library may set a default value
  for it or let the driver take care of that. |
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  True on success and false on failure.


delete()
--------
Delete an item from the cache by its unique key.

.. code-block:: php

  abstract public function delete (
      string $key
  ) : bool


:参数:
  +-------+--------------------------------------------+
  |名称   |说明                                        |
  +=======+============================================+
  |key    |The unique cache key of the item to delete. |
  +-------+--------------------------------------------+
  
  

:返回值:
  True if the item was successfully removed. False if there was an error.


clear()
-------
Wipes clean the entire cache's keys.

.. code-block:: php

  abstract public function clear () : bool


:返回值:
  True on success and false on failure.


getMultiple()
-------------
Obtains multiple cache items by their unique keys.

.. code-block:: php

  abstract public function getMultiple (
      iterable $keys,
      mixed $default = null
  ) : iterable


:参数:
  +--------+--------------------------------------------------------+
  |名称    |说明                                                    |
  +========+========================================================+
  |keys    |A list of keys that can obtained in a single operation. |
  +--------+--------------------------------------------------------+
  |default |Default value to return for keys that do not exist.     |
  +--------+--------------------------------------------------------+
  
  

:返回值:
  A list of key => value pairs. Cache keys that do not exist or are stale will have $default as value.


setMultiple()
-------------
Persists a set of key => value pairs in the cache, with an optional TTL.

.. code-block:: php

  abstract public function setMultiple (
      iterable $values,
      null|int|\DateInterval $ttl = null
  ) : bool


:参数:
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |名称   |说明                                                                                                                                                                       |
  +=======+===========================================================================================================================================================================+
  |values |A list of key => value pairs for a multiple-set operation.                                                                                                                 |
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |ttl    |Optional. The TTL value of this item. If no value is sent and
  the driver supports TTL then the library may set a default value
  for it or let the driver take care of that. |
  +-------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  True on success and false on failure.


deleteMultiple()
----------------
Deletes multiple cache items in a single operation.

.. code-block:: php

  abstract public function deleteMultiple (
      iterable $keys
  ) : bool


:参数:
  +-------+-------------------------------------------+
  |名称   |说明                                       |
  +=======+===========================================+
  |keys   |A list of string-based keys to be deleted. |
  +-------+-------------------------------------------+
  
  

:返回值:
  True if the items were successfully removed. False if there was an error.


has()
-----
Determines whether an item is present in the cache.

.. code-block:: php

  abstract public function has (
      string $key
  ) : bool


:参数:
  +-------+--------------------+
  |名称   |说明                |
  +=======+====================+
  |key    |The cache item key. |
  +-------+--------------------+
  
  


::

    NOTE: It is recommended that has() is only to be used for cache warming type purposes
    and not to be used within your live applications operations for get/set, as this method
    is subject to a race condition where your has() will return true and immediately after,
    another script can remove it making the state of your app out of date.


