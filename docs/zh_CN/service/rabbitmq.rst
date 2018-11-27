.. RabbitMQ
    FileName:   rabbitmq.rst
    Author:     Fasion Chan
    Created:    2018-03-26 19:37:31
    @contact:   fasionchan@gmail.com
    @version:   $Id$

    Description:

    Changelog:

.. meta::
    :description lang=zh:
    :keywords: docker, rabbitmq

========
RabbitMQ
========

获取镜像
========

以 ``3.7`` 版本为例，运行 ``docker pull`` 命令：

.. code-block:: shell-session

    $ docker pull rabbitmq:3.7
    $ docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    rabbitmq            3.7                 b17bd9d70e8b        11 days ago         127MB

.. note::

    Docker官方镜像部署在国外，网络不太稳定。

    ，请参考 :ref:`mirrors` 一节。

.. code-block:: shell-session

    $ docker pull rabbitmq:3.7-management
    $ docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    rabbitmq            3.7-management      df0ee1f2343b        11 days ago         151MB
    rabbitmq            3.7                 b17bd9d70e8b        11 days ago         127MB

.. code-block:: shell-session

    $ docker pull rabbitmq:latest

.. warning::

    推荐关注最新版本动态，但不要在生产环境上直接部署 latest 镜像！
    万一拉到最新版本，与程序代码有兼容性问题，就悲剧了……

    生产环境部署，指定准确的版本号，这样做最保险。

启动镜像
========

.. code-block:: shell-session

    $ docker run -d --hostname rabbit.test --name rabbit.test \
    -e RABBITMQ_ERLANG_COOKIE='XXXX' \
    -e RABBITMQ_DEFAULT_USER='mx' \
    -e RABBITMQ_DEFAULT_PASS='XXXX' \
    -p 5671:5671 \
    -p 5672:5672 \
    -p 15671:15671 \
    -p 15672:15672 \
    rabbitmq:3.7-management

.. comments
    comment something out below

