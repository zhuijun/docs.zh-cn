---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397872"
---
# \<knownType>
<span data-ttu-id="f0d71-101">指定在反序列化过程中将由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的类型。</span><span class="sxs-lookup"><span data-stu-id="f0d71-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="f0d71-102">该元素指定由某个“声明的类型”的字段或属性返回到“已知类型”。</span><span class="sxs-lookup"><span data-stu-id="f0d71-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="f0d71-103">有关详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d71-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="f0d71-104">语法</span><span class="sxs-lookup"><span data-stu-id="f0d71-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="f0d71-105">类型</span><span class="sxs-lookup"><span data-stu-id="f0d71-105">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0d71-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f0d71-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f0d71-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f0d71-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0d71-108">特性</span><span class="sxs-lookup"><span data-stu-id="f0d71-108">Attributes</span></span>  
  
|<span data-ttu-id="f0d71-109">属性</span><span class="sxs-lookup"><span data-stu-id="f0d71-109">Attribute</span></span>|<span data-ttu-id="f0d71-110">说明</span><span class="sxs-lookup"><span data-stu-id="f0d71-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0d71-111">type</span><span class="sxs-lookup"><span data-stu-id="f0d71-111">type</span></span>|<span data-ttu-id="f0d71-112">指定类型（包括命名空间）、程序集名称、版本、区域性和公钥标记。</span><span class="sxs-lookup"><span data-stu-id="f0d71-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0d71-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f0d71-113">Child Elements</span></span>  
  
|<span data-ttu-id="f0d71-114">元素</span><span class="sxs-lookup"><span data-stu-id="f0d71-114">Element</span></span>|<span data-ttu-id="f0d71-115">描述</span><span class="sxs-lookup"><span data-stu-id="f0d71-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="f0d71-116">当声明类型为泛型类型时指定参数索引。</span><span class="sxs-lookup"><span data-stu-id="f0d71-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0d71-117">父元素</span><span class="sxs-lookup"><span data-stu-id="f0d71-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f0d71-118">元素</span><span class="sxs-lookup"><span data-stu-id="f0d71-118">Element</span></span>|<span data-ttu-id="f0d71-119">描述</span><span class="sxs-lookup"><span data-stu-id="f0d71-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="f0d71-120">向声明类型的集合中添加一个声明类型。</span><span class="sxs-lookup"><span data-stu-id="f0d71-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0d71-121">注解</span><span class="sxs-lookup"><span data-stu-id="f0d71-121">Remarks</span></span>  
 <span data-ttu-id="f0d71-122">有关已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="f0d71-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f0d71-123">[\<dataContractSerializer>](datacontractserializer-element.md)有关使用此元素的示例，请参见。</span><span class="sxs-lookup"><span data-stu-id="f0d71-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d71-124">示例</span><span class="sxs-lookup"><span data-stu-id="f0d71-124">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="f0d71-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0d71-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="f0d71-126">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="f0d71-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
