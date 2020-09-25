---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 3432d33c0cd65af03d2b1ac1302ca2c8ff3e0f43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201637"
---
# \<allowAccounts>

<span data-ttu-id="02400-101">包含一个配置元素的集合，这些元素为承载 Windows Communication Foundation (WCF) 服务并向其授予对共享服务的连接访问权限的进程指定用户帐户。</span><span class="sxs-lookup"><span data-stu-id="02400-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="02400-102">语法</span><span class="sxs-lookup"><span data-stu-id="02400-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02400-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="02400-103">Attributes and Elements</span></span>  

 <span data-ttu-id="02400-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="02400-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02400-105">特性</span><span class="sxs-lookup"><span data-stu-id="02400-105">Attributes</span></span>  

 <span data-ttu-id="02400-106">无。</span><span class="sxs-lookup"><span data-stu-id="02400-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02400-107">子元素</span><span class="sxs-lookup"><span data-stu-id="02400-107">Child Elements</span></span>  
  
|<span data-ttu-id="02400-108">Attribute</span><span class="sxs-lookup"><span data-stu-id="02400-108">Attribute</span></span>|<span data-ttu-id="02400-109">描述</span><span class="sxs-lookup"><span data-stu-id="02400-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="02400-110">为承载 WCF 服务且被授予对共享服务的连接访问权限的进程添加用户帐户</span><span class="sxs-lookup"><span data-stu-id="02400-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02400-111">父元素</span><span class="sxs-lookup"><span data-stu-id="02400-111">Parent Elements</span></span>  
  
|<span data-ttu-id="02400-112">元素</span><span class="sxs-lookup"><span data-stu-id="02400-112">Element</span></span>|<span data-ttu-id="02400-113">描述</span><span class="sxs-lookup"><span data-stu-id="02400-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02400-114">[\<net.pipe>](net-pipe.md) 或 [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="02400-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="02400-115">指定 Net Pipe 或 TCP 共享服务的配置设置。</span><span class="sxs-lookup"><span data-stu-id="02400-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02400-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="02400-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
