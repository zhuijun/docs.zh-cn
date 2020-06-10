---
title: 数据协定版本管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 493efab41e2c6763eb95df8662e6254d9e0df2f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593498"
---
# <a name="data-contract-versioning"></a><span data-ttu-id="66e76-102">数据协定版本管理</span><span class="sxs-lookup"><span data-stu-id="66e76-102">Data Contract Versioning</span></span>
<span data-ttu-id="66e76-103">随着应用程序的发展，您也可能不得不更改服务使用的数据协定。</span><span class="sxs-lookup"><span data-stu-id="66e76-103">As applications evolve, you may also have to change the data contracts the services use.</span></span> <span data-ttu-id="66e76-104">本主题说明如何管理数据协定的版本。</span><span class="sxs-lookup"><span data-stu-id="66e76-104">This topic explains how to version data contracts.</span></span> <span data-ttu-id="66e76-105">本主题介绍数据协定版本管理机制。</span><span class="sxs-lookup"><span data-stu-id="66e76-105">This topic describes the data contract versioning mechanisms.</span></span> <span data-ttu-id="66e76-106">有关完整的概述和说明性的版本控制指南，请参阅[最佳做法：数据协定版本控制](../best-practices-data-contract-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="66e76-106">For a complete overview and prescriptive versioning guidance, see [Best Practices: Data Contract Versioning](../best-practices-data-contract-versioning.md).</span></span>  
  
## <a name="breaking-vs-nonbreaking-changes"></a><span data-ttu-id="66e76-107">重大更改与非重大更改</span><span class="sxs-lookup"><span data-stu-id="66e76-107">Breaking vs. Nonbreaking Changes</span></span>  
 <span data-ttu-id="66e76-108">对数据协定的更改可能是重大更改，也可能是非重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-108">Changes to a data contract can be breaking or nonbreaking.</span></span> <span data-ttu-id="66e76-109">对数据协定进行非重大更改时，使用较早版本协定的应用程序和使用较新版本协定的应用程序可以互相通信。</span><span class="sxs-lookup"><span data-stu-id="66e76-109">When a data contract is changed in a nonbreaking way, an application using the older version of the contract can communicate with an application using the newer version, and an application using the newer version of the contract can communicate with an application using the older version.</span></span> <span data-ttu-id="66e76-110">另一方面，如果进行重大更改，则会阻止单向或双向通信。</span><span class="sxs-lookup"><span data-stu-id="66e76-110">On the other hand, a breaking change prevents communication in one or both directions.</span></span>  
  
 <span data-ttu-id="66e76-111">对类型的任何更改，只要不影响其传输方式和接收方式，都是非重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-111">Any changes to a type that do not affect how it is transmitted and received are nonbreaking.</span></span> <span data-ttu-id="66e76-112">这类更改只更改基础类型，而不更改数据协定。</span><span class="sxs-lookup"><span data-stu-id="66e76-112">Such changes do not change the data contract, only the underlying type.</span></span> <span data-ttu-id="66e76-113">例如，如果更改一个字段的名称后，将 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性设置为较早版本的名称，则属于非重大更改方式。</span><span class="sxs-lookup"><span data-stu-id="66e76-113">For example, you can change the name of a field in a nonbreaking way if you then set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to the older version name.</span></span> <span data-ttu-id="66e76-114">下面的代码演示数据协定的版本 1。</span><span class="sxs-lookup"><span data-stu-id="66e76-114">The following code shows version 1 of a data contract.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 <span data-ttu-id="66e76-115">下面的代码演示非重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-115">The following code shows a nonbreaking change.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 <span data-ttu-id="66e76-116">有些更改确实修改了传输的数据，但这些更改可能是重大更改，也可能不是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-116">Some changes do modify the transmitted data, but may or may not be breaking.</span></span> <span data-ttu-id="66e76-117">下面的更改始终是重大更改：</span><span class="sxs-lookup"><span data-stu-id="66e76-117">The following changes are always breaking:</span></span>  
  
- <span data-ttu-id="66e76-118">更改数据协定的 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 或 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="66e76-118">Changing the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> or <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> value of a data contract.</span></span>  
  
- <span data-ttu-id="66e76-119">通过 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性来更改数据成员的顺序。</span><span class="sxs-lookup"><span data-stu-id="66e76-119">Changing the order of data members by using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute>.</span></span>  
  
- <span data-ttu-id="66e76-120">重命名数据成员。</span><span class="sxs-lookup"><span data-stu-id="66e76-120">Renaming a data member.</span></span>  
  
- <span data-ttu-id="66e76-121">更改数据成员的数据协定。</span><span class="sxs-lookup"><span data-stu-id="66e76-121">Changing the data contract of a data member.</span></span> <span data-ttu-id="66e76-122">例如，将数据成员的类型从整数更改为字符串，或者从数据协定名称为“Customer”的类型更改为数据协定名称为“Person”的类型。</span><span class="sxs-lookup"><span data-stu-id="66e76-122">For example, changing the type of data member from an integer to a string, or from a type with a data contract named "Customer" to a type with a data contract named "Person".</span></span>  
  
 <span data-ttu-id="66e76-123">下面的更改也可能是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-123">The following changes are also possible.</span></span>  
  
## <a name="adding-and-removing-data-members"></a><span data-ttu-id="66e76-124">添加或移除数据成员</span><span class="sxs-lookup"><span data-stu-id="66e76-124">Adding and Removing Data Members</span></span>  
 <span data-ttu-id="66e76-125">大多数情况下，添加或移除数据成员不是重大更改，除非要求严格的架构验证（新实例针对旧架构进行验证）。</span><span class="sxs-lookup"><span data-stu-id="66e76-125">In most cases, adding or removing a data member is not a breaking change, unless you require strict schema validity (new instances validating against the old schema).</span></span>  
  
 <span data-ttu-id="66e76-126">将具有额外字段的类型反序列化为具有缺失字段的类型时，将忽略额外的信息。</span><span class="sxs-lookup"><span data-stu-id="66e76-126">When a type with an extra field is deserialized into a type with a missing field, the extra information is ignored.</span></span> <span data-ttu-id="66e76-127">（还可能出于往返目的而存储它; 有关详细信息，请参阅[向前兼容的数据约定](forward-compatible-data-contracts.md)）。</span><span class="sxs-lookup"><span data-stu-id="66e76-127">(It may also be stored for round-tripping purposes; for more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md)).</span></span>  
  
 <span data-ttu-id="66e76-128">具有缺失字段的类型反序列化为具有额外字段的类型时，额外字段将保留其默认值，通常为零或 `null`。</span><span class="sxs-lookup"><span data-stu-id="66e76-128">When a type with a missing field is deserialized into a type with an extra field, the extra field is left at its default value, usually zero or `null`.</span></span> <span data-ttu-id="66e76-129">（默认值可能会更改; 有关详细信息，请参阅[版本容错序列化回调](version-tolerant-serialization-callbacks.md)。）</span><span class="sxs-lookup"><span data-stu-id="66e76-129">(The default value may be changed; for more information, see [Version-Tolerant Serialization Callbacks](version-tolerant-serialization-callbacks.md).)</span></span>  
  
 <span data-ttu-id="66e76-130">例如，您可以在客户端上使用 `CarV1` 类，在服务上使用 `CarV2` 类；也可以在服务上使用 `CarV1` 类，在客户端上使用 `CarV2` 类。</span><span class="sxs-lookup"><span data-stu-id="66e76-130">For example, you can use the `CarV1` class on a client and the `CarV2` class on a service, or you can use the `CarV1` class on a service and the `CarV2` class on a client.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 <span data-ttu-id="66e76-131">版本 2 终结点可以成功地向版本 1 终结点发送数据。</span><span class="sxs-lookup"><span data-stu-id="66e76-131">The version 2 endpoint can successfully send data to the version 1 endpoint.</span></span> <span data-ttu-id="66e76-132">对版本 2 的 `Car` 数据协定进行序列化将生成 XML，如下所示。</span><span class="sxs-lookup"><span data-stu-id="66e76-132">Serializing version 2 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 <span data-ttu-id="66e76-133">V1 上的反序列化引擎没有找到 `HorsePower` 字段的匹配数据成员，因而丢弃该数据。</span><span class="sxs-lookup"><span data-stu-id="66e76-133">The deserialization engine on V1 does not find a matching data member for the `HorsePower` field, and discards that data.</span></span>  
  
 <span data-ttu-id="66e76-134">同样，版本 1 终结点也可以向版本 2 终结点发送数据。</span><span class="sxs-lookup"><span data-stu-id="66e76-134">Also, the version 1 endpoint can send data to the version 2 endpoint.</span></span> <span data-ttu-id="66e76-135">对版本 1 的 `Car` 数据协定进行序列化将生成 XML，如下所示。</span><span class="sxs-lookup"><span data-stu-id="66e76-135">Serializing version 1 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 <span data-ttu-id="66e76-136">版本 2 反序列化程序不知道将 `HorsePower` 字段设置为何值，因为传入的 XML 中没有匹配数据。</span><span class="sxs-lookup"><span data-stu-id="66e76-136">The version 2 deserializer does not know what to set the `HorsePower` field to, because there is no matching data in the incoming XML.</span></span> <span data-ttu-id="66e76-137">该字段设置为默认值 0。</span><span class="sxs-lookup"><span data-stu-id="66e76-137">Instead, the field is set to the default value of 0.</span></span>  
  
## <a name="required-data-members"></a><span data-ttu-id="66e76-138">必需的数据成员</span><span class="sxs-lookup"><span data-stu-id="66e76-138">Required Data Members</span></span>  
 <span data-ttu-id="66e76-139">通过将 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性设置为 `true`，可以将数据成员标记为必需的数据成员。</span><span class="sxs-lookup"><span data-stu-id="66e76-139">A data member may be marked as being required by setting the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to `true`.</span></span> <span data-ttu-id="66e76-140">如果反序列化时缺少必需的数据，则会引发异常，而不是将数据成员设置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="66e76-140">If required data is missing while deserializing, an exception is thrown instead of setting the data member to its default value.</span></span>  
  
 <span data-ttu-id="66e76-141">添加必需的数据成员是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-141">Adding a required data member is a breaking change.</span></span> <span data-ttu-id="66e76-142">也就是说，新类型仍然可以发送到具有旧类型的终结点，但无法反向发送。</span><span class="sxs-lookup"><span data-stu-id="66e76-142">That is, the newer type can still be sent to endpoints with the older type, but not the other way around.</span></span> <span data-ttu-id="66e76-143">移除在任何早期版本中标记为必需成员的数据成员也是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-143">Removing a data member that was marked as required in any prior version is also a breaking change.</span></span>  
  
 <span data-ttu-id="66e76-144">将 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 属性值从 `true` 更改为 `false` 不是重大更改；如果类型的任何早期版本都没有相应数据成员，将该属性值从 `false` 更改为 `true` 就可能是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-144">Changing the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property value from `true` to `false` is not breaking, but changing it from `false` to `true` may be breaking if any prior versions of the type do not have the data member in question.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66e76-145">尽管 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 属性设置为 `true`，但传入数据可能为 null 或零，类型必须准备好处理这种可能的情况。</span><span class="sxs-lookup"><span data-stu-id="66e76-145">Although the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property is set to `true`, the incoming data may be null or zero, and a type must be prepared to handle this possibility.</span></span> <span data-ttu-id="66e76-146">不要将 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 用作安全机制来防止不良传入数据。</span><span class="sxs-lookup"><span data-stu-id="66e76-146">Do not use <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> as a security mechanism to protect against bad incoming data.</span></span>  
  
## <a name="omitted-default-values"></a><span data-ttu-id="66e76-147">省略的默认值</span><span class="sxs-lookup"><span data-stu-id="66e76-147">Omitted Default Values</span></span>  
 <span data-ttu-id="66e76-148">可以（尽管不建议）将 `EmitDefaultValue` DataMemberAttribute 属性上的属性设置为 `false` ，如[数据成员默认值](data-member-default-values.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="66e76-148">It is possible (although not recommended) to set the `EmitDefaultValue` property on the DataMemberAttribute attribute to `false`, as described in [Data Member Default Values](data-member-default-values.md).</span></span> <span data-ttu-id="66e76-149">如果该属性设置为 `false`，而数据成员设置为其默认值（通常为 null 或零），则不会发出该数据成员。</span><span class="sxs-lookup"><span data-stu-id="66e76-149">If this setting is `false`, the data member will not be emitted if it is set to its default value (usually null or zero).</span></span> <span data-ttu-id="66e76-150">这样，就在两个方面与不同版本中的必需数据成员不兼容：</span><span class="sxs-lookup"><span data-stu-id="66e76-150">This is not compatible with required data members in different versions in two ways:</span></span>  
  
- <span data-ttu-id="66e76-151">一个版本中具有必需数据成员的数据协定无法从该数据成员的 `EmitDefaultValue` 已设置为 `false` 的另一个版本接收默认值（null 或零）数据。</span><span class="sxs-lookup"><span data-stu-id="66e76-151">A data contract with a data member that is required in one version cannot receive default (null or zero) data from a different version in which the data member has `EmitDefaultValue` set to `false`.</span></span>  
  
- <span data-ttu-id="66e76-152">已将 `EmitDefaultValue` 设置为 `false` 的必需数据成员不可用来序列化其默认值（null 或零），但它可在反序列化时接收其默认值。</span><span class="sxs-lookup"><span data-stu-id="66e76-152">A required data member that has `EmitDefaultValue` set to `false` cannot be used to serialize its default (null or zero) value, but can receive such a value on deserialization.</span></span> <span data-ttu-id="66e76-153">这就形成了一个往返问题（数据可以读入，但随后无法写出同样的数据）。</span><span class="sxs-lookup"><span data-stu-id="66e76-153">This creates a round-tripping problem (data can be read in but the same data cannot then be written out).</span></span> <span data-ttu-id="66e76-154">因此，如果在一个版本中，`IsRequired` 为 `true` 而 `EmitDefaultValue` 为 `false`，则同样的组合应当应用到所有其他版本，任何数据协定版本都无法生成一个不会导致往返过程的值。</span><span class="sxs-lookup"><span data-stu-id="66e76-154">Therefore, if `IsRequired` is `true` and `EmitDefaultValue` is `false` in one version, the same combination should apply to all other versions such that no version of the data contract would be able to produce a value that does not result in a round trip.</span></span>  
  
## <a name="schema-considerations"></a><span data-ttu-id="66e76-155">架构注意事项</span><span class="sxs-lookup"><span data-stu-id="66e76-155">Schema Considerations</span></span>  
 <span data-ttu-id="66e76-156">有关为数据协定类型生成的架构的说明，请参阅[数据协定架构引用](data-contract-schema-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="66e76-156">For an explanation of what schema is produced for data contract types, see [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span>  
  
 <span data-ttu-id="66e76-157">WCF 为数据协定类型生成的架构不会对版本控制进行任何设置。</span><span class="sxs-lookup"><span data-stu-id="66e76-157">The schema WCF produces for data contract types makes no provisions for versioning.</span></span> <span data-ttu-id="66e76-158">也就是说，从类型的某个版本中导出的架构仅包含该版本的数据成员。</span><span class="sxs-lookup"><span data-stu-id="66e76-158">That is, the schema exported from a certain version of a type contains only those data members present in that version.</span></span> <span data-ttu-id="66e76-159">实现 <xref:System.Runtime.Serialization.IExtensibleDataObject> 接口不会改变类型的架构。</span><span class="sxs-lookup"><span data-stu-id="66e76-159">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface does not change the schema for a type.</span></span>  
  
 <span data-ttu-id="66e76-160">默认情况下，数据成员是作为可选元素导出到架构的。</span><span class="sxs-lookup"><span data-stu-id="66e76-160">Data members are exported to the schema as optional elements by default.</span></span> <span data-ttu-id="66e76-161">即，`minOccurs`（XML 属性）值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="66e76-161">That is, the `minOccurs` (XML attribute) value is set to 0.</span></span> <span data-ttu-id="66e76-162">如果 `minOccurs` 设置为 1，则导出必需的数据成员。</span><span class="sxs-lookup"><span data-stu-id="66e76-162">Required data members are exported with `minOccurs` set to 1.</span></span>  
  
 <span data-ttu-id="66e76-163">如果要求严格遵从架构，许多视为非重大更改的更改实际上是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-163">Many of the changes considered to be nonbreaking are actually breaking if strict adherence to the schema is required.</span></span> <span data-ttu-id="66e76-164">在上面的示例中，仅具有 `CarV1` 元素的 `Model` 实例将针对 `CarV2` 架构（具有 `Model` 和 `Horsepower`，但它们都是可选的）进行验证。</span><span class="sxs-lookup"><span data-stu-id="66e76-164">In the preceding example, a `CarV1` instance with just the `Model` element would validate against the `CarV2` schema (which has both `Model` and `Horsepower`, but both are optional).</span></span> <span data-ttu-id="66e76-165">但是，反过来并不成立：`CarV2` 实例无法针对 `CarV1` 架构进行验证。</span><span class="sxs-lookup"><span data-stu-id="66e76-165">However, the reverse is not true: a `CarV2` instance would fail validation against the `CarV1` schema.</span></span>  
  
 <span data-ttu-id="66e76-166">关于往返过程，还有一些其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="66e76-166">Round-tripping also entails some additional considerations.</span></span> <span data-ttu-id="66e76-167">有关详细信息，请参阅[向前兼容的数据协定](forward-compatible-data-contracts.md)中的 "架构注意事项" 部分。</span><span class="sxs-lookup"><span data-stu-id="66e76-167">For more information, see the "Schema Considerations" section in [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
### <a name="other-permitted-changes"></a><span data-ttu-id="66e76-168">其他允许的更改</span><span class="sxs-lookup"><span data-stu-id="66e76-168">Other Permitted Changes</span></span>  
 <span data-ttu-id="66e76-169">实现 <xref:System.Runtime.Serialization.IExtensibleDataObject> 接口是非重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-169">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface is a nonbreaking change.</span></span> <span data-ttu-id="66e76-170">但是，在实现 <xref:System.Runtime.Serialization.IExtensibleDataObject> 的版本之前，类型版本不提供往返过程支持。</span><span class="sxs-lookup"><span data-stu-id="66e76-170">However, round-tripping support does not exist for versions of the type prior to the version in which <xref:System.Runtime.Serialization.IExtensibleDataObject> was implemented.</span></span> <span data-ttu-id="66e76-171">有关详细信息，请参阅[向前兼容的数据协定](forward-compatible-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="66e76-171">For more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="66e76-172">枚举</span><span class="sxs-lookup"><span data-stu-id="66e76-172">Enumerations</span></span>  
 <span data-ttu-id="66e76-173">添加或移除枚举成员是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-173">Adding or removing an enumeration member is a breaking change.</span></span> <span data-ttu-id="66e76-174">更改枚举成员的名称是重大更改，除非使用 `EnumMemberAttribute` 属性将其协定名称保持为与旧版本中的名称相同。</span><span class="sxs-lookup"><span data-stu-id="66e76-174">Changing the name of an enumeration member is breaking, unless its contract name is kept the same as in the old version by using the `EnumMemberAttribute` attribute.</span></span> <span data-ttu-id="66e76-175">有关详细信息，请参阅[数据协定中的枚举类型](enumeration-types-in-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="66e76-175">For more information, see [Enumeration Types in Data Contracts](enumeration-types-in-data-contracts.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="66e76-176">集合</span><span class="sxs-lookup"><span data-stu-id="66e76-176">Collections</span></span>  
 <span data-ttu-id="66e76-177">大多数集合更改是非重大更改，这是因为在数据协定模型中，大多数集合类型可以彼此互换。</span><span class="sxs-lookup"><span data-stu-id="66e76-177">Most collection changes are nonbreaking because most collection types are interchangeable with each other in the data contract model.</span></span> <span data-ttu-id="66e76-178">但是，将非自定义集合更改为自定义集合是重大更改，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="66e76-178">However, making a noncustomized collection customized or vice versa is a breaking change.</span></span> <span data-ttu-id="66e76-179">此外，更改集合的自定义设置（即，更改其数据协定名称和命名空间、重复元素名称、键元素名称以及值元素名称）也是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-179">Also, changing the collection's customization settings is a breaking change; that is, changing its data contract name and namespace, repeating element name, key element name, and value element name.</span></span> <span data-ttu-id="66e76-180">有关集合自定义的详细信息，请参阅[数据协定中的集合类型](collection-types-in-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="66e76-180">For more information about collection customization, see [Collection Types in Data Contracts](collection-types-in-data-contracts.md).</span></span>  
<span data-ttu-id="66e76-181">更改集合内容的数据协定（例如，从整数列表更改为字符串列表）自然也是重大更改。</span><span class="sxs-lookup"><span data-stu-id="66e76-181">Naturally, changing the data contract of contents of a collection (for example, changing from a list of integers to a list of strings) is a breaking change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e76-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66e76-182">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [<span data-ttu-id="66e76-183">版本容错序列化回调</span><span class="sxs-lookup"><span data-stu-id="66e76-183">Version-Tolerant Serialization Callbacks</span></span>](version-tolerant-serialization-callbacks.md)
- [<span data-ttu-id="66e76-184">最佳做法：数据协定版本管理</span><span class="sxs-lookup"><span data-stu-id="66e76-184">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="66e76-185">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="66e76-185">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="66e76-186">数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="66e76-186">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="66e76-187">向前兼容的数据协定</span><span class="sxs-lookup"><span data-stu-id="66e76-187">Forward-Compatible Data Contracts</span></span>](forward-compatible-data-contracts.md)
