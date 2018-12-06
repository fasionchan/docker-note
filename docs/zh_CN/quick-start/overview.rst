.. Docker概览
    FileName:   overview.rst
    Author:     Fasion Chan
    Created:    2018-12-04 10:01:08
    @contact:   fasionchan@gmail.com
    @version:   $Id$

    Description:

    Changelog:

.. meta::
    :description lang=zh:
    :keywords:

==========
Docker概览
==========

`Docker`_ 是一个用于开发、分发以及运行应用的开源平台。
*Docker* 将应用与基础设施(硬件)分离，以便软件快速分发。
借助 *Docker* ，你可以采用与管理应用相同的方式来管理基础设施。
*Docker* 提供了一系列快速分发、测试以及部署代码的方法，
显著减少从编写代码到生产级运行的时间。

Docker平台
==========

`Docker` 提供了用容器打包运行应用的能力，容器是一种松散的隔离环境。
由于 **隔离性** 和 **安全性** ，一台主机可以同时运行很多容器。
容器是轻量级的，因为它们不需要额外的模拟器，直接跑在宿主机内核中。
与虚拟机相比，同样条件的硬件机器可以运行更多的容器。
你甚至也可以在虚拟机中运行 *Docker* 容器。

*Docker* 提供管理容器整个生命周期的工具和平台：

- 使用容器 **开发** 应用及其支撑组件；
- 以容器为单位进行应用部署和 **测试** ；
- 一切就绪后，将应用 **部署** 到 **生产环境** ，应用可以是原始容器或者服务编排，
  生产环境可以是本地数据中心、云提供商或者两者结合；

Docker引擎
==========

*Docker* 引擎是一个典型的 *CS* ( *client-server* )架构的应用，主要组件包括：

- 服务器是一个长时间运行的 `守护程序` ( `dockerd` 命令)；
- 服务提供 `RESTful` 接口供外部程序调用；
- 命令行工具( `docker` 命令)；

.. figure:: /_images/quick-start/overview/3f7ab62915a67bf91b85838cf0248c20.png

    *Docker引擎结构*

命令行工具( `CLI` )通过 `Restful` 接口与 `Docker` 守护程序交互，既可直接运行，亦可在脚本中调用。
很多 *Docker* 应用均使用底层 `API` 或者命令行工具。

守护程序创建并管理 *Docker* 对象，例如： :doc:`images` ，容器，网络以及卷。

Docker可以做什么
================

持续交付
--------

使用 *Docker* ，研发人员可以用容器这种 **标准化** 环境来提供应用和服务，极大缩短研发周期。
容器特别适用于 **持续集成** ( *continuous integration* ， *CI* )
以及 **持续交付** ( *continuous delivery* ， *CD* )型工作流。

试想以下场景：

- 研发人员在本地编写代码并通过容器与同事分享工作成果；
- 研发人员使用 `Docker` 将应用推到测试环境并执行自动化测试以及手工测试；
- 发现 *BUG* 后，研发人员在开发环境快速修复并重新部署到测试环境进行验证；
- 测试通过后，发布补丁也非常简单，将新镜像推到生产环境即可；

灵活部署
--------

*Docker* 基于容器的特性特别适用于可移植的工作场景。
容器可以跑在各种各样的环境上：研发人员本地电脑；数据中心物理机或虚拟机；云提供商等等。

由于可移植以及轻量级的特性， *Docker* 能够轻松实现动态服务负荷管理，
近乎 **实时** 地实现业务急需的扩容或缩容动作。

节约硬件
--------

*Docker* 非常轻量级，因此很高效。
相比基于模拟器的虚拟化技术， *Docker* 更可行，开销更小，更能充分挖掘机器的处理能力。
*Docker* 非常适合高密度环境以及资源有限而业务繁多的中小型部署。


Docker架构
==========

*Docker* 采用 `CS` 架构。
*Docker* 客户端与 *Docker* 守护程序通讯，容器构建、运行、部署均由守护程序直接负责。
客户端和守护程序可以部署在同台机器，或者通过网络远程连接。
客户端通过 `Restful API` 与守护程序交互，走 `Unix` 套接字或网络均可。

.. figure:: /_images/quick-start/overview/b595b80b1dc39db2af4ffd6f0e8e8f55.svg

    *Docker架构*

Docker守护程序
--------------

`Docker` 守护程序( `dockerd` )监听 `API` 请求并管理 `Docker` 对象，包括镜像、容器、网络以及卷等。
为管理 `Docker` 服务，守护程序也可以跟其他守护程序进行通讯。

Docker客户端
------------

`Docker` 客户端( `docker` 命令)是大部分用户与 `Docker` 交互的主要方式。
当用户执行形如 `docker run` 的操作命令后，客户端将命令发送给 `dockerd` ，由它负责执行。
`docker` 命令使用 `Docker` *API* 与 `dockerd` 通讯。
客户端可与多个守护程序通讯。

Docker镜像库
------------

:doc:`registries` ( `registry` )是存储 *Docker* 镜像的地方。
`Docker Hub`_ 和 `Docker Cloud`_ 是公共镜像库，任何人均可使用。
*Docker* 默认使用 `Docker Hub`_ 。
用户可以部署自己的私有镜像库。
*Docker* 数据中心( *DDC* )包括 *Docker* 镜像库( *DTR* )。

执行 :code:`docker pull` 或 :code:`docker run` 时，需要的镜像将从配置的镜像库拉取；
执行 :code:`docker push` 时，镜像将推送到配置的镜像库。

`Docker商店`_ 是买卖镜像的地方，免费发布当然也可以。
例如，你可以从软件供应商那购买一个包含应用或服务的镜像，并将其部署到自己的测试、预发布乃至生产环境。
拉取新版本镜像并重新部署容器即可完成软件升级，方便快捷。

Docker对象
----------

使用 `Docker` 时，你会创建并使用镜像、容器、网络、卷、插件以及其他 *Docker* 对象。
本节简要介绍其中部分常用对象。

镜像
++++

镜像是一个用于创建 *Docker* 容器的只读模板。
新镜像通常以母镜像为基础，进行额外定制而成。
举个例子，你可以基于 `ubuntu`_ 镜像构建新镜像，
安装 `Apache` `Web` 服务器以及应用程序，同时添加必要的配置文件。

你可以构建自己的镜像，也可以直接使用别人创建并发布的镜像。
创建新镜像需要先准备 `Dockerfile` 文件，定义构建所需的步骤以及执行方式。
`Dockerfile` 提供简单的指令语法，每个指令均在原镜像之上叠加新层。
修改 `Dockerfile` 后重新构建镜像，只有变更层需要重建。
这是镜像与其他虚拟化技术相比更为 **轻量级** 、更 **小巧** 也更 **高效** 的原因。

容器
++++

容器是镜像的可执行实例。
用户可通过 `API` 或客户端创建、启动、暂停、移动或者删除容器。
用户可将容器连到一个或多个网络，挂载存储介质，或者基于其当前状态创建新镜像。

默认，容器与其他容器以及宿主机相对隔离。
用户可以根据需要调整容器网络、存储以及其他底层子系统与其他容器以及宿主机的隔离性。

容器由其镜像以及创建该容器时提供的可配置选项定义。
删除容器时，所有状态变更将被清除，除非存于永久存储设备。

Docker服务
----------

*Docker* `swarm` 服务提供集群容器弹性部署，服务由 **管理节点** 及 **工作节点** 组成。
每个 `swarm` 成员均为 *Docker* 守护程序，所有守护程序通过 *Docker API* 通讯。
用户可以定义目标状态，例如服务实例数。
默认，服务在所有工作节点上做负载均衡。
在用户看来， *Docker* 服务是一个单一应用。
*Docker* 引擎在版本 *1.12* 后均支持 `swarm` 模式。

实例
----

以下命令启动一个 `ubuntu` 容器，交互式地附上当前命令行会话，并执行 ``/bin/bash`` ：

.. code-block:: shell-session

    $ docker run -i -t ubuntu /bin/bash

#. 如果 `ubuntu` 镜像本地不存在， *Docker* 将从镜像库拉取，等价于手工运行 :code:`docker pull ubuntu` 命令；
#. *Docker* 创建新镜像，等价于手工运行 :code:`docker container create` 命令；
#. *Docker* 为容器分配一个可读可写的文件系统，作为最后一层。
   容器运行起来后，可以创建或修改本地文件及目录；
#. 由于命令中未指定网络选项， *Docker* 创建网络接口并将容器连到默认网络，同时为容器分配 *IP* 地址。
   默认，容器可通过宿主连接外部网络；
#. *Dcoker* 启动容器并执行 ``/bin/bash`` 命令。
   由于容器是交互式执行的，并且附上终端( `-i` 及 `-t` 选项)，用户可以通过键盘进行输入，而程序也在终端输出；
#. 输入 ``exit`` 命令终止 ``/bin/bash`` 命令后，容器停止但不删除。后续可以再次启动该容器或者将其删除；

底层技术
========

*Docker* 由 `Go <https://golang-book.readthedocs.io/zh_CN/latest/>`_ 语言开发，
为实现功能用到了若干 `Linux <https://learn-linux.readthedocs.io/zh_CN/latest/>`_ 内核特性：

namespace
---------

*Docker* 利用 **命名空间** ( `namespaces` )技术实现容器隔离工作环境。
运行容器时， *Docker* 为容器创建一个命名空间集。

命名空间提供了一定级别的 **隔离性** ( *isolation* )。
容器每部分运行在隔离的名字空间中，并将访问限制在该名字空间内。

`Docker` 使用以下 `Linux` 命名空间：

- `pid` 命名空间：进程隔离( *PID* 即进程 *ID* )；
- `net` 命名空间：管理网络界面；
- `ipc` 命名空间：管理进程间通讯资源( `ipc` 进程间通讯)；
- `mnt` 命名空间：管理文件系统挂载点；
- `uts` 命名空间：隔离内核及版本识别符( `uts` 即 *Unix Timesharing System* )；

cgroup
------

*Docker* 还依赖另一种 *Linux* 技术—— **控制组** ( *control groups* ，即 *cgroups* )。
控制组将应用程序对资源的消耗控制在给定范围内。
利用该技术， *Docker* 引擎可以将硬件资源分享给多个容器，并对用量加以限制。
例如，你可以限制指定容器可用的内存。

UnionFS
-------

`Union` 文件系统，简称 `UnionFS` ，操作通过创建新数据层进行，非常轻量快捷。
*Docker* 引擎采用 *UnionFS* 作为基础模块构建容器。
*Docker* 引擎兼容多种 `UnionFS` 变体，包括 `AUFS` 、 `btrfs` 、 `vfs` 以及 `DeviceMapper` 。

容器格式
--------

*Docker* 引擎将 `namespace` 、 `cgroup` 以及 `UnionFS` 组合起来形成统一包装—— **容器格式** ( `container format` )。
默认的容器格式是 `libcontainer` 。
未来 *Docker* 可能支持更多容器格式，并将 `BSD Jails` 、 `Solaris Zones` 等技术整合进去。

下一步
======

.. include:: /_fragments/next-step-to-wechat-mp.rst

.. include:: /_fragments/wechat-reward.rst

.. include:: /_fragments/disqus.rst

.. _Docker: https://www.docker.com/
.. _Docker Cloud: https://cloud.docker.com/
.. _Docker Hub: https://hub.docker.com/
.. _Docker商店: http://store.docker.com/
.. _ubuntu: https://hub.docker.com/_/ubuntu/

.. comments
    comment something out below

