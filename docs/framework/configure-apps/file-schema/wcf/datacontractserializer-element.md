---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400453"
---
# \<dataContractSerializer>
<span data-ttu-id="47b9d-101">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="47b9d-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="47b9d-102">此元素出现在两个不同的层次结构中。</span><span class="sxs-lookup"><span data-stu-id="47b9d-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="47b9d-103">这两个层次结构分别在下面的“架构层次结构”一节和“备注”一节中列出。</span><span class="sxs-lookup"><span data-stu-id="47b9d-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="47b9d-104">语法</span><span class="sxs-lookup"><span data-stu-id="47b9d-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47b9d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="47b9d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="47b9d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="47b9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47b9d-107">特性</span><span class="sxs-lookup"><span data-stu-id="47b9d-107">Attributes</span></span>  
  
|<span data-ttu-id="47b9d-108">元素</span><span class="sxs-lookup"><span data-stu-id="47b9d-108">Element</span></span>|<span data-ttu-id="47b9d-109">说明</span><span class="sxs-lookup"><span data-stu-id="47b9d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47b9d-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="47b9d-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="47b9d-111">一个布尔值，指定在对终结点进行序列化或反序列化时，是否要忽略由该终结点提供的数据。</span><span class="sxs-lookup"><span data-stu-id="47b9d-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="47b9d-112">只可对 `<dataContractSerializer>` 元素下的 `<behavior>` 设置此属性。</span><span class="sxs-lookup"><span data-stu-id="47b9d-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="47b9d-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="47b9d-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="47b9d-114">一个整数，指定要序列化或反序列化的最大项数。</span><span class="sxs-lookup"><span data-stu-id="47b9d-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="47b9d-115">此属性为 65536。</span><span class="sxs-lookup"><span data-stu-id="47b9d-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47b9d-116">子元素</span><span class="sxs-lookup"><span data-stu-id="47b9d-116">Child Elements</span></span>  
 <span data-ttu-id="47b9d-117">无。</span><span class="sxs-lookup"><span data-stu-id="47b9d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47b9d-118">父元素</span><span class="sxs-lookup"><span data-stu-id="47b9d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="47b9d-119">元素</span><span class="sxs-lookup"><span data-stu-id="47b9d-119">Element</span></span>|<span data-ttu-id="47b9d-120">说明</span><span class="sxs-lookup"><span data-stu-id="47b9d-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="47b9d-121">服务行为的设置集合。</span><span class="sxs-lookup"><span data-stu-id="47b9d-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="47b9d-122">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="47b9d-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47b9d-123">注解</span><span class="sxs-lookup"><span data-stu-id="47b9d-123">Remarks</span></span>  
 <span data-ttu-id="47b9d-124">如本主题的简介中所述，这是在其中发生元素的第二个层次结构 \<X509Extension> 。</span><span class="sxs-lookup"><span data-stu-id="47b9d-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="47b9d-125">有关已知类型的更多信息，请参见 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="47b9d-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b9d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47b9d-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="47b9d-127">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="47b9d-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="47b9d-128">数据传输和序列化</span><span class="sxs-lookup"><span data-stu-id="47b9d-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
