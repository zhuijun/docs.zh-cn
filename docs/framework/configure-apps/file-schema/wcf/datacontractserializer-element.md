---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 2a994a8ba97d4c65fdaba5a85e779dd9935e3074
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195022"
---
# \<dataContractSerializer>

<span data-ttu-id="aae81-101">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="aae81-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="aae81-102">此元素出现在两个不同的层次结构中。</span><span class="sxs-lookup"><span data-stu-id="aae81-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="aae81-103">这两个层次结构分别在下面的“架构层次结构”一节和“备注”一节中列出。</span><span class="sxs-lookup"><span data-stu-id="aae81-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="aae81-104">语法</span><span class="sxs-lookup"><span data-stu-id="aae81-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aae81-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="aae81-105">Attributes and Elements</span></span>  

 <span data-ttu-id="aae81-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aae81-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aae81-107">特性</span><span class="sxs-lookup"><span data-stu-id="aae81-107">Attributes</span></span>  
  
|<span data-ttu-id="aae81-108">元素</span><span class="sxs-lookup"><span data-stu-id="aae81-108">Element</span></span>|<span data-ttu-id="aae81-109">描述</span><span class="sxs-lookup"><span data-stu-id="aae81-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aae81-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="aae81-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="aae81-111">一个布尔值，指定在对终结点进行序列化或反序列化时，是否要忽略由该终结点提供的数据。</span><span class="sxs-lookup"><span data-stu-id="aae81-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="aae81-112">只可对 `<dataContractSerializer>` 元素下的 `<behavior>` 设置此属性。</span><span class="sxs-lookup"><span data-stu-id="aae81-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="aae81-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="aae81-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="aae81-114">一个整数，指定要序列化或反序列化的最大项数。</span><span class="sxs-lookup"><span data-stu-id="aae81-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="aae81-115">此属性为 65536。</span><span class="sxs-lookup"><span data-stu-id="aae81-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aae81-116">子元素</span><span class="sxs-lookup"><span data-stu-id="aae81-116">Child Elements</span></span>  

 <span data-ttu-id="aae81-117">无。</span><span class="sxs-lookup"><span data-stu-id="aae81-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aae81-118">父元素</span><span class="sxs-lookup"><span data-stu-id="aae81-118">Parent Elements</span></span>  
  
|<span data-ttu-id="aae81-119">元素</span><span class="sxs-lookup"><span data-stu-id="aae81-119">Element</span></span>|<span data-ttu-id="aae81-120">描述</span><span class="sxs-lookup"><span data-stu-id="aae81-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="aae81-121">服务行为的设置集合。</span><span class="sxs-lookup"><span data-stu-id="aae81-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="aae81-122">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="aae81-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aae81-123">备注</span><span class="sxs-lookup"><span data-stu-id="aae81-123">Remarks</span></span>  

 <span data-ttu-id="aae81-124">如本主题的简介中所述，这是在其中发生元素的第二个层次结构 \<X509Extension> 。</span><span class="sxs-lookup"><span data-stu-id="aae81-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="aae81-125">有关已知类型的更多信息，请参见 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="aae81-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae81-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="aae81-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="aae81-127">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="aae81-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="aae81-128">数据传输和序列化</span><span class="sxs-lookup"><span data-stu-id="aae81-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
