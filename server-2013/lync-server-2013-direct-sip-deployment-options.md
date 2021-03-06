﻿---
title: Lync Server 2013：直接 SIP 部署选项
TOCTitle: 直接 SIP 部署选项
ms:assetid: 84691944-03f2-4a89-9f2b-1ab3d7f388cc
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398672(v=OCS.15)
ms:contentKeyID: 49313481
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的直接 SIP 部署选项

 

_**上一次修改主题：** 2016-12-08_

本主题提供部署直接 SIP 连接的示例拓扑。

## Lync Server 独立

如果您的组织采用本节中描述的部署方案之一，则可以使用 Lync Server 2013 作为部分或整个组织的唯一电话解决方案。本节详细介绍了以下部署：

  - **增量部署：**此选项假定您现有一个专用交换机 (PBX) 基础结构，并且打算在组织的小型组或团队中逐步引入 企业语音。

  - **Lync Server 仅 VoIP 部署：**此选项假定您正考虑在没有传统电话基础结构的站点上部署 企业语音。

## 增量部署

在增量部署中， Lync Server 2013 是个别团队或部门的唯一电话解决方案，而组织中的其余用户继续使用 PBX。此增量部署策略提供一种方法，通过受控的试点计划将 IP 电话引入企业。最适合由 Microsoft 统一通信为其通信需求提供服务的工作组将移动到 企业语音，而其他用户保留在现有 PBX 上。可以根据需要将其他工作组迁移到 企业语音。

如果对通信要求一致且适合于集中管理的用户组进行了明确的定义，则建议使用增量选项。此选项对于跨越广泛地理区域的团队或部门也起作用，因为对于这样的团队或部门，可以大幅节省长途话费。实际上，此选项对于创建其成员可能会分散在世界各地的虚拟团队非常有用。为了快速响应不断变化的业务要求，您可以创建、调整或解散这样的团队。

下图显示了在 PBX 后面部署 企业语音的通用拓扑。建议针对增量部署使用此拓扑。

**增量部署选项**

![部门迁移选项图](images/Gg398672.e951ecf4-7cd2-425a-9106-76977492d682(OCS.15).jpg "部门迁移选项图")

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>如果要将 Lync Server 部署连接到已认证的直接 SIP 合作伙伴，则 中介服务器和 PBX 之间不需要公用电话交换网 (PSTN) 网关。有关已认证的直接 SIP 合作伙伴的列表，请访问 Microsoft 统一通信开放互操作性计划网站，网址为 <a href="http://go.microsoft.com/fwlink/?linkid=203309%26clcid=0x804" class="uri">http://go.microsoft.com/fwlink/?linkid=203309&amp;clcid=0x804</a>。</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>此图中显示的媒体路径已启用媒体旁路（推荐配置）。如果选择禁用媒体旁路，则媒体路径将通过 中介服务器进行路由。</td>
</tr>
</tbody>
</table>


在此拓扑中，已为选定的部门或工作组启用 企业语音。PSTN 网关会将已启用 IP 语音 (VoIP) 的工作组链接到 PBX。已启用 企业语音的用户（包括远程工作者）将通过 IP 网络进行通信。 企业语音用户对 PSTN 和未启用 企业语音的同事的呼叫将路由到相应的 PSTN 网关。来自仍使用 PBX 系统的同事的呼叫或者来自 PSTN 上呼叫者的呼叫将被路由到 PSTN 网关，该网关再将这些呼叫转接到 Lync Server 进行路由。

连接 企业语音与现有 PBX 基础结构进行互操作时，建议采用以下两种配置： 企业语音位于 PBX 后面和 企业语音位于 PBX 前面。

## 企业语音位于 PBX 后面

如果在 PBX 后面部署 企业语音，来自 PSTN 的所有呼叫都将到达 PBX，PBX 会将对 企业语音用户的呼叫路由到 PSTN 网关，并将对 PBX 用户的呼叫路由到 PBX。

## 企业语音位于 PBX 前面。

如果在 PBX 前面部署 企业语音，所有呼叫都将到达 PSTN 网关，该网关会将对 企业语音用户的呼叫路由到 Lync Server，并将对 PBX 用户的呼叫路由到 PBX。 企业语音用户和 PBX 用户对于 PSTN 的呼叫将通过 IP 网络路由到最经济的 PSTN 网关。下表显示了该配置的优缺点。

### 在 PBX 之前部署 企业语音的优缺点

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>优点</th>
<th>缺点</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PBX 仍为那些未启用 企业语音的用户提供服务。</p></td>
<td><p>现有的网关可能不支持所需的功能或容量。</p></td>
</tr>
<tr class="even">
<td><p>PBX 处理所有的早期设备。</p></td>
<td><p>需要从网关到 PBX 和从网关到 中介服务器的中继。可能需要服务提供商提供更多中继。</p></td>
</tr>
<tr class="odd">
<td><p>企业语音用户仍使用原来的电话号码。</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


## Lync Server 仅 VoIP 部署

通过对新公司以及现有公司的新办事处使用 企业语音，您将有机会实现全功能的 VoIP 解决方案，而不必担心与 PBX 集成的问题，也不会出现 IP-PBX 基础结构的大量部署和维护成本。此解决方案既支持现场工作者，又支持远程工作者。

在此部署中，所有呼叫都通过 IP 网络路由。对 PSTN 的呼叫将路由到相应的 PSTN 网关。 Lync 2013 或 Lync Phone Edition 充当软电话。远程呼叫控制不可用，并且也不是必需的，原因是用户不需要控制 PBX 电话。通过 Exchange 统一消息 (UM) 的可选部署，可以使用语音邮件和自动助理服务。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>除了支持 Lync Server 2013 所需的网络基础结构以外，仅 VoIP 部署还可以使用小型合格网关支持传真机和模拟设备。</td>
</tr>
</tbody>
</table>


下图显示了仅 VoIP 部署的典型拓扑。

**仅 VoIP 部署选项**

![绿场部署选项](images/Gg398672.820dc5fe-0e20-431b-ae4e-fefdf2221d3b(OCS.15).jpg "绿场部署选项")

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>此图中显示的媒体路径已启用媒体旁路（推荐配置）。如果选择禁用媒体旁路，则媒体路径将通过 中介服务器进行路由。</td>
</tr>
</tbody>
</table>

