---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399962"
---
# \<routing>

<span data-ttu-id="bfeb2-101">表示用于定义一组路由筛选器的配置节，这些筛选器确定计算传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义在筛选器匹配时要将消息发送到的目标终结点的路由表。</span><span class="sxs-lookup"><span data-stu-id="bfeb2-101">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="bfeb2-102">语法</span><span class="sxs-lookup"><span data-stu-id="bfeb2-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfeb2-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bfeb2-103">Attributes and elements</span></span>

<span data-ttu-id="bfeb2-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bfeb2-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfeb2-105">特性</span><span class="sxs-lookup"><span data-stu-id="bfeb2-105">Attributes</span></span>

<span data-ttu-id="bfeb2-106">无</span><span class="sxs-lookup"><span data-stu-id="bfeb2-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfeb2-107">子元素</span><span class="sxs-lookup"><span data-stu-id="bfeb2-107">Child elements</span></span>

|     | <span data-ttu-id="bfeb2-108">说明</span><span class="sxs-lookup"><span data-stu-id="bfeb2-108">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="bfeb2-109">包含一组路由筛选器，用于确定在计算传入消息时将使用的 Windows Communication Foundation （WCF） MessageFilter 的类型。</span><span class="sxs-lookup"><span data-stu-id="bfeb2-109">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="bfeb2-110">包含路由筛选器和目标终结点之间的映射，以便指定在筛选器匹配时使用的终结点。</span><span class="sxs-lookup"><span data-stu-id="bfeb2-110">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="bfeb2-111">父元素</span><span class="sxs-lookup"><span data-stu-id="bfeb2-111">Parent elements</span></span>

|     | <span data-ttu-id="bfeb2-112">说明</span><span class="sxs-lookup"><span data-stu-id="bfeb2-112">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="bfeb2-113">所有 WCF 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="bfeb2-113">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="bfeb2-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bfeb2-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
