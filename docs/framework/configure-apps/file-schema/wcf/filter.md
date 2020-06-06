---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855258"
---
# \<filter>

<span data-ttu-id="343d2-101">定义一个路由筛选器，该筛选器确定 <xref:System.ServiceModel.Dispatcher.MessageFilter> 要在评估传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及筛选器所需的任何支持数据或参数。</span><span class="sxs-lookup"><span data-stu-id="343d2-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="343d2-102">语法</span><span class="sxs-lookup"><span data-stu-id="343d2-102">Syntax</span></span>  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="343d2-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="343d2-103">Attributes and elements</span></span>

<span data-ttu-id="343d2-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="343d2-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="343d2-105">特性</span><span class="sxs-lookup"><span data-stu-id="343d2-105">Attributes</span></span>

| <span data-ttu-id="343d2-106">属性</span><span class="sxs-lookup"><span data-stu-id="343d2-106">Attribute</span></span>  | <span data-ttu-id="343d2-107">说明</span><span class="sxs-lookup"><span data-stu-id="343d2-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="343d2-108">customType</span><span class="sxs-lookup"><span data-stu-id="343d2-108">customType</span></span> | <span data-ttu-id="343d2-109">一个字符串，包含要用作筛选器的自定义类型的完全限定类型名称。</span><span class="sxs-lookup"><span data-stu-id="343d2-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="343d2-110">如果 `filterType` 设置为 `custom` ，则此特性包含要创建的类的完全限定类型名称。</span><span class="sxs-lookup"><span data-stu-id="343d2-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="343d2-111">`filterData`还可以包含在计算自定义类型筛选器的过程中要使用的值。</span><span class="sxs-lookup"><span data-stu-id="343d2-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="343d2-112">filterData</span><span class="sxs-lookup"><span data-stu-id="343d2-112">filterData</span></span> | <span data-ttu-id="343d2-113">一个包含筛选器数据的字符串。</span><span class="sxs-lookup"><span data-stu-id="343d2-113">A string containing the filter data.</span></span> <span data-ttu-id="343d2-114">有关如何指定此特性的更多信息，请参见 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="343d2-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="343d2-115">filterType</span><span class="sxs-lookup"><span data-stu-id="343d2-115">filterType</span></span> | <span data-ttu-id="343d2-116">一个包含筛选器类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="343d2-116">A string containing the filter type.</span></span> <span data-ttu-id="343d2-117">此特性的类型为 <xref:System.ServiceModel.Routing.Configuration.FilterType>。</span><span class="sxs-lookup"><span data-stu-id="343d2-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="343d2-118">有关如何使用此 `filterData` 特性的更多信息，请参见 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="343d2-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="343d2-119">NAME</span><span class="sxs-lookup"><span data-stu-id="343d2-119">name</span></span>       | <span data-ttu-id="343d2-120">一个字符串，包含此筛选器元素的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="343d2-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="343d2-121">子元素</span><span class="sxs-lookup"><span data-stu-id="343d2-121">Child elements</span></span>

<span data-ttu-id="343d2-122">无。</span><span class="sxs-lookup"><span data-stu-id="343d2-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="343d2-123">父元素</span><span class="sxs-lookup"><span data-stu-id="343d2-123">Parent elements</span></span>

| <span data-ttu-id="343d2-124">元素</span><span class="sxs-lookup"><span data-stu-id="343d2-124">Element</span></span> | <span data-ttu-id="343d2-125">描述</span><span class="sxs-lookup"><span data-stu-id="343d2-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="343d2-126">用于定义一组路由筛选器的配置节，这些筛选器确定 <xref:System.ServiceModel.Dispatcher.MessageFilter> 计算传入消息时使用的 Windows Communication Foundation （WCF）的类型。</span><span class="sxs-lookup"><span data-stu-id="343d2-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="343d2-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="343d2-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
