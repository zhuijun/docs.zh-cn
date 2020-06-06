---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398406"
---
# \<allowAccounts>
<span data-ttu-id="0799a-101">包含一个配置元素集合，这些元素为承载 Windows Communication Foundation （WCF）服务且被授予对共享服务的连接访问权限的进程指定用户帐户。</span><span class="sxs-lookup"><span data-stu-id="0799a-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="0799a-102">语法</span><span class="sxs-lookup"><span data-stu-id="0799a-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0799a-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0799a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0799a-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0799a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0799a-105">特性</span><span class="sxs-lookup"><span data-stu-id="0799a-105">Attributes</span></span>  
 <span data-ttu-id="0799a-106">无。</span><span class="sxs-lookup"><span data-stu-id="0799a-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0799a-107">子元素</span><span class="sxs-lookup"><span data-stu-id="0799a-107">Child Elements</span></span>  
  
|<span data-ttu-id="0799a-108">属性</span><span class="sxs-lookup"><span data-stu-id="0799a-108">Attribute</span></span>|<span data-ttu-id="0799a-109">说明</span><span class="sxs-lookup"><span data-stu-id="0799a-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="0799a-110">为承载 WCF 服务且被授予对共享服务的连接访问权限的进程添加用户帐户</span><span class="sxs-lookup"><span data-stu-id="0799a-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0799a-111">父元素</span><span class="sxs-lookup"><span data-stu-id="0799a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0799a-112">元素</span><span class="sxs-lookup"><span data-stu-id="0799a-112">Element</span></span>|<span data-ttu-id="0799a-113">描述</span><span class="sxs-lookup"><span data-stu-id="0799a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0799a-114">[\<net.pipe>](net-pipe.md)或[\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="0799a-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="0799a-115">指定 Net Pipe 或 TCP 共享服务的配置设置。</span><span class="sxs-lookup"><span data-stu-id="0799a-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0799a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0799a-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
