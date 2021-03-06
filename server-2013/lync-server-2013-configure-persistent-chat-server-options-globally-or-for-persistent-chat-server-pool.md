﻿---
title: Lync Server 2013：全局或为持久聊天服务器池配置持久聊天服务器选项
TOCTitle: 全局或为持久聊天服务器池配置持久聊天服务器选项
ms:assetid: 1e8d5245-cd58-4aad-9a1c-35b24189bc40
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/JJ204731(v=OCS.15)
ms:contentKeyID: 49312201
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 在 Lync Server 2013 中全局或为持久聊天服务器池配置持久聊天服务器选项

 

_**上一次修改主题：** 2012-10-06_

在 Lync Server 2013 控制面板中，您可以使用“持久聊天”页的“持久聊天配置”部分全局（如果适用于所有 持久聊天服务器池）或针对特定 持久聊天服务器池配置 持久聊天设置。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>要配置和使用 持久聊天服务器，则必须先使用 拓扑生成器将 持久聊天服务器支持添加到拓扑，然后发布该拓扑。有关详细信息，请参阅部署文档中的 <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">在 Lync Server 2013 中将持久聊天服务器添加到部署</a>。</td>
</tr>
</tbody>
</table>


## 全局配置持久聊天选项

1.  使用分配给 CsPersistentChatAdministrator 或 CsAdministrator 角色的用户帐户登录您的本地部署中的任一计算机。

2.  从“开始”菜单中选择 Lync Server 控制面板或打开浏览器窗口，然后输入管理 URL。有关可用于启动 Lync Server 控制面板的不同方法的详细信息，请参阅[打开 Lync Server 管理工具](lync-server-2013-open-lync-server-administrative-tools.md)。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>您还可以使用 Windows PowerShell cmdlet。有关详细信息，请参阅部署文档中的 <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">使用 Windows PowerShell Cmdlet 配置持久聊天服务器</a>。</td>
    </tr>
    </tbody>
    </table>


3.  在左侧导航栏中，单击“持久聊天”，然后单击“持久聊天配置”。

4.  在“持久聊天配置”页上，单击“新建”，然后单击“站点配置”。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>如果要将配置应用于在站点中部署的所有持久聊天服务器池，请选择此选项。如果要将配置应用于特定持久聊天服务器池，请单击“池配置”。</td>
    </tr>
    </tbody>
    </table>


5.  在“选择站点”中，为持久聊天服务器站点配置选择要配置的站点。

6.  在“新建持久聊天配置”中，执行以下操作：
    
      - 在“名称”中，指定新配置设置的名称。默认情况下，已存在站点名称。
    
      - 在“默认聊天历史记录”中，定义首次请求时每个聊天室要处理的聊天消息的数目。默认情况下，此数目为 30。这是全局默认值，管理员可根据每个类别禁用聊天历史记录。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>持久聊天服务器将在内存中缓存这些消息，因此如果增加此数目，将缓存更多消息。您始终可通过搜索来访问历史内容。默认数目只确定您在连接到聊天室时最初看到的最大消息数。</td>
        </tr>
        </tbody>
        </table>
    
      - 在“最大文件大小(KB)”中，选择每条聊天历史记录的最大文件大小。默认情况下，此数目为 20 MB (20,000 KB)。这是可以上载到系统（已通过对应的“类别”设置为其启用文件上载）中任意聊天室的文件的最大大小。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>此设置在服务器上强制实施，因为使用 Office Communications Server 2007 R2群聊服务器或 Lync Server 2010 群聊的自定义应用程序或以前的 群聊客户端可以将文件张贴到聊天室。 Lync 2013 客户端不具有文件上载/下载功能，因此如果您采用纯 Lync 2013 部署或 Lync 2013 客户端，则可能无法在 持久聊天服务器聊天室中张贴文件。</td>
        </tr>
        </tbody>
        </table>
    
      - 在“参与者更新限制”中，选择对参与者更新的限制。持久聊天服务器会将名单信息（连接至聊天室）发送给所有参与者，直至连接的用户数达到此数目。默认情况下，此数目为 75。此限制指示给定聊天室的参与者的最大数目，超过该数目后， 持久聊天服务器将停止向连接的客户端发送关于聊天室中在线人员的名单更新。
    
      - （可选。）在“聊天室管理 URL”中，选择聊天室管理 URL。这是基于 Web 的自定义聊天室管理的 URL。如果不需要自定义聊天室管理并且只想使用默认设置，请将此选项留空。在设置该 URL 后，它将应用为内部和外部聊天室管理 URL。
        
        如果您想要自定义聊天室创建体验，并包括您的特定业务工作流，可使用 持久聊天服务器软件开发工具包 (SDK) 构建一个自定义聊天室管理解决方案，将其托管到某个位置并将 URL 放在此处。此 URL 将被发送给客户端，以便用户在尝试查看或创建聊天室时将被定向到您的自定义聊天室管理解决方案。

7.  单击“提交”。

## 为特定持久聊天服务器池配置持久聊天选项

1.  使用分配给 CsPersistentChatAdministrator 或 CsAdministrator 角色的用户帐户登录您的本地部署中的任一计算机。

2.  从“开始”菜单选择 Lync Server 控制面板或打开浏览器窗口，然后输入管理 URL。有关可用于启动 Lync Server 控制面板的各种方法的详细信息，请参阅[打开 Lync Server 管理工具](lync-server-2013-open-lync-server-administrative-tools.md)。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>您还可以使用 Windows PowerShell cmdlet。有关详细信息，请参阅部署文档中的 <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">使用 Windows PowerShell Cmdlet 配置持久聊天服务器</a>。</td>
    </tr>
    </tbody>
    </table>


3.  在左侧导航栏中，单击“持久聊天”，然后单击“持久聊天配置”。

4.  在“持久聊天配置”页上，单击“新建”，然后单击“池配置”。

5.  在“选择服务”中，选择与要配置的 持久聊天服务器池关联的服务。

6.  在“新建 持久聊天配置”中，执行以下操作：
    
      - 在“名称”中，指定新配置设置的名称。默认情况下，已存在站点池名称。
    
      - 在“默认聊天历史记录”中，定义首次请求时每个聊天室要处理的聊天消息的数目。默认情况下，此数目为 30。这是全局默认值，管理员可根据每个类别禁用聊天历史记录。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>持久聊天服务器将在内存中缓存这些消息，因此如果增加此数目，将缓存更多消息。您始终可通过搜索来访问历史内容。默认数目只确定您在连接到聊天室时最初看到的最大消息数。</td>
        </tr>
        </tbody>
        </table>
    
      - 在“最大文件大小(KB)”中，选择每条聊天历史记录的最大文件大小。默认情况下，此数目为 20 MB (20,000 KB)。这是可以上载到系统（已通过对应的“类别”设置为其启用文件上载）中任意聊天室的文件的最大大小。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>此设置在服务器上实施，因为自定义应用程序或旧 群聊客户端（ Office Communications Server 2007 R2群聊服务器或 Lync Server 2010 群聊）可将文件张贴到聊天室。 Lync 2013 客户端不具有文件上载/下载功能，因此如果您采用纯 Lync 2013 部署或 Lync 2013 客户端，则可能无法在 持久聊天服务器聊天室中张贴文件。</td>
        </tr>
        </tbody>
        </table>
    
      - 在“参与者更新限制”中，选择对参与者更新的限制。持久聊天服务器会将名单信息（连接至聊天室）发送给所有参与者，直至连接的用户数达到此数目。默认情况下，此数目为 75。此限制指示给定聊天室的参与者的最大数目，超过该数目后， 持久聊天服务器将停止向连接的客户端发送关于聊天室中在线人员的名单更新。
    
      - 在“聊天室管理 URL”中，选择聊天室管理 URL。这是基于 Web 的聊天室管理部署的 URL。如果不需要自定义聊天室管理并且只想使用默认设置，请将此选项留空。
        
        如果您想要自定义聊天室创建体验，并包括您的特定业务工作流，请使用 持久聊天服务器软件开发工具包 (SDK) 构建一个自定义聊天室管理解决方案，将其托管到某个位置并将 URL 放在此处。此 URL 将被发送给客户端，以便用户在尝试查看/创建聊天室时将被定向到您的自定义聊天室管理解决方案。

7.  单击“提交”。

