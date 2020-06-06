---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850266"
---
# \<backupLists>
<span data-ttu-id="582d1-101">表示一个配置节，用于定义一组用来处理错误的备份服务。</span><span class="sxs-lookup"><span data-stu-id="582d1-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="582d1-102">每个子元素都是一个备份列表，用于枚举当无法到达主终结点时路由服务将使用的一组终结点。</span><span class="sxs-lookup"><span data-stu-id="582d1-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="582d1-103">如果列表中的第一个终结点关闭，则路由服务会自动故障转移到列表中的下一个终结点。</span><span class="sxs-lookup"><span data-stu-id="582d1-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="582d1-104">这样，可以方便地提高应用程序的可靠性，而不必告诉客户端应用程序应如何处理复杂模式或所有服务的部署位置。</span><span class="sxs-lookup"><span data-stu-id="582d1-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="582d1-105">语法</span><span class="sxs-lookup"><span data-stu-id="582d1-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="582d1-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="582d1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="582d1-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="582d1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="582d1-108">特性</span><span class="sxs-lookup"><span data-stu-id="582d1-108">Attributes</span></span>  
 <span data-ttu-id="582d1-109">无。</span><span class="sxs-lookup"><span data-stu-id="582d1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="582d1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="582d1-110">Child Elements</span></span>  
  
|<span data-ttu-id="582d1-111">元素</span><span class="sxs-lookup"><span data-stu-id="582d1-111">Element</span></span>|<span data-ttu-id="582d1-112">说明</span><span class="sxs-lookup"><span data-stu-id="582d1-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="582d1-113">包含当无法访问主终结点时路由服务将使用的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="582d1-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="582d1-114">.</span><span class="sxs-lookup"><span data-stu-id="582d1-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="582d1-115">父元素</span><span class="sxs-lookup"><span data-stu-id="582d1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="582d1-116">元素</span><span class="sxs-lookup"><span data-stu-id="582d1-116">Element</span></span>|<span data-ttu-id="582d1-117">说明</span><span class="sxs-lookup"><span data-stu-id="582d1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="582d1-118">表示用于定义一组路由筛选器的配置节，这些筛选器确定计算传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义在筛选器匹配时要将消息发送到的目标终结点的路由表。</span><span class="sxs-lookup"><span data-stu-id="582d1-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="582d1-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="582d1-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
