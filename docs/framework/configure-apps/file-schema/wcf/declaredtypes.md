---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398053"
---
# \<declaredTypes>
<span data-ttu-id="dbe6b-101">包含在进行反序列化时 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知类型。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="dbe6b-102">有关数据协定和已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="dbe6b-103">语法</span><span class="sxs-lookup"><span data-stu-id="dbe6b-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbe6b-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dbe6b-104">Attributes and Elements</span></span>  
 <span data-ttu-id="dbe6b-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbe6b-106">特性</span><span class="sxs-lookup"><span data-stu-id="dbe6b-106">Attributes</span></span>  
 <span data-ttu-id="dbe6b-107">无。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dbe6b-108">子元素</span><span class="sxs-lookup"><span data-stu-id="dbe6b-108">Child Elements</span></span>  
  
|<span data-ttu-id="dbe6b-109">元素</span><span class="sxs-lookup"><span data-stu-id="dbe6b-109">Element</span></span>|<span data-ttu-id="dbe6b-110">说明</span><span class="sxs-lookup"><span data-stu-id="dbe6b-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="dbe6b-111">添加需要已知类型的类型。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbe6b-112">父元素</span><span class="sxs-lookup"><span data-stu-id="dbe6b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="dbe6b-113">元素</span><span class="sxs-lookup"><span data-stu-id="dbe6b-113">Element</span></span>|<span data-ttu-id="dbe6b-114">说明</span><span class="sxs-lookup"><span data-stu-id="dbe6b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="dbe6b-115">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe6b-116">注解</span><span class="sxs-lookup"><span data-stu-id="dbe6b-116">Remarks</span></span>  
 <span data-ttu-id="dbe6b-117">有关已知类型的详细信息，请参阅[数据协定已知类型](../../../wcf/feature-details/data-contract-known-types.md)和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbe6b-118">示例</span><span class="sxs-lookup"><span data-stu-id="dbe6b-118">Example</span></span>  
 <span data-ttu-id="dbe6b-119">以下 XML 代码显示了已声明的类型和添加到元素的已知类型 `DataContractSerializer` 。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="dbe6b-120">此示例演示要添加的三个类型。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-120">The example shows three types being added.</span></span> <span data-ttu-id="dbe6b-121">第一个类型是名为“Orders”的自定义类型，它使用一个名为“Item”的已知类型。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="dbe6b-122">第二个声明类型 <xref:System.Collections.Generic.List%601>，它使用 `Item` 作为已知类型。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="dbe6b-123">最后，第三个声明类型是 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="dbe6b-124"><xref:System.Collections.Generic.Dictionary%602> 类类型是泛型类型，并带有两个类型参数。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="dbe6b-125">第一个参数表示键，第二个参数表示值。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="dbe6b-126">下面的示例将第二个类型的 <xref:System.Collections.Generic.List%601>（值）添加到已知类型的列表中。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="dbe6b-127">必须使用 `index` 属性来指定在已知类型中使用的类型参数。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="dbe6b-128">在此例中，通过将 index 属性设置为“1”（基于零的集合）来指示值类型。</span><span class="sxs-lookup"><span data-stu-id="dbe6b-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="dbe6b-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbe6b-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="dbe6b-130">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="dbe6b-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
