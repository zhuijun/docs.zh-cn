---
title: <add> of <declaredTypes> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9af47848b03074ec88f38a5884089bc50239ee50
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201663"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="e8131-102">\<add> of \<declaredTypes> 元素</span><span class="sxs-lookup"><span data-stu-id="e8131-102">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="e8131-103">添加在反序列化过程中由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的类型。</span><span class="sxs-lookup"><span data-stu-id="e8131-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="e8131-104">每个声明类型都包含一些将作为声明类型的字段或属性返回的已知类型。</span><span class="sxs-lookup"><span data-stu-id="e8131-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e8131-105">语法</span><span class="sxs-lookup"><span data-stu-id="e8131-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8131-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e8131-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e8131-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e8131-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8131-108">特性</span><span class="sxs-lookup"><span data-stu-id="e8131-108">Attributes</span></span>  
  
|<span data-ttu-id="e8131-109">属性</span><span class="sxs-lookup"><span data-stu-id="e8131-109">Attribute</span></span>|<span data-ttu-id="e8131-110">说明</span><span class="sxs-lookup"><span data-stu-id="e8131-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8131-111">type</span><span class="sxs-lookup"><span data-stu-id="e8131-111">type</span></span>|<span data-ttu-id="e8131-112">必需的字符串属性。</span><span class="sxs-lookup"><span data-stu-id="e8131-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="e8131-113">指定类型名称（包括命名空间）、程序集名称、版本号、区域性和公钥标记。</span><span class="sxs-lookup"><span data-stu-id="e8131-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8131-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e8131-114">Child Elements</span></span>  
  
|<span data-ttu-id="e8131-115">元素</span><span class="sxs-lookup"><span data-stu-id="e8131-115">Element</span></span>|<span data-ttu-id="e8131-116">描述</span><span class="sxs-lookup"><span data-stu-id="e8131-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="e8131-117">指定要添加的声明类型的已知类型。</span><span class="sxs-lookup"><span data-stu-id="e8131-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="e8131-118">如果声明类型是泛型类型，则还必须向 `<knownType>` 元素添加一个参数元素，以指定用于返回已知类型的泛型参数。</span><span class="sxs-lookup"><span data-stu-id="e8131-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8131-119">父元素</span><span class="sxs-lookup"><span data-stu-id="e8131-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e8131-120">元素</span><span class="sxs-lookup"><span data-stu-id="e8131-120">Element</span></span>|<span data-ttu-id="e8131-121">描述</span><span class="sxs-lookup"><span data-stu-id="e8131-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="e8131-122">包含在 <xref:System.Runtime.Serialization.DataContractSerializer> 进行反序列化过程中需要已知类型的类型。</span><span class="sxs-lookup"><span data-stu-id="e8131-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8131-123">备注</span><span class="sxs-lookup"><span data-stu-id="e8131-123">Remarks</span></span>  

 <span data-ttu-id="e8131-124">有关已知类型的详细信息，请参阅 [数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md) 和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="e8131-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e8131-125">[\<dataContractSerializer>](datacontractserializer-element.md)有关使用此元素的示例，请参见。</span><span class="sxs-lookup"><span data-stu-id="e8131-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8131-126">如果将 <xref:System.Object> 类型添加为 `<declaredType>`，则会引发 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="e8131-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="e8131-127">这是因为，<xref:System.Object> 类型不能在配置中用作声明的类型。</span><span class="sxs-lookup"><span data-stu-id="e8131-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8131-128">示例</span><span class="sxs-lookup"><span data-stu-id="e8131-128">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="e8131-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8131-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="e8131-130">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="e8131-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="e8131-131">\<declaredTypes> 的 \<add></span><span class="sxs-lookup"><span data-stu-id="e8131-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
