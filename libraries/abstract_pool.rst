=========
缓存池
=========


+-------------+---------------------------------------------------------------+
|属性         |值                                                             |
+=============+===============================================================+
|命名空间     |fize\\cache                                                    |
+-------------+---------------------------------------------------------------+
|类名         |AbstractPool                                                   |
+-------------+---------------------------------------------------------------+
|修饰符       |abstract                                                       |
+-------------+---------------------------------------------------------------+
|实现接口     |fize\\cache\\PoolInterface, Psr\\Cache\\CacheItemPoolInterface |
+-------------+---------------------------------------------------------------+


:方法:


+------------------+----------------------------------------------------------------+
|方法名            |说明                                                            |
+==================+================================================================+
|`__construct()`_  |构造                                                            |
+------------------+----------------------------------------------------------------+
|`hasItem()`_      |检查是否有对应的缓存项                                          |
+------------------+----------------------------------------------------------------+
|`getItems()`_     |返回一个可供遍历的缓存项集合                                    |
+------------------+----------------------------------------------------------------+
|`deleteItems()`_  |移除多个缓存项                                                  |
+------------------+----------------------------------------------------------------+
|`saveItems()`_    |设置多个缓存项                                                  |
+------------------+----------------------------------------------------------------+
|`saveDeferred()`_ |稍后为缓存项做数据持久化                                        |
+------------------+----------------------------------------------------------------+
|`commit()`_       |提交所有的正在队列里等待的请求到数据持久层                      |
+------------------+----------------------------------------------------------------+
|`getItem()`_      |Returns a Cache Item representing the specified key.            |
+------------------+----------------------------------------------------------------+
|`clear()`_        |Deletes all items in the pool.                                  |
+------------------+----------------------------------------------------------------+
|`deleteItem()`_   |Removes the item from the pool.                                 |
+------------------+----------------------------------------------------------------+
|`save()`_         |Persists a cache item immediately.                              |
+------------------+----------------------------------------------------------------+


方法
======
__construct()
-------------
构造

.. code-block:: php

  public function __construct (
      array $config = []
  )


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |config |配置   |
  +-------+-------+
  
  


hasItem()
---------
检查是否有对应的缓存项

.. code-block:: php

  public function hasItem (
      string $key
  ) : bool


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |key    |键名   |
  +-------+-------+
  
  


getItems()
----------
返回一个可供遍历的缓存项集合

.. code-block:: php

  public function getItems (
      array $keys = []
  ) : \CacheItemInterface[]


:参数:
  +-------+----------------------+
  |名称   |说明                  |
  +=======+======================+
  |keys   |键名组成的数组        |
  +-------+----------------------+
  
  


deleteItems()
-------------
移除多个缓存项

.. code-block:: php

  public function deleteItems (
      array $keys
  ) : bool


:参数:
  +-------+----------------------+
  |名称   |说明                  |
  +=======+======================+
  |keys   |键名组成的数组        |
  +-------+----------------------+
  
  


saveItems()
-----------
设置多个缓存项

.. code-block:: php

  public function saveItems (
      \CacheItemInterface[] $items
  ) : bool


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |items  |       |
  +-------+-------+
  
  


saveDeferred()
--------------
稍后为缓存项做数据持久化

.. code-block:: php

  public function saveDeferred (
      \Psr\Cache\CacheItemInterface $item
  ) : bool


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |item   |       |
  +-------+-------+
  
  


commit()
--------
提交所有的正在队列里等待的请求到数据持久层

.. code-block:: php

  public function commit () : bool



getItem()
---------
Returns a Cache Item representing the specified key.

.. code-block:: php

  abstract public function getItem (
      string $key
  ) : \Psr\Cache\CacheItemInterface


:参数:
  +-------+----------------------------------------------------------+
  |名称   |说明                                                      |
  +=======+==========================================================+
  |key    |The key for which to return the corresponding Cache Item. |
  +-------+----------------------------------------------------------+
  
  

:返回值:
  The corresponding Cache Item.


::

    This method must always return a CacheItemInterface object, even in case of
    a cache miss. It MUST NOT return null.


clear()
-------
Deletes all items in the pool.

.. code-block:: php

  abstract public function clear () : bool


:返回值:
  True if the pool was successfully cleared. False if there was an error.


deleteItem()
------------
Removes the item from the pool.

.. code-block:: php

  abstract public function deleteItem (
      string $key
  ) : bool


:参数:
  +-------+-------------------+
  |名称   |说明               |
  +=======+===================+
  |key    |The key to delete. |
  +-------+-------------------+
  
  

:返回值:
  True if the item was successfully removed. False if there was an error.


save()
------
Persists a cache item immediately.

.. code-block:: php

  abstract public function save (
      \Psr\Cache\CacheItemInterface $item
  ) : bool


:参数:
  +-------+------------------------+
  |名称   |说明                    |
  +=======+========================+
  |item   |The cache item to save. |
  +-------+------------------------+
  
  

:返回值:
  True if the item was successfully persisted. False if there was an error.


