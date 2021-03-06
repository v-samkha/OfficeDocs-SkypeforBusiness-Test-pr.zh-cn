﻿---
title: Lync Server 2013：在前端服务器上部署 IP 地址类型
TOCTitle: 在前端服务器上部署 IP 地址类型
ms:assetid: b6c8e0f9-ec8e-4a4e-a525-756f9cd6b9d0
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/JJ205191(v=OCS.15)
ms:contentKeyID: 49314014
ms.date: 07/28/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 针对 Lync Server 2013 在前端服务器上部署 IP 地址类型

 

_**上一次修改主题：** 2016-07-28_

通过使用 拓扑生成器，执行以下过程中的步骤在 前端服务器上部署 IP 地址类型。

## 在前端服务器上部署 IP 地址类型

1.  在“Enterprise Edition 前端池”下，右键单击池中的服务器，然后选择“编辑属性”。（也可以选择服务器，然后单击“操作”菜单中的“编辑属性”。）

2.  在“编辑属性”对话框中，选择您要配置的 IP 地址类型。对于双协议栈配置，则选择“启用 IPv4”和“启用 IPv6”，如下图所示。
    
    **前端服务器池的“编辑属性”对话框**
    
    ![前端服务器“编辑属性”对话框](images/JJ205191.737a9d71-c0bc-4a54-9608-9e028dacc814(OCS.15).png "前端服务器“编辑属性”对话框")
    
      - **使用所有配置 IP 地址**。如果您希望允许使用计算机上定义的任何 IP 地址，请选择此选项。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>这是针对 IP 版本 6 (IPv6) 配置的建议选项。</td>
        </tr>
        </tbody>
        </table>
    
      - **服务仅供选定 IP 地址使用**。选择此选项可指定要在新服务器上使用的特定地址。如果选择此选项，则必须输入“主 IP 地址”的值。
    
      - **主 IP 地址**。输入用于除公用电话交换网 (PSTN) 之外的所有通信的 IP 地址。所输入的 IP 地址必须符合选择的地址类型的格式。
    
      - **PSTN IP 地址**。在前端服务器上并置中介服务器时定义一个 PSTN IP 地址。该地址必须符合选择的地址类型的格式。

