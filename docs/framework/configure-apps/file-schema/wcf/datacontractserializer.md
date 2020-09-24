---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0e4cbc50c25d4fa1f67f283f2b52d4b174428cd3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153919"
---
# <a name="datacontractserializer"></a><span data-ttu-id="97dec-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="97dec-102">dataContractSerializer</span></span>

<span data-ttu-id="97dec-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="97dec-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="97dec-104">语法</span><span class="sxs-lookup"><span data-stu-id="97dec-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97dec-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="97dec-105">Attributes and Elements</span></span>  

 <span data-ttu-id="97dec-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="97dec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97dec-107">特性</span><span class="sxs-lookup"><span data-stu-id="97dec-107">Attributes</span></span>  
  
|<span data-ttu-id="97dec-108">元素</span><span class="sxs-lookup"><span data-stu-id="97dec-108">Element</span></span>|<span data-ttu-id="97dec-109">描述</span><span class="sxs-lookup"><span data-stu-id="97dec-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97dec-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="97dec-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="97dec-111">一个布尔值，指定在对终结点进行序列化或反序列化时，是否要忽略由该终结点提供的数据。</span><span class="sxs-lookup"><span data-stu-id="97dec-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="97dec-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="97dec-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="97dec-113">一个整数，指定要序列化或反序列化的最大项数。</span><span class="sxs-lookup"><span data-stu-id="97dec-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97dec-114">子元素</span><span class="sxs-lookup"><span data-stu-id="97dec-114">Child Elements</span></span>  

 <span data-ttu-id="97dec-115">无。</span><span class="sxs-lookup"><span data-stu-id="97dec-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97dec-116">父元素</span><span class="sxs-lookup"><span data-stu-id="97dec-116">Parent Elements</span></span>  
  
|<span data-ttu-id="97dec-117">元素</span><span class="sxs-lookup"><span data-stu-id="97dec-117">Element</span></span>|<span data-ttu-id="97dec-118">描述</span><span class="sxs-lookup"><span data-stu-id="97dec-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="97dec-119">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="97dec-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97dec-120">备注</span><span class="sxs-lookup"><span data-stu-id="97dec-120">Remarks</span></span>  

 <span data-ttu-id="97dec-121">有关已知类型的更多信息，请参见 <xref:System.Runtime.Serialization.DataContractSerializer> 文档。</span><span class="sxs-lookup"><span data-stu-id="97dec-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="97dec-122">在配置文件中，`<dataContractSerializer>` 行为元素（如果有）应始终在 `<enableWebScript>` 行为元素之前出现。</span><span class="sxs-lookup"><span data-stu-id="97dec-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="97dec-123">否则，产生的行为将是不确定的。</span><span class="sxs-lookup"><span data-stu-id="97dec-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97dec-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="97dec-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="97dec-125">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="97dec-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="97dec-126">数据传输和序列化</span><span class="sxs-lookup"><span data-stu-id="97dec-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
