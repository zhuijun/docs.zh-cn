---
title: <filters> 的 <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855247"
---
# <a name="filters-of-routing"></a><span data-ttu-id="85a3f-102">\<filters> 的 \<routing></span><span class="sxs-lookup"><span data-stu-id="85a3f-102">\<filters> of \<routing></span></span>

<span data-ttu-id="85a3f-103">表示用于定义一组路由筛选器的配置节，这些筛选器确定 <xref:System.ServiceModel.Dispatcher.MessageFilter> 计算传入消息时使用的 Windows Communication Foundation （WCF）的类型。</span><span class="sxs-lookup"><span data-stu-id="85a3f-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="85a3f-104">语法</span><span class="sxs-lookup"><span data-stu-id="85a3f-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85a3f-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="85a3f-105">Attributes and elements</span></span>

<span data-ttu-id="85a3f-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85a3f-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="85a3f-107">特性</span><span class="sxs-lookup"><span data-stu-id="85a3f-107">Attributes</span></span>

<span data-ttu-id="85a3f-108">无</span><span class="sxs-lookup"><span data-stu-id="85a3f-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="85a3f-109">子元素</span><span class="sxs-lookup"><span data-stu-id="85a3f-109">Child elements</span></span>

|     | <span data-ttu-id="85a3f-110">说明</span><span class="sxs-lookup"><span data-stu-id="85a3f-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="85a3f-111">包含一个路由筛选器，该筛选器确定 <xref:System.ServiceModel.Dispatcher.MessageFilter> 计算传入消息时将使用的 Windows Communication Foundation （WCF）的类型。</span><span class="sxs-lookup"><span data-stu-id="85a3f-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="85a3f-112">父元素</span><span class="sxs-lookup"><span data-stu-id="85a3f-112">Parent elements</span></span>

|     | <span data-ttu-id="85a3f-113">说明</span><span class="sxs-lookup"><span data-stu-id="85a3f-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="85a3f-114">表示用于定义一组路由筛选器的配置节，这些筛选器确定计算传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义在筛选器匹配时要将消息发送到的目标终结点的路由表。</span><span class="sxs-lookup"><span data-stu-id="85a3f-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="85a3f-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85a3f-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
