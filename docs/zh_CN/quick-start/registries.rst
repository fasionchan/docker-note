.. 镜像库
    FileName:   registries.rst
    Author:     Fasion Chan
    Created:    2018-11-29 18:33:01
    @contact:   fasionchan@gmail.com
    @version:   $Id$

    Description:

    Changelog:

    .. meta::
        :description lang=zh:
        :keywords: docker registry

======
镜像库
======

*Docker* 镜像构建完毕，便可在本地宿主运行。
在其他服务器上运行该镜像，则需要借助一个集中存储、分发镜像的服务—— *Docker* 镜像库( *Docker Registry* )。

登录镜像库
==========

对于私有镜像库，需先登录方能使用：

.. code-block:: shell-session

    $ docker login docker.xxxx.com

命令将提示输入用户名及密码用于认证。认证信息也可以通过命令行选项指定：

.. code-block:: shell-session

    $ docker login docker.xxxx.com -u xxxx -p xxxx

命令行选项说明如下：

.. csv-table::
    :header: "短选项", "长选项", "说明"

    "-u", "--user", "用户名"
    "-p", "--password", "密码"

.. comments
    comment something out below

