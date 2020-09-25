---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 2ef674dc8601bc9afaf6b547265988bb8a99f943
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170163"
---
# \<parameter>

<span data-ttu-id="6de0f-101">指定当声明类型是泛型类型时的泛型参数。</span><span class="sxs-lookup"><span data-stu-id="6de0f-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="6de0f-102">语法</span><span class="sxs-lookup"><span data-stu-id="6de0f-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6de0f-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6de0f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6de0f-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6de0f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6de0f-105">特性</span><span class="sxs-lookup"><span data-stu-id="6de0f-105">Attributes</span></span>  
  
|<span data-ttu-id="6de0f-106">属性</span><span class="sxs-lookup"><span data-stu-id="6de0f-106">Attribute</span></span>|<span data-ttu-id="6de0f-107">说明</span><span class="sxs-lookup"><span data-stu-id="6de0f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6de0f-108">索引</span><span class="sxs-lookup"><span data-stu-id="6de0f-108">index</span></span>|<span data-ttu-id="6de0f-109">当声明类型是泛型类型时，指定将返回已知类型的泛型参数。</span><span class="sxs-lookup"><span data-stu-id="6de0f-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="6de0f-110">type</span><span class="sxs-lookup"><span data-stu-id="6de0f-110">type</span></span>|<span data-ttu-id="6de0f-111">一个字符串，描述用于序列化和反序列化的已知类型。</span><span class="sxs-lookup"><span data-stu-id="6de0f-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="6de0f-112">index 特性</span><span class="sxs-lookup"><span data-stu-id="6de0f-112">index Attribute</span></span>  
  
|<span data-ttu-id="6de0f-113">值</span><span class="sxs-lookup"><span data-stu-id="6de0f-113">Value</span></span>|<span data-ttu-id="6de0f-114">描述</span><span class="sxs-lookup"><span data-stu-id="6de0f-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6de0f-115">"0"</span><span class="sxs-lookup"><span data-stu-id="6de0f-115">"0"</span></span>|<span data-ttu-id="6de0f-116">泛型类型中的第一个参数。</span><span class="sxs-lookup"><span data-stu-id="6de0f-116">The first parameter in the generic type.</span></span> <span data-ttu-id="6de0f-117">例如，一个 <xref:System.Collections.Generic.List%601> 仅有一个参数。</span><span class="sxs-lookup"><span data-stu-id="6de0f-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="6de0f-118">如果此参数用作声明类型，则将 index 特性设置为“0”。</span><span class="sxs-lookup"><span data-stu-id="6de0f-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="6de0f-119">"1"</span><span class="sxs-lookup"><span data-stu-id="6de0f-119">"1"</span></span>|<span data-ttu-id="6de0f-120">泛型类型中的第二个参数。</span><span class="sxs-lookup"><span data-stu-id="6de0f-120">The second parameter in a generic type.</span></span> <span data-ttu-id="6de0f-121">例如，一个 <xref:System.Collections.Generic.Dictionary%602> 有两个参数。</span><span class="sxs-lookup"><span data-stu-id="6de0f-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="6de0f-122">如果通过第二个参数返回已知类型，则将 index 特性设置为“1”。</span><span class="sxs-lookup"><span data-stu-id="6de0f-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6de0f-123">子元素</span><span class="sxs-lookup"><span data-stu-id="6de0f-123">Child Elements</span></span>  

 <span data-ttu-id="6de0f-124">无。</span><span class="sxs-lookup"><span data-stu-id="6de0f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6de0f-125">父元素</span><span class="sxs-lookup"><span data-stu-id="6de0f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6de0f-126">元素</span><span class="sxs-lookup"><span data-stu-id="6de0f-126">Element</span></span>|<span data-ttu-id="6de0f-127">描述</span><span class="sxs-lookup"><span data-stu-id="6de0f-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="6de0f-128">指定一个可由声明类型的字段或属性返回的已知类型。</span><span class="sxs-lookup"><span data-stu-id="6de0f-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6de0f-129">备注</span><span class="sxs-lookup"><span data-stu-id="6de0f-129">Remarks</span></span>  

 <span data-ttu-id="6de0f-130">有关已知类型的详细信息，请参阅 [数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md) 和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="6de0f-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6de0f-131">[\<dataContractSerializer>](datacontractserializer-element.md)有关使用此元素的示例，请参见。</span><span class="sxs-lookup"><span data-stu-id="6de0f-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="6de0f-132">此配置元素不能同时具有两个属性。</span><span class="sxs-lookup"><span data-stu-id="6de0f-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="6de0f-133">如果设置两个属性，则发生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="6de0f-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de0f-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="6de0f-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="6de0f-135">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="6de0f-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
