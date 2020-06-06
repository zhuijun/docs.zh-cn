---
title: <dataContractSerializer><的>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398084"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="96006-102">\<dataContractSerializer> 的 \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="96006-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="96006-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="96006-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="96006-104">语法</span><span class="sxs-lookup"><span data-stu-id="96006-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96006-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="96006-105">Attributes and Elements</span></span>  
 <span data-ttu-id="96006-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="96006-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96006-107">特性</span><span class="sxs-lookup"><span data-stu-id="96006-107">Attributes</span></span>  
  
|<span data-ttu-id="96006-108">元素</span><span class="sxs-lookup"><span data-stu-id="96006-108">Element</span></span>|<span data-ttu-id="96006-109">说明</span><span class="sxs-lookup"><span data-stu-id="96006-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96006-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="96006-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="96006-111">一个布尔值，指定在对终结点进行序列化或反序列化时，是否要忽略由该终结点提供的数据。</span><span class="sxs-lookup"><span data-stu-id="96006-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="96006-112">只可对 `<dataContractSerializer>` 元素下的 `<behavior>` 设置此属性。</span><span class="sxs-lookup"><span data-stu-id="96006-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="96006-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="96006-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="96006-114">一个整数，指定要序列化或反序列化的最大项数。</span><span class="sxs-lookup"><span data-stu-id="96006-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="96006-115">此属性为 65536。</span><span class="sxs-lookup"><span data-stu-id="96006-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96006-116">子元素</span><span class="sxs-lookup"><span data-stu-id="96006-116">Child Elements</span></span>  
  
|<span data-ttu-id="96006-117">元素</span><span class="sxs-lookup"><span data-stu-id="96006-117">Element</span></span>|<span data-ttu-id="96006-118">说明</span><span class="sxs-lookup"><span data-stu-id="96006-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="96006-119">包含在进行反序列化时 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="96006-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="96006-120">有关数据协定和已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="96006-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96006-121">父元素</span><span class="sxs-lookup"><span data-stu-id="96006-121">Parent Elements</span></span>  
  
|<span data-ttu-id="96006-122">元素</span><span class="sxs-lookup"><span data-stu-id="96006-122">Element</span></span>|<span data-ttu-id="96006-123">说明</span><span class="sxs-lookup"><span data-stu-id="96006-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="96006-124">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="96006-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96006-125">注解</span><span class="sxs-lookup"><span data-stu-id="96006-125">Remarks</span></span>  
 <span data-ttu-id="96006-126">有关已知类型的详细信息，请参阅 <xref:System.Runtime.Serialization.DataContractSerializer> 和[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="96006-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96006-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96006-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="96006-128">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="96006-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
