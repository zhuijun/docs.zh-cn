---
title: 使用数据协定
description: 了解用于为每个参数或返回类型定义的数据协定，将序列化的数据序列化到 WCF 客户端和服务器之间进行交换。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 80ea2a8bd67c627fbe11ee07e640704c1a41ef7b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244720"
---
# <a name="using-data-contracts"></a><span data-ttu-id="0b33d-103">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="0b33d-103">Using Data Contracts</span></span>
<span data-ttu-id="0b33d-104">“数据协定” \*\* 是在服务与客户端之间达成的正式协议，用于以抽象方式描述要交换的数据。</span><span class="sxs-lookup"><span data-stu-id="0b33d-104">A *data contract* is a formal agreement between a service and a client that abstractly describes the data to be exchanged.</span></span> <span data-ttu-id="0b33d-105">也就是说，为了进行通信，客户端和服务不必共享相同的类型，而只需共享相同的数据协定。</span><span class="sxs-lookup"><span data-stu-id="0b33d-105">That is, to communicate, the client and the service do not have to share the same types, only the same data contracts.</span></span> <span data-ttu-id="0b33d-106">数据协定为每个参数或返回类型精确定义为进行交换而序列化哪些数据（将哪些数据转换为 XML）。</span><span class="sxs-lookup"><span data-stu-id="0b33d-106">A data contract precisely defines, for each parameter or return type, what data is serialized (turned into XML) to be exchanged.</span></span>  
  
## <a name="data-contract-basics"></a><span data-ttu-id="0b33d-107">数据协定基本知识</span><span class="sxs-lookup"><span data-stu-id="0b33d-107">Data Contract Basics</span></span>  
 <span data-ttu-id="0b33d-108">默认情况下，Windows Communication Foundation （WCF）使用一种名为数据协定序列化程序的序列化引擎来序列化和反序列化数据（将其与 XML 相互转换）。</span><span class="sxs-lookup"><span data-stu-id="0b33d-108">Windows Communication Foundation (WCF) uses a serialization engine called the Data Contract Serializer by default to serialize and deserialize data (convert it to and from XML).</span></span> <span data-ttu-id="0b33d-109">所有 .NET Framework 基元类型（如整数和字符串）以及某些被视为基元的类型（如 <xref:System.DateTime> 和 <xref:System.Xml.XmlElement> ）都可以进行序列化，而无需进行任何其他准备，并被视为具有默认数据协定。</span><span class="sxs-lookup"><span data-stu-id="0b33d-109">All .NET Framework primitive types, such as integers and strings, as well as certain types treated as primitives, such as <xref:System.DateTime> and <xref:System.Xml.XmlElement>, can be serialized with no other preparation and are considered as having default data contracts.</span></span> <span data-ttu-id="0b33d-110">许多 .NET Framework 类型也具有现有数据协定。</span><span class="sxs-lookup"><span data-stu-id="0b33d-110">Many .NET Framework types also have existing data contracts.</span></span> <span data-ttu-id="0b33d-111">有关可序列化类型的完整列表，请参阅 [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md)。</span><span class="sxs-lookup"><span data-stu-id="0b33d-111">For a full list of serializable types, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="0b33d-112">必须为所创建的新复杂类型定义数据协定才能序列化这些类型。</span><span class="sxs-lookup"><span data-stu-id="0b33d-112">New complex types that you create must have a data contract defined for them to be serializable.</span></span> <span data-ttu-id="0b33d-113">默认情况下， <xref:System.Runtime.Serialization.DataContractSerializer> 推断数据协定并序列化所有公共可见类型。</span><span class="sxs-lookup"><span data-stu-id="0b33d-113">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> infers the data contract and serializes all publicly visible types.</span></span> <span data-ttu-id="0b33d-114">类型的所有公共读/写属性和字段均被序列化。</span><span class="sxs-lookup"><span data-stu-id="0b33d-114">All public read/write properties and fields of the type are serialized.</span></span> <span data-ttu-id="0b33d-115">可以使用 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>从序列化中剔除某些成员。</span><span class="sxs-lookup"><span data-stu-id="0b33d-115">You can opt out members from serialization by using the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>.</span></span> <span data-ttu-id="0b33d-116">还可以使用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性显式创建数据协定。</span><span class="sxs-lookup"><span data-stu-id="0b33d-116">You can also explicitly create a data contract by using <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="0b33d-117">正常情况下可通过将 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用到该类型来完成该任务。</span><span class="sxs-lookup"><span data-stu-id="0b33d-117">This is normally done by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="0b33d-118">可以将此属性应用到类、结构和枚举。</span><span class="sxs-lookup"><span data-stu-id="0b33d-118">This attribute can be applied to classes, structures, and enumerations.</span></span> <span data-ttu-id="0b33d-119">然后必须将 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性应用到数据协定类型的每个成员，以指示这些成员为数据成员， \*\* 即应进行序列化。</span><span class="sxs-lookup"><span data-stu-id="0b33d-119">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute must then be applied to each member of the data contract type to indicate that it is a *data member*, that is, it should be serialized.</span></span> <span data-ttu-id="0b33d-120">有关详细信息，请参阅[可序列化类型](serializable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0b33d-120">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b33d-121">示例</span><span class="sxs-lookup"><span data-stu-id="0b33d-121">Example</span></span>  
 <span data-ttu-id="0b33d-122">下面的示例演示已经显式应用了 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 属性的服务协定（接口）。</span><span class="sxs-lookup"><span data-stu-id="0b33d-122">The following example shows a service contract (an interface) to which the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes have been explicitly applied.</span></span> <span data-ttu-id="0b33d-123">该示例演示基元类型不要求数据协定，而复杂类型却对此有要求。</span><span class="sxs-lookup"><span data-stu-id="0b33d-123">The example shows that primitive types do not require a data contract, while a complex type does.</span></span>  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 <span data-ttu-id="0b33d-124">下面的示例演示如何通过将 `MyTypes.PurchaseOrder` 和 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用于类及其成员来创建 <xref:System.Runtime.Serialization.DataMemberAttribute> 类型的数据协定。</span><span class="sxs-lookup"><span data-stu-id="0b33d-124">The following example shows how a data contract for the `MyTypes.PurchaseOrder` type is created by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a><span data-ttu-id="0b33d-125">备注</span><span class="sxs-lookup"><span data-stu-id="0b33d-125">Notes</span></span>  
 <span data-ttu-id="0b33d-126">下面的注释提供在创建数据协定时需要考虑的事项：</span><span class="sxs-lookup"><span data-stu-id="0b33d-126">The following notes provide items to consider when creating data contracts:</span></span>  
  
- <span data-ttu-id="0b33d-127">仅当用于未标记的类型时，才接受 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="0b33d-127">The <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute is only honored when used with unmarked types.</span></span> <span data-ttu-id="0b33d-128">这包括未使用 <xref:System.Runtime.Serialization.DataContractAttribute>、 <xref:System.SerializableAttribute>、 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>或 <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性之一标记的类型，或通过任何其他方式（如 <xref:System.Xml.Serialization.IXmlSerializable>）标记为可序列化的类型。</span><span class="sxs-lookup"><span data-stu-id="0b33d-128">This includes types that are not marked with one of the <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, or <xref:System.Runtime.Serialization.EnumMemberAttribute> attributes, or marked as serializable by any other means (such as <xref:System.Xml.Serialization.IXmlSerializable>).</span></span>  
  
- <span data-ttu-id="0b33d-129">可以将 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (Attribute) 应用于字段和属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="0b33d-129">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to fields, and properties.</span></span>  
  
- <span data-ttu-id="0b33d-130">成员可访问性级别（internal、private、protected 或 public）对数据协定无任何影响。</span><span class="sxs-lookup"><span data-stu-id="0b33d-130">Member accessibility levels (internal, private, protected, or public) do not affect the data contract in any way.</span></span>  
  
- <span data-ttu-id="0b33d-131">如果将 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性应用于静态成员，则将忽略该属性。</span><span class="sxs-lookup"><span data-stu-id="0b33d-131">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is ignored if it is applied to static members.</span></span>  
  
- <span data-ttu-id="0b33d-132">在序列化期间，为属性数据成员调用 property-get 代码来获取要序列化的属性的值。</span><span class="sxs-lookup"><span data-stu-id="0b33d-132">During serialization, property-get code is called for property data members to get the value of the properties to be serialized.</span></span>  
  
- <span data-ttu-id="0b33d-133">在反序列化期间，首先创建一个未初始化的对象，而不在该类型上调用任何构造函数。</span><span class="sxs-lookup"><span data-stu-id="0b33d-133">During deserialization, an uninitialized object is first created, without calling any constructors on the type.</span></span> <span data-ttu-id="0b33d-134">然后反序列化所有数据成员。</span><span class="sxs-lookup"><span data-stu-id="0b33d-134">Then all data members are deserialized.</span></span>  
  
- <span data-ttu-id="0b33d-135">在反序列化期间，为属性数据成员调用 property-set 代码，将属性设置为要反序列化的值。</span><span class="sxs-lookup"><span data-stu-id="0b33d-135">During deserialization, property-set code is called for property data members to set the properties to the value being deserialized.</span></span>  
  
- <span data-ttu-id="0b33d-136">对于将要生效的数据协定，它必须能序列化其所有数据成员。</span><span class="sxs-lookup"><span data-stu-id="0b33d-136">For a data contract to be valid, it must be possible to serialize all of its data members.</span></span> <span data-ttu-id="0b33d-137">有关可序列化类型的完整列表，请参阅 [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md)。</span><span class="sxs-lookup"><span data-stu-id="0b33d-137">For a full list of serializable types, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span>  
  
     <span data-ttu-id="0b33d-138">泛型类型的处理方式与非泛型类型完全相同。</span><span class="sxs-lookup"><span data-stu-id="0b33d-138">Generic types are handled in exactly the same way as non-generic types.</span></span> <span data-ttu-id="0b33d-139">泛型参数无特殊要求。</span><span class="sxs-lookup"><span data-stu-id="0b33d-139">There are no special requirements for generic parameters.</span></span> <span data-ttu-id="0b33d-140">例如，请注意以下类型：</span><span class="sxs-lookup"><span data-stu-id="0b33d-140">For example, consider the following type.</span></span>  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 <span data-ttu-id="0b33d-141">无论用于泛型类型参数 (`T`) 的类型能否序列化，此类型都可序列化。</span><span class="sxs-lookup"><span data-stu-id="0b33d-141">This type is serializable whether the type used for the generic type parameter (`T`) is serializable or not.</span></span> <span data-ttu-id="0b33d-142">因为它必须能序列化所有数据成员，所以下面的类型仅在泛型类型参数也可序列化时才可序列化，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="0b33d-142">Because it must be possible to serialize all data members, the following type is serializable only if the generic type parameter is also serializable, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 <span data-ttu-id="0b33d-143">有关定义数据协定的 WCF 服务的完整代码示例，请参阅 [Basic Data Contract](../samples/basic-data-contract.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="0b33d-143">For a complete code sample of a WCF service that defines a data contract see the [Basic Data Contract](../samples/basic-data-contract.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b33d-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="0b33d-144">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="0b33d-145">可序列化类型</span><span class="sxs-lookup"><span data-stu-id="0b33d-145">Serializable Types</span></span>](serializable-types.md)
- [<span data-ttu-id="0b33d-146">数据协定名称</span><span class="sxs-lookup"><span data-stu-id="0b33d-146">Data Contract Names</span></span>](data-contract-names.md)
- [<span data-ttu-id="0b33d-147">数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="0b33d-147">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="0b33d-148">数据成员顺序</span><span class="sxs-lookup"><span data-stu-id="0b33d-148">Data Member Order</span></span>](data-member-order.md)
- [<span data-ttu-id="0b33d-149">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="0b33d-149">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="0b33d-150">向前兼容的数据协定</span><span class="sxs-lookup"><span data-stu-id="0b33d-150">Forward-Compatible Data Contracts</span></span>](forward-compatible-data-contracts.md)
- [<span data-ttu-id="0b33d-151">数据协定版本管理</span><span class="sxs-lookup"><span data-stu-id="0b33d-151">Data Contract Versioning</span></span>](data-contract-versioning.md)
- [<span data-ttu-id="0b33d-152">版本容错序列化回调</span><span class="sxs-lookup"><span data-stu-id="0b33d-152">Version-Tolerant Serialization Callbacks</span></span>](version-tolerant-serialization-callbacks.md)
- [<span data-ttu-id="0b33d-153">数据成员默认值</span><span class="sxs-lookup"><span data-stu-id="0b33d-153">Data Member Default Values</span></span>](data-member-default-values.md)
- [<span data-ttu-id="0b33d-154">数据协定序列化程序支持的类型</span><span class="sxs-lookup"><span data-stu-id="0b33d-154">Types Supported by the Data Contract Serializer</span></span>](types-supported-by-the-data-contract-serializer.md)
- [<span data-ttu-id="0b33d-155">如何：创建类或结构的基本数据协定</span><span class="sxs-lookup"><span data-stu-id="0b33d-155">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
