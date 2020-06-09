---
title: 数据成员默认值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: e4eaaec880ecfcff24d9d5b4e8347a84738e070b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593472"
---
# <a name="data-member-default-values"></a><span data-ttu-id="4675d-102">数据成员默认值</span><span class="sxs-lookup"><span data-stu-id="4675d-102">Data Member Default Values</span></span>
<span data-ttu-id="4675d-103">在 .NET Framework 中，类型具有*默认值*的概念。</span><span class="sxs-lookup"><span data-stu-id="4675d-103">In the .NET Framework, types have a concept of *default values*.</span></span> <span data-ttu-id="4675d-104">例如，对于任何引用类型，默认值为 `null`，而整型的默认值为零。</span><span class="sxs-lookup"><span data-stu-id="4675d-104">For example, for any reference type the default value is `null`, and for an integer type it is zero.</span></span> <span data-ttu-id="4675d-105">如果某个数据成员设置为其默认值，有时会希望序列化数据中不包含该数据成员。</span><span class="sxs-lookup"><span data-stu-id="4675d-105">It is occasionally desirable to omit a data member from serialized data when it is set to its default value.</span></span> <span data-ttu-id="4675d-106">由于成员具有默认值，这个实际值不需要进行序列化；这样处理可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="4675d-106">Because the member has a default value, an actual value need not be serialized; this has a performance advantage.</span></span>  
  
 <span data-ttu-id="4675d-107">若要在序列化数据中忽略某个成员，请将 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 属性 (Attribute) 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (Property) 设置为 `false`（默认值为 `true`）。</span><span class="sxs-lookup"><span data-stu-id="4675d-107">To omit a member from serialized data, set the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to `false` (the default is `true`).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4675d-108">如果有特定需要（如实现互操作性或减小数据大小），应将 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="4675d-108">You should set the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property to `false` if there is a specific need to do so, such as for interoperability or data size reduction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4675d-109">示例</span><span class="sxs-lookup"><span data-stu-id="4675d-109">Example</span></span>  
 <span data-ttu-id="4675d-110">下面的代码中，有几个成员的 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="4675d-110">The following code has several members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> set to `false`.</span></span>  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 <span data-ttu-id="4675d-111">如果序列化此类的实例，则结果如下：序列化 `employeeName` 和 `employeeID`。</span><span class="sxs-lookup"><span data-stu-id="4675d-111">If an instance of this class is serialized, the result is as follows: `employeeName` and `employeeID` is serialized.</span></span> <span data-ttu-id="4675d-112">`employeeName` 的 null 值和 `employeeID` 的零值显式成为序列化数据的一部分。</span><span class="sxs-lookup"><span data-stu-id="4675d-112">The null value for `employeeName` and the zero value for `employeeID` is explicitly part of the serialized data.</span></span> <span data-ttu-id="4675d-113">但是，`position`、`salary` 和 `bonus` 成员没有被序列化。</span><span class="sxs-lookup"><span data-stu-id="4675d-113">However, the `position`, `salary`, and `bonus` members are not serialized.</span></span> <span data-ttu-id="4675d-114">最后，即使 `targetSalary` 属性设置为 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>，由于 57800 不是 .NET 的整数默认值零，`false` 还是照常被序列化。</span><span class="sxs-lookup"><span data-stu-id="4675d-114">Finally, `targetSalary` is serialized as usual, even though the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property is set to `false`, because 57800 does not match the .NET default value for an integer, which is zero.</span></span>  
  
### <a name="xml-representation"></a><span data-ttu-id="4675d-115">XML 表示形式</span><span class="sxs-lookup"><span data-stu-id="4675d-115">XML Representation</span></span>  
 <span data-ttu-id="4675d-116">如果上一个示例序列化为 XML，则表示形式类似于下面的内容。</span><span class="sxs-lookup"><span data-stu-id="4675d-116">If the previous example is serialized to XML, the representation is similar to the following.</span></span>  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 <span data-ttu-id="4675d-117">`xsi:nil` 属性是万维网联合会 (W3C) XML 架构实例命名空间中的一个特殊属性，它提供一种显式表示 null 值的可互操作方式。</span><span class="sxs-lookup"><span data-stu-id="4675d-117">The `xsi:nil` attribute is a special attribute in the World Wide Web Consortium (W3C) XML Schema instance namespace that provides an interoperable way to explicitly represent a null value.</span></span> <span data-ttu-id="4675d-118">请注意，在 XML 中，没有 position、salary 和 bonus 数据成员的任何相关信息。</span><span class="sxs-lookup"><span data-stu-id="4675d-118">Note that there is no information at all in the XML about position, salary, and bonus data members.</span></span> <span data-ttu-id="4675d-119">接收端可将它们分别解释为 `null`、零和 `null`。</span><span class="sxs-lookup"><span data-stu-id="4675d-119">The receiving end can interpret these as `null`, zero, and `null`, respectively.</span></span> <span data-ttu-id="4675d-120">无法确保第三方反序列化程序可以进行正确的解释，这就是不建议使用这种模式的原因。</span><span class="sxs-lookup"><span data-stu-id="4675d-120">There is no guarantee that a third-party deserializer can make the correct interpretation, which is why this pattern is not recommended.</span></span> <span data-ttu-id="4675d-121"><xref:System.Runtime.Serialization.DataContractSerializer> 类始终为缺少的值选择正确的解释。</span><span class="sxs-lookup"><span data-stu-id="4675d-121">The <xref:System.Runtime.Serialization.DataContractSerializer> class always selects the correct interpretation for missing values.</span></span>  
  
### <a name="interaction-with-isrequired"></a><span data-ttu-id="4675d-122">与 IsRequired 交互</span><span class="sxs-lookup"><span data-stu-id="4675d-122">Interaction with IsRequired</span></span>  
 <span data-ttu-id="4675d-123">如[数据协定版本控制](data-contract-versioning.md)中所述， <xref:System.Runtime.Serialization.DataMemberAttribute> 特性具有一个 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 属性（默认值为 `false` ）。</span><span class="sxs-lookup"><span data-stu-id="4675d-123">As discussed in [Data Contract Versioning](data-contract-versioning.md), the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property (the default is `false`).</span></span> <span data-ttu-id="4675d-124">该属性 (Property) 指示，当某个给定数据成员进行反序列化时，该数据成员是否必须出现在序列化数据中。</span><span class="sxs-lookup"><span data-stu-id="4675d-124">The property indicates whether a given data member must be present in the serialized data when it is being deserialized.</span></span> <span data-ttu-id="4675d-125">如果 `IsRequired` 设置为 `true`（指示值必须存在）并且 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 设置为 `false`（指示如果值设置为其默认值，则该值不得存在），则由于结果相互矛盾，此数据成员的默认值无法序列化。</span><span class="sxs-lookup"><span data-stu-id="4675d-125">If `IsRequired` is set to `true`, (which indicates that a value must be present) and <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> is set to `false` (indicating that the value must not be present if it is set to its default value), default values for this data member cannot be serialized because the results would be contradictory.</span></span> <span data-ttu-id="4675d-126">如果这样的一个数据成员被设置为其默认值（通常为 `null` 或零）并且尝试进行序列化，则会引发 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="4675d-126">If such a data member is set to its default value (usually `null` or zero) and a serialization is attempted, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
### <a name="schema-representation"></a><span data-ttu-id="4675d-127">架构表示形式</span><span class="sxs-lookup"><span data-stu-id="4675d-127">Schema Representation</span></span>  
 <span data-ttu-id="4675d-128">当属性设置为时，数据成员的 XML 架构定义语言（XSD）架构表示形式的详细信息 `EmitDefaultValue` `false` 将在[数据协定架构引用](data-contract-schema-reference.md)中讨论。</span><span class="sxs-lookup"><span data-stu-id="4675d-128">The details of the XML Schema definition language (XSD) schema representation of data members when the `EmitDefaultValue` property is set to `false` are discussed in [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span> <span data-ttu-id="4675d-129">下面是简要概述：</span><span class="sxs-lookup"><span data-stu-id="4675d-129">However, the following is a brief overview:</span></span>  
  
- <span data-ttu-id="4675d-130">当 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 设置为时 `false` ，它会在架构中表示为特定于 WINDOWS COMMUNICATION FOUNDATION （WCF）的批注。</span><span class="sxs-lookup"><span data-stu-id="4675d-130">When the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> is set to `false`, it is represented in the schema as an annotation specific to Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4675d-131">没有用于表示此信息的可交互操作方式。</span><span class="sxs-lookup"><span data-stu-id="4675d-131">There is no interoperable way to represent this information.</span></span> <span data-ttu-id="4675d-132">特别是，架构中的“default”属性不用于此目的，`minOccurs` 属性仅受 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 设置的影响，而 `nillable` 属性仅受数据成员类型的影响。</span><span class="sxs-lookup"><span data-stu-id="4675d-132">In particular, the "default" attribute in the schema is not used for this purpose, the `minOccurs` attribute is affected only by the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> setting, and the `nillable` attribute is affected only by the type of the data member.</span></span>  
  
- <span data-ttu-id="4675d-133">要使用的实际默认值在架构中不存在。</span><span class="sxs-lookup"><span data-stu-id="4675d-133">The actual default value to use is not present in the schema.</span></span> <span data-ttu-id="4675d-134">由接收终结点负责对缺少元素进行适当解释。</span><span class="sxs-lookup"><span data-stu-id="4675d-134">It is up to the receiving endpoint to appropriately interpret a missing element.</span></span>  
  
 <span data-ttu-id="4675d-135">对于架构导入， <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false` 只要检测到前面提到的 WCF 特定的批注，属性就会自动设置为。</span><span class="sxs-lookup"><span data-stu-id="4675d-135">On schema import, the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property is automatically set to `false` whenever the WCF-specific annotation mentioned previously is detected.</span></span> <span data-ttu-id="4675d-136">对于属性设置为的引用类型，它还设置为， `false` `nillable` `false` 以支持在使用 ASP.NET Web 服务时经常发生的特定互操作方案。</span><span class="sxs-lookup"><span data-stu-id="4675d-136">It is also set to `false` for reference types that have the `nillable` property set to `false` to support specific interoperability scenarios that commonly occur when consuming ASP.NET Web services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4675d-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4675d-137">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
