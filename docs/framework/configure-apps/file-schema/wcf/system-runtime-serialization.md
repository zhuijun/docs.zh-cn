---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152965"
---
# \<system.runtime.serialization>
<span data-ttu-id="0a6e3-102">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="0a6e3-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="0a6e3-103">语法</span><span class="sxs-lookup"><span data-stu-id="0a6e3-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a6e3-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0a6e3-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0a6e3-105">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0a6e3-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a6e3-106">特性</span><span class="sxs-lookup"><span data-stu-id="0a6e3-106">Attributes</span></span>  
 <span data-ttu-id="0a6e3-107">无。</span><span class="sxs-lookup"><span data-stu-id="0a6e3-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0a6e3-108">子元素</span><span class="sxs-lookup"><span data-stu-id="0a6e3-108">Child Elements</span></span>  
  
|<span data-ttu-id="0a6e3-109">元素</span><span class="sxs-lookup"><span data-stu-id="0a6e3-109">Element</span></span>|<span data-ttu-id="0a6e3-110">说明</span><span class="sxs-lookup"><span data-stu-id="0a6e3-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="0a6e3-111">使得可以在反序列化时添加要使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="0a6e3-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a6e3-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0a6e3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0a6e3-113">元素</span><span class="sxs-lookup"><span data-stu-id="0a6e3-113">Element</span></span>|<span data-ttu-id="0a6e3-114">说明</span><span class="sxs-lookup"><span data-stu-id="0a6e3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a6e3-115">\<configuration>Element</span><span class="sxs-lookup"><span data-stu-id="0a6e3-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="0a6e3-116">配置的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="0a6e3-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a6e3-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a6e3-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="0a6e3-118">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="0a6e3-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="0a6e3-119">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="0a6e3-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
