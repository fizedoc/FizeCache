===============
缓存池接口
===============


+-------------+-----------------------------------+
|属性         |值                                 |
+=============+===================================+
|命名空间     |fize\\cache                        |
+-------------+-----------------------------------+
|类名         |PoolInterface                      |
+-------------+-----------------------------------+
|实现接口     |Psr\\Cache\\CacheItemPoolInterface |
+-------------+-----------------------------------+


:方法:


+------------------+-----------------------------------------------------+
|方法名            |说明                                                 |
+==================+=====================================================+
|`__construct()`_  |构造                                                 |
+------------------+-----------------------------------------------------+
|`saveItems()`_    |设置多个缓存项                                       |
+------------------+-----------------------------------------------------+
|`getItem()`_      |Returns a Cache Item representing the specified key. |
+------------------+-----------------------------------------------------+
|`getItems()`_     |Returns a traversable set of cache items.            |
+------------------+-----------------------------------------------------+
|`hasItem()`_      |Confirms if the cache contains specified cache item. |
+------------------+-----------------------------------------------------+
|`clear()`_        |Deletes all items in the pool.                       |
+------------------+-----------------------------------------------------+
|`deleteItem()`_   |Removes the item from the pool.                      |
+------------------+-----------------------------------------------------+
|`deleteItems()`_  |Removes multiple items from the pool.                |
+------------------+-----------------------------------------------------+
|`save()`_         |Persists a cache item immediately.                   |
+------------------+-----------------------------------------------------+
|`saveDeferred()`_ |Sets a cache item to be persisted later.             |
+------------------+-----------------------------------------------------+
|`commit()`_       |Persists any deferred cache items.                   |
+------------------+-----------------------------------------------------+


方法
======
__construct()
-------------
构造

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
  
  


saveItems()
-----------
设置多个缓存项

.. code-block:: php

  abstract public function saveItems (
      \CacheItemInterface[] $items
  ) : bool


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |items  |       |
  +-------+-------+
  
  


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


getItems()
----------
Returns a traversable set of cache items.

.. code-block:: php

  abstract public function getItems (
      string[] $keys = []
  ) : array|\Traversable


:参数:
  +-------+-----------------------------------------------+
  |名称   |说明                                           |
  +=======+===============================================+
  |keys   |An indexed array of keys of items to retrieve. |
  +-------+-----------------------------------------------+
  
  

:返回值:
  A traversable collection of Cache Items keyed by the cache keys of
  each item. A Cache item will be returned for each key, even if that
  key is not found. However, if no keys are specified then an empty
  traversable MUST be returned instead.


hasItem()
---------
Confirms if the cache contains specified cache item.

.. code-block:: php

  abstract public function hasItem (
      string $key
  ) : bool


:参数:
  +-------+--------------------------------------+
  |名称   |说明                                  |
  +=======+======================================+
  |key    |The key for which to check existence. |
  +-------+--------------------------------------+
  
  

:返回值:
  True if item exists in the cache, false otherwise.


::

    Note: This method MAY avoid retrieving the cached value for performance reasons.
    This could result in a race condition with CacheItemInterface::get(). To avoid
    such situation use CacheItemInterface::isHit() instead.


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


deleteItems()
-------------
Removes multiple items from the pool.

.. code-block:: php

  abstract public function deleteItems (
      string[] $keys
  ) : bool


:参数:
  +-------+-------------------------------------------------------+
  |名称   |说明                                                   |
  +=======+=======================================================+
  |keys   |An array of keys that should be removed from the pool. |
  +-------+-------------------------------------------------------+
  
  

:返回值:
  True if the items were successfully removed. False if there was an error.


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


saveDeferred()
--------------
Sets a cache item to be persisted later.

.. code-block:: php

  abstract public function saveDeferred (
      \Psr\Cache\CacheItemInterface $item
  ) : bool


:参数:
  +-------+------------------------+
  |名称   |说明                    |
  +=======+========================+
  |item   |The cache item to save. |
  +-------+------------------------+
  
  

:返回值:
  False if the item could not be queued or if a commit was attempted and failed. True otherwise.


commit()
--------
Persists any deferred cache items.

.. code-block:: php

  abstract public function commit () : bool


:返回值:
  True if all not-yet-saved items were successfully saved or there were none. False otherwise.


