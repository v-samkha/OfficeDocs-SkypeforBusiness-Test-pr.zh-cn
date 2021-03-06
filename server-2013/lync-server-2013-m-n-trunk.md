﻿---
title: Lync Server 2013：M:N 中继
TOCTitle: M:N 中继
ms:assetid: dc4c5d66-297c-48a5-91b9-b9b8ce44a6e0
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398971(v=OCS.15)
ms:contentKeyID: 49314463
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的 M:N 中继

 

_**上一次修改主题：** 2012-10-01_

Lync Server 2013 在定义用于呼叫路由的中继方面比早期版本具有更大的灵活性。中继是 中介服务器与侦听端口号之间以及网关与侦听端口号之间的逻辑关联。这意味着以下几项内容：一个 中介服务器可以有多个到同一网关的中继；一个 中介服务器可以有多个到不同网关的中继；相反，一个网关可以有多个到不同 中介服务器的中继。

使用 拓扑生成器向 Lync 拓扑添加网关时，仍需要创建根中继。给定的 中介服务器可以处理的网关数取决于服务器在高峰忙碌时段的处理能力。如果在超过 Lync Server 2013 的最低硬件要求（如可支持性文档中的“[支持的适用于 Lync Server 2013 的硬件](lync-server-2013-supported-hardware.md)”中所述）的硬件上部署 中介服务器，那么估计独立的 中介服务器可以处理的活动无绕过呼叫数量大约是 1000 个。在满足这些规范的硬件上进行部署时， 中介服务器应执行代码转换，但仍将为多个网关路由呼叫，即使网关不支持媒体旁路也是如此。

定义呼叫路由时，需指定与该路由关联的中继，但不必指定与该路由关联的 中介服务器。而是使用 拓扑生成器将中继与 中介服务器相关联。换句话说，路由可确定用于呼叫的网关，随后与该中继关联的 中介服务器将被发送用于该呼叫的信号。

中介服务器可以部署为池；该池可以与 前端池并置，也可以作为独立的池进行部署。 中介服务器与 前端池并置时，池的大小最多为 10（注册器池大小的限制）。综合而言，这些新功能增加了 中介服务器的可靠性和部署灵活性，但需要以下对等实体中的相关功能：

  - **PSTN 网关。**Lync Server 2013 的合格网关必须实现 DNS 负载平衡，以便合格的公用电话交换网 (PSTN) 网关可以充当一个 中介服务器池的负载平衡器，从而对整个池的呼叫进行负载平衡。

  - **会话边界控制器。**对于 SIP 中继，对等实体是 Internet 电话服务提供商的会话边界控制器 (SBC)。方向为从 中介服务器池池到 SBC 时，SBC 可以接收来自池中任何 中介服务器的连接。方向为从 SBC 到池时，可将流量发送到池中的任何 中介服务器。实现此功能的一个方法是通过 DNS 负载平衡（如果服务提供商和 SBC 支持）。另一种方法是为服务提供商提供池中所有 中介服务器的 IP 地址，服务提供商会在其 SBC 中将这些 IP 地址分别设置为每个 中介服务器的 SIP 中继。然后，服务提供商将处理自己的服务器的负载平衡。并非所有服务提供商或 SBC 都可以支持这些功能。此外，服务提供商可能会对此功能收取额外费用。通常，每个到 SBC 的 SIP 中继按月收费。

  - **IP-PBX。**方向为从 中介服务器池池到 IP-PBX SIP 终端时，IP-PBX 可以接收来自池中任何 中介服务器的连接。方向为从 IP-PBX 到池时，可将流量发送到池中的任何 中介服务器。由于大多数 IP-PBX 不支持 DNS 负载平衡，因此建议将各个直接 SIP 连接定义为从 IP-PBX 到池中的每台 中介服务器。然后，IP-PBX 将通过向中继组分发流量处理自己的负载平衡。假定中继组在 IP-PBX 中具有一组一致的路由规则。需要先确定特定的 IP-PBX 是否支持此中继组概念以及如何与 IP-PBX 自身的冗余/群集基础结构相交，然后才能确定 中介服务器群集能否正确地与 IP-PBX 进行交互。

中介服务器池必须具有与其进行交互的对等网关的统一视图。这意味着池中的所有成员都能从配置存储访问对等网关的同一定义，并且都可能针对传出呼叫与其进行交互。因此，也就无法划分池，这样某些 中介服务器只能针对传出呼叫与特定的对等网关进行通信。如果此类划分有必要，则必须使用单独的 中介服务器池。例如，如果与池进行交互的 PSTN 网关、SIP 中继或 IP-PBX 中的相关功能（如本主题中前面所述）不存在，则此情况适用。

特定的 PSTN 网关、IP-PBX 或 SIP 中继可以路由到多个 中介服务器或中继。特定的 中介服务器池可以控制的网关数取决于使用媒体旁路的呼叫的数目。如果大量呼叫使用媒体旁路，则池中的 中介服务器可以处理更多的呼叫，因为只有信号层处理是必需的。

