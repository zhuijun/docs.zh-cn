---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 84ced06691ce3b3c9c9573fc9d114335096a849d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157104"
---
# \<system.runtime.serialization>

<span data-ttu-id="d10d6-102">表示 <xref:System.Runtime.Serialization> 命名空间节的根元素，并包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的设置选项的元素。</span><span class="sxs-lookup"><span data-stu-id="d10d6-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="d10d6-103">语法</span><span class="sxs-lookup"><span data-stu-id="d10d6-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d10d6-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d10d6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d10d6-105">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d10d6-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d10d6-106">特性</span><span class="sxs-lookup"><span data-stu-id="d10d6-106">Attributes</span></span>  

 <span data-ttu-id="d10d6-107">无。</span><span class="sxs-lookup"><span data-stu-id="d10d6-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d10d6-108">子元素</span><span class="sxs-lookup"><span data-stu-id="d10d6-108">Child Elements</span></span>  
  
|<span data-ttu-id="d10d6-109">元素</span><span class="sxs-lookup"><span data-stu-id="d10d6-109">Element</span></span>|<span data-ttu-id="d10d6-110">描述</span><span class="sxs-lookup"><span data-stu-id="d10d6-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="d10d6-111">使得可以在反序列化时添加要使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="d10d6-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d10d6-112">父元素</span><span class="sxs-lookup"><span data-stu-id="d10d6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d10d6-113">元素</span><span class="sxs-lookup"><span data-stu-id="d10d6-113">Element</span></span>|<span data-ttu-id="d10d6-114">描述</span><span class="sxs-lookup"><span data-stu-id="d10d6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d10d6-115">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="d10d6-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="d10d6-116">配置的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="d10d6-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d10d6-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="d10d6-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="d10d6-118">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="d10d6-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="d10d6-119">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="d10d6-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
