---
title: 将 NetTcpBinding 应用程序转换为对等通道应用程序
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 42266d8c7c04e2d8f3f1e4734d9a05181c3f1ea3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595552"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="f2a52-102">将 NetTcpBinding 应用程序转换为对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="f2a52-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="f2a52-103">可以通过使用描述连接参数的绑定，在使用 WinFX 的客户端之间创建连接。</span><span class="sxs-lookup"><span data-stu-id="f2a52-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="f2a52-104">将 .NET Framework 应用程序转换为使用对等连接时，需要在建立客户端连接时支持该技术的绑定。</span><span class="sxs-lookup"><span data-stu-id="f2a52-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="f2a52-105">对等通道提供了一种称为 <xref:System.ServiceModel.NetPeerTcpBinding> 的绑定，其使用方式与 <xref:System.ServiceModel.NetTcpBinding> 类似。</span><span class="sxs-lookup"><span data-stu-id="f2a52-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="f2a52-106">关键区别包括指定解析程序服务和定义安全设置。</span><span class="sxs-lookup"><span data-stu-id="f2a52-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="f2a52-107">如果应用程序使用默认解析程序和安全设置，那么将基于客户端/服务器的标准应用程序转换为使用对等通道需要在应用程序配置文件中将绑定名称从“NetTcpBinding”更改为“NetPeerTcpBinding”，而无需更改应用程序基本代码。</span><span class="sxs-lookup"><span data-stu-id="f2a52-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a52-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2a52-108">See also</span></span>

- [<span data-ttu-id="f2a52-109">生成对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="f2a52-109">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="f2a52-110">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="f2a52-110">System-Provided Bindings</span></span>](../system-provided-bindings.md)
