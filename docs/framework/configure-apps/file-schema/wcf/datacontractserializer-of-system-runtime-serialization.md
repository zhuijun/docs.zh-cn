---
title: <dataContractSerializer> <的>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: a8d379e7a37bca0cdb58836a6afdf814320e2411
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190184"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="85c85-102">\<dataContractSerializer> 的 \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="85c85-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="85c85-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="85c85-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="85c85-104">语法</span><span class="sxs-lookup"><span data-stu-id="85c85-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85c85-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="85c85-105">Attributes and Elements</span></span>  

 <span data-ttu-id="85c85-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85c85-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85c85-107">特性</span><span class="sxs-lookup"><span data-stu-id="85c85-107">Attributes</span></span>  
  
|<span data-ttu-id="85c85-108">元素</span><span class="sxs-lookup"><span data-stu-id="85c85-108">Element</span></span>|<span data-ttu-id="85c85-109">描述</span><span class="sxs-lookup"><span data-stu-id="85c85-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85c85-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="85c85-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="85c85-111">一个布尔值，指定在对终结点进行序列化或反序列化时，是否要忽略由该终结点提供的数据。</span><span class="sxs-lookup"><span data-stu-id="85c85-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="85c85-112">只可对 `<dataContractSerializer>` 元素下的 `<behavior>` 设置此属性。</span><span class="sxs-lookup"><span data-stu-id="85c85-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="85c85-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="85c85-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="85c85-114">一个整数，指定要序列化或反序列化的最大项数。</span><span class="sxs-lookup"><span data-stu-id="85c85-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="85c85-115">此属性为 65536。</span><span class="sxs-lookup"><span data-stu-id="85c85-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85c85-116">子元素</span><span class="sxs-lookup"><span data-stu-id="85c85-116">Child Elements</span></span>  
  
|<span data-ttu-id="85c85-117">元素</span><span class="sxs-lookup"><span data-stu-id="85c85-117">Element</span></span>|<span data-ttu-id="85c85-118">描述</span><span class="sxs-lookup"><span data-stu-id="85c85-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="85c85-119">包含在进行反序列化时 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="85c85-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="85c85-120">有关数据协定和已知类型的详细信息，请参阅 [数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="85c85-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85c85-121">父元素</span><span class="sxs-lookup"><span data-stu-id="85c85-121">Parent Elements</span></span>  
  
|<span data-ttu-id="85c85-122">元素</span><span class="sxs-lookup"><span data-stu-id="85c85-122">Element</span></span>|<span data-ttu-id="85c85-123">描述</span><span class="sxs-lookup"><span data-stu-id="85c85-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="85c85-124">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="85c85-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85c85-125">备注</span><span class="sxs-lookup"><span data-stu-id="85c85-125">Remarks</span></span>  

 <span data-ttu-id="85c85-126">有关已知类型的详细信息，请参阅 <xref:System.Runtime.Serialization.DataContractSerializer> 和 [数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="85c85-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c85-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="85c85-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="85c85-128">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="85c85-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
