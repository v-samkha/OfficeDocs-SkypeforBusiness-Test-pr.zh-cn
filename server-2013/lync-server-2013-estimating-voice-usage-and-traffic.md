﻿---
title: Lync Server 2013：估计语音使用和流量
TOCTitle: 估计语音使用和流量
ms:assetid: 621b08fb-f894-4d91-ac38-e443401b098b
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398439(v=OCS.15)
ms:contentKeyID: 49313037
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 估计 Lync Server 2013 的语音使用和流量

 

_**上一次修改主题：** 2012-08-07_

Microsoft Lync Server 2013 规划工具使用以下指标来估计每个站点的用户流量以及支持该流量所需的端口数。

  -   
    对于 **低流量**（每个用户每小时一个 PSTN 呼叫），每个端口对应 15 个用户。

  -   
    对于 **中等流量**（每个用户每小时 2 个 PSTN 呼叫），每个端口对应 10 个用户。

  -   
    对于 **高流量**（每个用户每小时 3 个或更多 PSTN 呼叫），每个端口对应 5 个用户。

端口数反过来决定需要使用的 中介服务器数量和网关数量。大多数组织都考虑部署大小在 2 到 960 个端口之间的公用电话交换网 (PSTN) 网关。（还有更大的网关，但是这些网关主要由电话服务提供商使用。）

例如，具有 10,000 个用户和中等流量的组织将需要 1000 个端口。所需的网关数等于所需的端口总数，由网关的总容量决定。

