========
安装说明
========

FizeCache 的环境要求如下：

-  "php": ">=5.4.0"
-  如果使用 Database 处理器，请安装 `FizeDb <https://fizedb.readthedocs.io/zh_CN/latest/index.html>`_。
-  如果使用 File 处理器，请安装 `FizeCrypt <https://fizecrypt.readthedocs.io/zh_CN/latest/index.html>`_ 和 `FizeIo <https://fizeio.readthedocs.io/zh_CN/latest/index.html>`_。
-  如果使用 Memcache 处理器，请开启 memcache 扩展。
-  如果使用 Memcached 处理器，请开启 memcached 扩展。
-  如果使用 Redis 处理器，请开启 redis 扩展。

使用Composer安装
================

FizeCache 支持使用 `Composer <https://www.phpcomposer.com/>`_ 安装，也是唯一官方推荐的安装方法。

.. note::

   如果您尚未安装 composer ，请参考 `安装 composer <https://docs.phpcomposer.com/00-intro.html>`_ 。
   
   使用 `阿里云镜像 <https://developer.aliyun.com/composer?spm=a2c4e.11153940.0.0.40eb6995lM3bEz>`_ 以提高下载速度及稳定性。


在命令行下面，切换到您的项目根目录下面并执行下面的命令：

.. code-block:: bash

  composer require fize/cache

根据需要，选择 FizeCache 处理器。使用 composer 下载依赖或者开启相应扩展。
  
好了！您现在可以开始使用 FizeCache 了，就是这么简单！~

.. note::

   Fize 项目(包括所有子项目)严格遵守 `语义化版本 <https://semver.org/lang/zh-CN/spec/v2.0.0.html>`_ ，您可以放心大胆的使用。