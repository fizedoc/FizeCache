=========
Memcached
=========

Memcached处理器配置
===================

+---------------+-----------------------------------------+---------+------------------------------+
|参数名         |说明                                     |是否可选 |默认值                        |
+===============+=========================================+=========+==============================+
|servers        |Memcached初始化参数                      |是       |[['localhost', 11211, 100]]   |
+---------------+-----------------------------------------+---------+------------------------------+
|timeout        |Memcached超时时间                        |是       |10                            |
+---------------+-----------------------------------------+---------+------------------------------+
|expire         |有效时间，以秒为单位,0表示永久有效。     |是       |0                             |
+---------------+-----------------------------------------+---------+------------------------------+

.. warning::

   Memcached处理器暂未进行单元测试，请根据实际情况酌情使用。