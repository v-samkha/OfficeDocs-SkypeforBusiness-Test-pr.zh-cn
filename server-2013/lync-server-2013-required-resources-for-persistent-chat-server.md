﻿---
title: Lync Server 2013：持久聊天服务器所需的资源
TOCTitle: 所需资源
ms:assetid: bce50b95-f3c8-407e-963a-d8896ee77fbc
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/JJ205211(v=OCS.15)
ms:contentKeyID: 49314075
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 持久聊天服务器所需的资源

 

_**上一次修改主题：** 2016-02-05_

持久聊天服务器的高可用性和灾难恢复需要执行完整操作通常所需的资源之外的额外资源。在配置 持久聊天服务器以实现高可用性和灾难恢复之前，请确保您不仅拥有标准 持久聊天服务器操作所需的资源，还拥有以下资源。有关其他配置信息，请参阅 [在 Lync Server 2013 中配置持久聊天服务器](lync-server-2013-configuring-persistent-chat-server.md)。

  - 一个专用数据库实例，位于 持久聊天服务器服务的主前端所在的同一物理数据中心。此数据库将用作主 持久聊天数据库的 SQL Server 镜像。（可选）如果您希望自动故障转移到镜像数据库，请指定其他 SQL Server 以用作镜像见证服务器。

  - 一个位于其他物理数据中心的专用数据库实例。此数据库将用作主数据中心内的数据库的 SQL Server 日志传送辅助数据库。

  - 一个专用数据库实例，用作辅助数据库的 SQL Server 镜像。（可选）指定其他 SQL Server 以用作镜像见证服务器。它们都必须位于辅助数据库所在的同一物理数据中心。

  - 如果已启用 持久聊天服务器合规性，则需要额外三个专用数据库实例。其分布与之前概述的 持久聊天数据库的实例的分布相同。尽管合规性数据库可以与 持久聊天数据库共享相同的 SQL Server 实例，但我们建议使用独立的实例，以实现高可用性和灾难恢复。

  - 还必须为 SQL Server 日志传送事务日志创建并指定文件共享。两个数据中心中所有运行持久聊天 数据库的 SQL Server 必须对此文件共享具有读/写权限。此共享不会定义为 FileStore 角色的一部分。

  - 辅助数据库服务器上的一个文件共享，用作从主服务器文件共享中复制的 SQL Server 事务日志的目标文件夹。

下图提供了有关如何在两个不同的扩展池拓扑中配置整个 持久聊天服务器池的示例：

  - 数据中心按地理位置分布时的扩展 持久聊天服务器池（高带宽/低延迟）。

  - 数据中心按地理位置分布时的扩展 持久聊天服务器池（低带宽/高延迟）。

下图显示了数据中心按地理位置分布的高带宽/低延迟的扩展 持久聊天服务器池拓扑。

**数据中心按地理位置分布时的扩展持久聊天服务器池（高带宽/低延迟）。**

![持久聊天服务器池 HBW 配置示例](images/JJ205211.55d10910-c824-41e6-bed2-08d13a2abd65(OCS.15).jpg "持久聊天服务器池 HBW 配置示例")

下图显示了数据中心按地理位置分布的低带宽/高延迟的扩展 持久聊天服务器池拓扑。

**数据中心按地理位置分布时的扩展持久聊天服务器池（低带宽/高延迟）。**

![持久聊天服务器池 LBW 配置示例](images/JJ205211.586b0a3a-3767-4991-944f-ee54389512aa(OCS.15).jpg "持久聊天服务器池 LBW 配置示例")

