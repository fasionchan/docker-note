.. Rancher
    FileName:   index.rst
    Author:     Fasion Chan
    Created:    2018-12-03 17:37:09
    @contact:   fasionchan@gmail.com
    @version:   $Id$

    Description:

    Changelog:

.. meta::
    :description lang=zh:
        Rancher提供了管理生产级容器所需的全部软件栈。
        Rancher软件栈主要有以下四个组成部分：基础设施编排、容器编排与调度、应用目录以及企业级控制。
    :keywords: rancher, docker, rancher overview, containerized applications, docker swarm, kubernetes, mesos

=======
Rancher
=======

`Rancher` 是一个开源软件平台，让机构部署 **生产级** `Docker` 以及 `Kubernetes` 成为可能。
有了 `Rancher` ，机构无需使用开源技术项目从零开始构建容器服务平台。
`Rancher` 提供了管理生产级容器所需的 **全部软件栈** 。

`Rancher` 软件栈主要有以下四个组成部分：

.. figure:: /_images/platform/rancher/index/244f3bdcdfde2848135e6fc2ec6abe8c.png

    *Rancher主要组件及特性*

基础设施编排
============

`Rancher` **计算资源** 由 `Linux` 主机组成，可以由任何 **公有云** 或 **私有云** 提供。
`Linux` 主机可以是虚拟机，也可以是物理机。
`Rancher` 从每台主机获得 `CPU` 、内存、磁盘以及网络资源。
在 `Rancher` 看来，一台由云厂商提供的虚拟实例与一台物理服务器并没有任何区别。

`Rancher` 实现了一个可移植的 **基础设施** 服务层来驱动 **容器化服务** 。
`Rancher` 基础设施服务包括：网络、存储、负载均衡、 `DNS` 以及安全。
`Rancher` 基础设施服务本身也是作为容器来部署的，因此可以部署在任何 `Linux` 主机上。

容器编排与调度
==============

很多用户选择容器编排调度框架来运行容器化应用。
`Rancher` 现在支持主流的容器编排调度框架，包括： `Docker Swarm` 、 `Kubernetes` 以及 `Mesos` 。
同个用户可以创建多个 `Swarm` 或者 `Kubernetes` 集群。
用户甚至可以使用原生 `Swarm` 或者 `Kubernetes` 工具来管理应用。

除了 `Swarm` 、 `Kubernetes` 以及 `Mesos` ， `Rancher` 还提供了自己的容器编排调度框架—— `Cattle` 。
`Cattle` 被 `Rancher` 广泛应用于编排基础设施服务，
包括设置、管理和升级 `Swarm` 、 `Kubernetes` 以及 `Mesos` 集群。

应用目录
========

借助应用目录， `Rancher` 用户可以 **一键式** 部署 **多容器** 集群应用。
用户可以管理已部署应用并且在应用新版本就绪时 **全自动升级** 。
`Rancher` 维护了一个包含常见应用的公有目录，由 `Rancher` 社区贡献而来。
`Rancher` 用户也可以创建自己的私有目录。

企业级控制
==========

`Rancher` 支持灵活的 **用户认证** 插件，内部集成了 `Active Directory` 、 `LDAP` 以及 `Github` 等认证方式。
`Rancher` 支持按环境的 **角色访问控制** ( `Role-Based Access Control` )，
允许用户和用户组分享或拒绝 **开发** 和 **生产** 环境的访问权限。

下一步
======

.. include:: /_fragments/next-step-to-wechat-mp.rst

.. include:: /_fragments/wechat-reward.rst

.. include:: /_fragments/disqus.rst

.. comments
    comment something out below

