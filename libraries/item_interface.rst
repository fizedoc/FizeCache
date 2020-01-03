===============
缓存项接口
===============


+-------------+-------------------------------+
|属性         |值                             |
+=============+===============================+
|命名空间     |fize\\cache                    |
+-------------+-------------------------------+
|类名         |ItemInterface                  |
+-------------+-------------------------------+
|实现接口     |Psr\\Cache\\CacheItemInterface |
+-------------+-------------------------------+


:方法:


+------------------+----------------------------------------------------------------------------------+
|方法名            |说明                                                                              |
+==================+==================================================================================+
|`__construct()`_  |构造                                                                              |
+------------------+----------------------------------------------------------------------------------+
|`setHit()`_       |设置是否命中                                                                      |
+------------------+----------------------------------------------------------------------------------+
|`getExpires()`_   |获取缓存项的过期时间戳                                                            |
+------------------+----------------------------------------------------------------------------------+
|`checkHit()`_     |根据设置判断缓存是否有效                                                          |
+------------------+----------------------------------------------------------------------------------+
|`getKey()`_       |Returns the key for the current cache item.                                       |
+------------------+----------------------------------------------------------------------------------+
|`get()`_          |Retrieves the value of the item from the cache associated with this object's key. |
+------------------+----------------------------------------------------------------------------------+
|`isHit()`_        |Confirms if the cache item lookup resulted in a cache hit.                        |
+------------------+----------------------------------------------------------------------------------+
|`set()`_          |Sets the value represented by this cache item.                                    |
+------------------+----------------------------------------------------------------------------------+
|`expiresAt()`_    |Sets the expiration time for this cache item.                                     |
+------------------+----------------------------------------------------------------------------------+
|`expiresAfter()`_ |Sets the expiration time for this cache item.                                     |
+------------------+----------------------------------------------------------------------------------+


方法
======
__construct()
-------------
构造

.. code-block:: php

  abstract public function __construct (
      string $key
  )


:参数:
  +-------+-------+
  |名称   |说明   |
  +=======+=======+
  |key    |键名   |
  +-------+-------+
  
  


::

    禁止擅自初始化「CacheItemInterface」对象
    该类实例只能使用「CacheItemPoolInterface」对象的 getItem() 方法来获取


setHit()
--------
设置是否命中

.. code-block:: php

  abstract public function setHit (
      bool $is_hit
  ) : $this


:参数:
  +-------+-------------+
  |名称   |说明         |
  +=======+=============+
  |is_hit |是否命中     |
  +-------+-------------+
  
  


::

    外部不应直接调用该方法


getExpires()
------------
获取缓存项的过期时间戳

.. code-block:: php

  abstract public function getExpires () : int|null


:返回值:
  返回 null 表示永不过期


checkHit()
----------
根据设置判断缓存是否有效

.. code-block:: php

  abstract public function checkHit () : bool



getKey()
--------
Returns the key for the current cache item.

.. code-block:: php

  abstract public function getKey () : string


:返回值:
  The key string for this cache item.


::

    The key is loaded by the Implementing Library, but should be available to
    the higher level callers when needed.


get()
-----
Retrieves the value of the item from the cache associated with this object's key.

.. code-block:: php

  abstract public function get () : mixed


:返回值:
  The value corresponding to this cache item's key, or null if not found.


::

    The value returned must be identical to the value originally stored by set().
    
    If isHit() returns false, this method MUST return null. Note that null
    is a legitimate cached value, so the isHit() method SHOULD be used to
    differentiate between "null value was found" and "no value was found."


isHit()
-------
Confirms if the cache item lookup resulted in a cache hit.

.. code-block:: php

  abstract public function isHit () : bool


:返回值:
  True if the request resulted in a cache hit. False otherwise.


::

    Note: This method MUST NOT have a race condition between calling isHit()
    and calling get().


set()
-----
Sets the value represented by this cache item.

.. code-block:: php

  abstract public function set (
      mixed $value
  ) : static


:参数:
  +-------+-------------------------------------+
  |名称   |说明                                 |
  +=======+=====================================+
  |value  |The serializable value to be stored. |
  +-------+-------------------------------------+
  
  

:返回值:
  The invoked object.


::

    The $value argument may be any item that can be serialized by PHP,
    although the method of serialization is left up to the Implementing
    Library.


expiresAt()
-----------
Sets the expiration time for this cache item.

.. code-block:: php

  abstract public function expiresAt (
      \DateTimeInterface|null $expiration
  ) : static


:参数:
  +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |名称       |说明                                                                                                                                                                                                                              |
  +===========+==================================================================================================================================================================================================================================+
  |expiration |The point in time after which the item MUST be considered expired.
  If null is passed explicitly, a default value MAY be used. If none is set,
  the value should be stored permanently or for as long as the
  implementation allows. |
  +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  The called object.


expiresAfter()
--------------
Sets the expiration time for this cache item.

.. code-block:: php

  abstract public function expiresAfter (
      int|\DateInterval|null $time
  ) : static


:参数:
  +-------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  |名称   |说明                                                                                                                                                                                                                                                                                                                               |
  +=======+===================================================================================================================================================================================================================================================================================================================================+
  |time   |The period of time from the present after which the item MUST be considered
  expired. An integer parameter is understood to be the time in seconds until
  expiration. If null is passed explicitly, a default value MAY be used.
  If none is set, the value should be stored permanently or for as long as the
  implementation allows. |
  +-------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  The called object.


