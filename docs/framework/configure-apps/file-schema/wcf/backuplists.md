---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 940bf28958251e7257b2cc19a9c5ff0059411bcd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201546"
---
# \<backupLists>

<span data-ttu-id="eea7e-101">表示一个配置节，用于定义一组用来处理错误的备份服务。</span><span class="sxs-lookup"><span data-stu-id="eea7e-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="eea7e-102">每个子元素都是一个备份列表，用于枚举当无法到达主终结点时路由服务将使用的一组终结点。</span><span class="sxs-lookup"><span data-stu-id="eea7e-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="eea7e-103">如果列表中的第一个终结点关闭，则路由服务会自动故障转移到列表中的下一个终结点。</span><span class="sxs-lookup"><span data-stu-id="eea7e-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="eea7e-104">这样，可以方便地提高应用程序的可靠性，而不必告诉客户端应用程序应如何处理复杂模式或所有服务的部署位置。</span><span class="sxs-lookup"><span data-stu-id="eea7e-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="eea7e-105">语法</span><span class="sxs-lookup"><span data-stu-id="eea7e-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eea7e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="eea7e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="eea7e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eea7e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eea7e-108">特性</span><span class="sxs-lookup"><span data-stu-id="eea7e-108">Attributes</span></span>  

 <span data-ttu-id="eea7e-109">无。</span><span class="sxs-lookup"><span data-stu-id="eea7e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eea7e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="eea7e-110">Child Elements</span></span>  
  
|<span data-ttu-id="eea7e-111">元素</span><span class="sxs-lookup"><span data-stu-id="eea7e-111">Element</span></span>|<span data-ttu-id="eea7e-112">描述</span><span class="sxs-lookup"><span data-stu-id="eea7e-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="eea7e-113">包含当无法访问主终结点时路由服务将使用的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="eea7e-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="eea7e-114">.</span><span class="sxs-lookup"><span data-stu-id="eea7e-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eea7e-115">父元素</span><span class="sxs-lookup"><span data-stu-id="eea7e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="eea7e-116">元素</span><span class="sxs-lookup"><span data-stu-id="eea7e-116">Element</span></span>|<span data-ttu-id="eea7e-117">描述</span><span class="sxs-lookup"><span data-stu-id="eea7e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="eea7e-118">表示用于定义一组路由筛选器的配置节，这些筛选器确定计算传入消息时要使用的 Windows Communication Foundation 的类型 (WCF) ，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义筛选器匹配时要将消息发送到的目标终结点的路由表。</span><span class="sxs-lookup"><span data-stu-id="eea7e-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eea7e-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="eea7e-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
