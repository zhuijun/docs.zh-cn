---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855096"
---
# \<namespaceTable>

<span data-ttu-id="5def3-101">表示用于定义一组元素的配置节，这些元素包含随后可在 XPath 筛选器中用于路由的前缀映射的命名空间。</span><span class="sxs-lookup"><span data-stu-id="5def3-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="5def3-102">语法</span><span class="sxs-lookup"><span data-stu-id="5def3-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5def3-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5def3-103">Attributes and elements</span></span>

<span data-ttu-id="5def3-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5def3-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5def3-105">特性</span><span class="sxs-lookup"><span data-stu-id="5def3-105">Attributes</span></span>

<span data-ttu-id="5def3-106">无</span><span class="sxs-lookup"><span data-stu-id="5def3-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="5def3-107">子元素</span><span class="sxs-lookup"><span data-stu-id="5def3-107">Child elements</span></span>

|     | <span data-ttu-id="5def3-108">说明</span><span class="sxs-lookup"><span data-stu-id="5def3-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="5def3-109">定义用于 XPath 表达式的命名空间前缀映射。</span><span class="sxs-lookup"><span data-stu-id="5def3-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="5def3-110">父元素</span><span class="sxs-lookup"><span data-stu-id="5def3-110">Parent elements</span></span>

|     | <span data-ttu-id="5def3-111">说明</span><span class="sxs-lookup"><span data-stu-id="5def3-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="5def3-112">表示用于定义一组路由筛选器的配置节，这些筛选器确定计算传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义在筛选器匹配时要将消息发送到的目标终结点的路由表。</span><span class="sxs-lookup"><span data-stu-id="5def3-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="5def3-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5def3-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
