---
title: 数据协定中的枚举类型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 86fa38b281d8944797fa858f8c67f0b60c733be8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595539"
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="29dd4-102">数据协定中的枚举类型</span><span class="sxs-lookup"><span data-stu-id="29dd4-102">Enumeration Types in Data Contracts</span></span>
<span data-ttu-id="29dd4-103">枚举可以用数据协定模型来表示。</span><span class="sxs-lookup"><span data-stu-id="29dd4-103">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="29dd4-104">本主题演练几个介绍编程模型的示例。</span><span class="sxs-lookup"><span data-stu-id="29dd4-104">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="29dd4-105">枚举基础知识</span><span class="sxs-lookup"><span data-stu-id="29dd4-105">Enumeration Basics</span></span>  
 <span data-ttu-id="29dd4-106">若要使用以数据协定模型表示的枚举类型，一种方法就是将 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用于该类型。</span><span class="sxs-lookup"><span data-stu-id="29dd4-106">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="29dd4-107">然后，必须将 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性应用于每个必须在数据协定中包含的成员。</span><span class="sxs-lookup"><span data-stu-id="29dd4-107">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="29dd4-108">下面的示例演示了两个类。</span><span class="sxs-lookup"><span data-stu-id="29dd4-108">The following example shows two classes.</span></span> <span data-ttu-id="29dd4-109">第一个类使用枚举，第二个类定义枚举。</span><span class="sxs-lookup"><span data-stu-id="29dd4-109">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="29dd4-110">仅当将 `Car` 字段的值设置为 `condition`、`New` 或 `Used` 之一时，才可发送或接收 `Rental` 类的实例。</span><span class="sxs-lookup"><span data-stu-id="29dd4-110">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="29dd4-111">如果 `condition` 为 `Broken` 或 `Stolen`，则会引发一个 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="29dd4-111">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="29dd4-112">可以照常将 <xref:System.Runtime.Serialization.DataContractAttribute> 属性（<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 和 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>）用于枚举数据协定。</span><span class="sxs-lookup"><span data-stu-id="29dd4-112">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="29dd4-113">枚举成员值</span><span class="sxs-lookup"><span data-stu-id="29dd4-113">Enumeration Member Values</span></span>  
 <span data-ttu-id="29dd4-114">通常数据协定包括枚举成员名称，而不包括数值。</span><span class="sxs-lookup"><span data-stu-id="29dd4-114">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="29dd4-115">但是，在使用数据协定模型时，如果接收方是 WCF 客户端，则导出的架构将保留数字值。</span><span class="sxs-lookup"><span data-stu-id="29dd4-115">However, when using the data contract model, if the receiving side is a WCF client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="29dd4-116">请注意，使用[XmlSerializer 类](using-the-xmlserializer-class.md)时不会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="29dd4-116">Note that this is not the case when using the [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="29dd4-117">在上面的示例中，如果将 `condition` 设置为 `Used` 并且将数据序列化为 XML，则生成的 XML 是 `<condition>Used</condition>` 而不是 `<condition>1</condition>`。</span><span class="sxs-lookup"><span data-stu-id="29dd4-117">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="29dd4-118">因此，下面的数据协定等效于 `CarConditionEnum` 的数据协定。</span><span class="sxs-lookup"><span data-stu-id="29dd4-118">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="29dd4-119">例如，您可以在发送端使用 `CarConditionEnum` 并且在接收端使用 `CarConditionWithNumbers`。</span><span class="sxs-lookup"><span data-stu-id="29dd4-119">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="29dd4-120">尽管发送端的 `Used` 使用值“1”而接收端使用值“20”，但是两端的 XML 表示形式均为 `<condition>Used</condition>`。</span><span class="sxs-lookup"><span data-stu-id="29dd4-120">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="29dd4-121">若要包含在数据协定中，必须应用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="29dd4-121">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="29dd4-122">在 .NET Framework 中，始终可以将特殊值0（零）应用于枚举，这也是任何枚举的默认值。</span><span class="sxs-lookup"><span data-stu-id="29dd4-122">In the .NET Framework, you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="29dd4-123">但是，即使对于此特殊值零，也只能使用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性标记才能进行序列化。</span><span class="sxs-lookup"><span data-stu-id="29dd4-123">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="29dd4-124">以下为此规则的两种例外情况：</span><span class="sxs-lookup"><span data-stu-id="29dd4-124">There are two exceptions to this:</span></span>  
  
- <span data-ttu-id="29dd4-125">标志枚举（本主题的后面部分将进行讨论）。</span><span class="sxs-lookup"><span data-stu-id="29dd4-125">Flag enumerations (discussed later in this topic).</span></span>  
  
- <span data-ttu-id="29dd4-126"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 属性设置为 `false` 的枚举数据成员（这种情况下将从序列化数据中省略值为零的枚举）。</span><span class="sxs-lookup"><span data-stu-id="29dd4-126">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="29dd4-127">自定义枚举成员值</span><span class="sxs-lookup"><span data-stu-id="29dd4-127">Customizing Enumeration Member Values</span></span>  
 <span data-ttu-id="29dd4-128">可以通过使用 <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> 属性 (attribute) 的 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性 (property) 对作为数据协定构成部分的枚举成员值进行自定义。</span><span class="sxs-lookup"><span data-stu-id="29dd4-128">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="29dd4-129">例如，下面的数据协定也等效于 `CarConditionEnum` 的数据协定。</span><span class="sxs-lookup"><span data-stu-id="29dd4-129">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="29dd4-130">在序列化时，`PreviouslyOwned` 的值的 XML 表示形式为 `<condition>Used</condition>`。</span><span class="sxs-lookup"><span data-stu-id="29dd4-130">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="29dd4-131">简单枚举</span><span class="sxs-lookup"><span data-stu-id="29dd4-131">Simple Enumerations</span></span>  
 <span data-ttu-id="29dd4-132">您还可以对未向其应用 <xref:System.Runtime.Serialization.DataContractAttribute> 属性的枚举类型进行序列化。</span><span class="sxs-lookup"><span data-stu-id="29dd4-132">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="29dd4-133">可以按照上述方式来处理这种枚举类型，只不过将每个成员（这些成员未应用 <xref:System.NonSerializedAttribute> 属性）视为已应用了 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="29dd4-133">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="29dd4-134">例如，下面的枚举隐式具有一个与上面的 `CarConditionEnum` 示例等效的数据协定。</span><span class="sxs-lookup"><span data-stu-id="29dd4-134">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="29dd4-135">如果您不需要自定义枚举的数据协定名称、命名空间以及枚举成员值，则可以使用简单枚举。</span><span class="sxs-lookup"><span data-stu-id="29dd4-135">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="29dd4-136">简单枚举说明</span><span class="sxs-lookup"><span data-stu-id="29dd4-136">Notes on Simple Enumerations</span></span>  
 <span data-ttu-id="29dd4-137">将 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性应用于简单枚举是无效的。</span><span class="sxs-lookup"><span data-stu-id="29dd4-137">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="29dd4-138">是否将 <xref:System.SerializableAttribute> 属性应用于简单枚举并没有任何区别。</span><span class="sxs-lookup"><span data-stu-id="29dd4-138">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="29dd4-139"><xref:System.Runtime.Serialization.DataContractSerializer> 类采用应用于枚举成员的 <xref:System.NonSerializedAttribute> 属性的事实不同于 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 的行为。</span><span class="sxs-lookup"><span data-stu-id="29dd4-139">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="29dd4-140">这两种序列化程序都忽略 <xref:System.NonSerializedAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="29dd4-140">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="29dd4-141">标志枚举</span><span class="sxs-lookup"><span data-stu-id="29dd4-141">Flag Enumerations</span></span>  
 <span data-ttu-id="29dd4-142">可以将 <xref:System.FlagsAttribute> 属性应用于枚举。</span><span class="sxs-lookup"><span data-stu-id="29dd4-142">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="29dd4-143">在这种情况下，可以同时发送或接收包含零个或多个枚举值的列表。</span><span class="sxs-lookup"><span data-stu-id="29dd4-143">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="29dd4-144">为此，请将 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用于标志枚举，然后使用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性对所有为 2 的幂的成员进行标记。</span><span class="sxs-lookup"><span data-stu-id="29dd4-144">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="29dd4-145">请注意，若要使用标志枚举，级数必须为不间断的 2 的幂的序列（例如，1、2、4、8、16、32、64）。</span><span class="sxs-lookup"><span data-stu-id="29dd4-145">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="29dd4-146">可以使用下面的步骤来发送标志的枚举值：</span><span class="sxs-lookup"><span data-stu-id="29dd4-146">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1. <span data-ttu-id="29dd4-147">尝试查找映射到数值的枚举成员（应用了 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性）。</span><span class="sxs-lookup"><span data-stu-id="29dd4-147">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="29dd4-148">如果可以找到，请发送仅包含该成员的列表。</span><span class="sxs-lookup"><span data-stu-id="29dd4-148">If found, send a list that contains just that member.</span></span>  
  
2. <span data-ttu-id="29dd4-149">尝试将此数值分解为和的形式，以便枚举成员（每个成员都应用了 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性）可以映射到和的各个部分。</span><span class="sxs-lookup"><span data-stu-id="29dd4-149">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="29dd4-150">发送包含所有这些成员的列表。</span><span class="sxs-lookup"><span data-stu-id="29dd4-150">Send the list of all these members.</span></span> <span data-ttu-id="29dd4-151">请注意，*贪婪算法*用于查找这样的总和，因此不能保证即使存在此类 sum 也是如此。</span><span class="sxs-lookup"><span data-stu-id="29dd4-151">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="29dd4-152">为避免出现这种问题，请确保枚举成员的数值为 2 的幂。</span><span class="sxs-lookup"><span data-stu-id="29dd4-152">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3. <span data-ttu-id="29dd4-153">如果上面的两个步骤均无法实现并且数值为非零，则引发一个 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="29dd4-153">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="29dd4-154">如果数值为零，则发送空列表。</span><span class="sxs-lookup"><span data-stu-id="29dd4-154">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="29dd4-155">示例</span><span class="sxs-lookup"><span data-stu-id="29dd4-155">Example</span></span>  
 <span data-ttu-id="29dd4-156">下面的枚举示例可用于标志操作。</span><span class="sxs-lookup"><span data-stu-id="29dd4-156">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="29dd4-157">下面的示例值将按照指示的方式进行序列化。</span><span class="sxs-lookup"><span data-stu-id="29dd4-157">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="29dd4-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="29dd4-158">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="29dd4-159">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="29dd4-159">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="29dd4-160">在服务协定中指定数据传输</span><span class="sxs-lookup"><span data-stu-id="29dd4-160">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)
