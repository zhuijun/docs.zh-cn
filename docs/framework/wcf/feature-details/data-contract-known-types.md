---
title: 数据协定已知类型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: b7d78def4d656dea59af5400c7ed7deeef28cd0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597444"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="d3761-102">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="d3761-102">Data Contract Known Types</span></span>
<span data-ttu-id="d3761-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> 类允许您预先指定应该在反序列化期间包括在考虑范围内的类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="d3761-104">有关工作示例，请参阅 [Known Types](../samples/known-types.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="d3761-104">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="d3761-105">通常，在客户端和服务之间传递参数和返回值时，这两个终结点共享要传输的数据的所有数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="d3761-106">但是，在以下情况下并非如此：</span><span class="sxs-lookup"><span data-stu-id="d3761-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="d3761-107">已发送的数据协定派生自预期的数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="d3761-108">有关详细信息，请参阅[数据协定等效](data-contract-equivalence.md)性中有关继承的部分。</span><span class="sxs-lookup"><span data-stu-id="d3761-108">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="d3761-109">在该情况下，传输的数据没有与接收终结点所预期相同的数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="d3761-110">要传输的信息的声明类型是接口，而非类、结构或枚举。</span><span class="sxs-lookup"><span data-stu-id="d3761-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="d3761-111">因此，无法预先知道实际发送了实现接口的哪个类型，接收终结点就无法预先确定已传输数据的数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="d3761-112">要传输的信息的声明类型是 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="d3761-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="d3761-113">由于每个类型都继承自 <xref:System.Object>，而且无法预先知道实际发送了哪个类型，因此接收终结点无法预先确定已传输数据的数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="d3761-114">这是第一个项的特殊情况：每个数据协定都源自为 <xref:System.Object>生成的默认空数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="d3761-115">某些类型（包括 .NET Framework 类型）具有上述三种类别之一中的成员。</span><span class="sxs-lookup"><span data-stu-id="d3761-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="d3761-116">例如， <xref:System.Collections.Hashtable> 使用 <xref:System.Object> 在哈希表中存储实际对象。</span><span class="sxs-lookup"><span data-stu-id="d3761-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="d3761-117">在序列化这些类型时，接收方无法预先确定这些成员的数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="d3761-118">KnownTypeAttribute 类</span><span class="sxs-lookup"><span data-stu-id="d3761-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="d3761-119">当数据到达接收终结点时，WCF 运行时尝试将数据反序列化到公共语言运行时（CLR）类型的实例中。</span><span class="sxs-lookup"><span data-stu-id="d3761-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="d3761-120">通过首先检查传入消息选择为反序列化而实例化的类型，以确定消息内容遵循的数据协定。</span><span class="sxs-lookup"><span data-stu-id="d3761-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="d3761-121">然后反序列化引擎尝试查找实现与消息内容兼容的数据协定的 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="d3761-122">反序列化引擎在此过程中允许的侯选类型集称为反序列化程序的“已知类型”集。</span><span class="sxs-lookup"><span data-stu-id="d3761-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="d3761-123">让反序列化引擎了解某个类型的一种方法是使用 <xref:System.Runtime.Serialization.KnownTypeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="d3761-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="d3761-124">不能将属性应用于单个数据成员，只能将它应用于整个数据协定类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="d3761-125">将属性应用于可能为类或结构的“外部类型” \*\* 。</span><span class="sxs-lookup"><span data-stu-id="d3761-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="d3761-126">在其最基本的用法中，应用属性会将类型指定为“已知类型”。</span><span class="sxs-lookup"><span data-stu-id="d3761-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="d3761-127">只要反序列化外部类型的对象或通过其成员引用的任何对象，这就会导致已知类型成为已知类型集的一部分。</span><span class="sxs-lookup"><span data-stu-id="d3761-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="d3761-128">可以将多个 <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性应用于同一类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="d3761-129">已知类型和基元</span><span class="sxs-lookup"><span data-stu-id="d3761-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="d3761-130">基元类型以及被视为基元的某些类型（例如， <xref:System.DateTime> 和 <xref:System.Xml.XmlElement>）始终是“已知”的，且从来不必通过此机制进行添加。</span><span class="sxs-lookup"><span data-stu-id="d3761-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="d3761-131">但是，必须显式添加基元类型的数组。</span><span class="sxs-lookup"><span data-stu-id="d3761-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="d3761-132">大多数集合被视为等效于数组。</span><span class="sxs-lookup"><span data-stu-id="d3761-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="d3761-133">（非泛型集合被视为等效于 <xref:System.Object>的数组）。</span><span class="sxs-lookup"><span data-stu-id="d3761-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="d3761-134">有关使用基元、基元数组和基元集合的示例，请参见示例 4。</span><span class="sxs-lookup"><span data-stu-id="d3761-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3761-135">与其他基元类型不同， <xref:System.DateTimeOffset> 结构默认情况下不是已知类型，因此必须将它手动添加到已知类型列表。</span><span class="sxs-lookup"><span data-stu-id="d3761-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d3761-136">示例</span><span class="sxs-lookup"><span data-stu-id="d3761-136">Examples</span></span>  
 <span data-ttu-id="d3761-137">下面的示例说明如何使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 类。</span><span class="sxs-lookup"><span data-stu-id="d3761-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="d3761-138">示例 1</span><span class="sxs-lookup"><span data-stu-id="d3761-138">Example 1</span></span>  
 <span data-ttu-id="d3761-139">有三个具有继承关系的类。</span><span class="sxs-lookup"><span data-stu-id="d3761-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="d3761-140">如果 `CompanyLogo` 成员设置为 `ShapeOfLogo` 或 `CircleType` 对象，则可以序列化下面的 `TriangleType` 类，而不能对其进行反序列化，因为反序列化引擎无法识别具有数据协定名称“Circle”或“Triangle”的任何类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="d3761-141">在下面的代码中演示了编写 `CompanyLogo` 类型的正确方法。</span><span class="sxs-lookup"><span data-stu-id="d3761-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="d3761-142">只要反序列化外部类型 `CompanyLogo2` ，反序列化引擎就会了解有关 `CircleType` 和 `TriangleType` ，因此能够查找“Circle”和“Triangle”数据协定的匹配类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="d3761-143">示例 2</span><span class="sxs-lookup"><span data-stu-id="d3761-143">Example 2</span></span>  
 <span data-ttu-id="d3761-144">在下面的示例中，尽管 `CustomerTypeA` 和 `CustomerTypeB` 都具有 `Customer` 数据协定，但是只要反序列化 `CustomerTypeB` 就会创建 `PurchaseOrder` 的实例，因为只有 `CustomerTypeB` 对反序列化引擎是已知的。</span><span class="sxs-lookup"><span data-stu-id="d3761-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="d3761-145">示例 3</span><span class="sxs-lookup"><span data-stu-id="d3761-145">Example 3</span></span>  
 <span data-ttu-id="d3761-146">在下面的示例中， <xref:System.Collections.Hashtable> 将其内容在内部存储为 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="d3761-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="d3761-147">若要成功反序列化哈希表，反序列化引擎必须知道那里可能出现的一组可能类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="d3761-148">在这种情况下，我们预先知道只有 `Book` 和 `Magazine` 对象存储在 `Catalog`中，因此使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性添加它们。</span><span class="sxs-lookup"><span data-stu-id="d3761-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="d3761-149">示例 4</span><span class="sxs-lookup"><span data-stu-id="d3761-149">Example 4</span></span>  
 <span data-ttu-id="d3761-150">在下面的示例中，数据协定存储一个数字和要对该数字执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d3761-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="d3761-151">`Numbers` 数据成员可以是整数、整数数组或包含整数的 <xref:System.Collections.Generic.List%601> 。</span><span class="sxs-lookup"><span data-stu-id="d3761-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d3761-152">仅当使用 SVCUTIL.EXE 来生成 WCF 代理时，此方法才能在客户端使用。</span><span class="sxs-lookup"><span data-stu-id="d3761-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="d3761-153">SVCUTIL.EXE 从包含任何已知类型的服务中检索元数据。</span><span class="sxs-lookup"><span data-stu-id="d3761-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="d3761-154">如果没有此信息，客户端将不能反序列化该类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="d3761-155">这是应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="d3761-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="d3761-156">已知类型、继承和接口</span><span class="sxs-lookup"><span data-stu-id="d3761-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="d3761-157">使用 `KnownTypeAttribute` 属性将已知类型与特定类型关联时，已知类型也与该类型的所有派生类型关联。</span><span class="sxs-lookup"><span data-stu-id="d3761-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="d3761-158">例如，请参见下面的代码。</span><span class="sxs-lookup"><span data-stu-id="d3761-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="d3761-159">`DoubleDrawing` 类无需 `KnownTypeAttribute` 属性即可在 `Square` 字段中使用 `Circle` 和 `AdditionalShape` ，因为基类 (`Drawing`) 已经应用这些属性。</span><span class="sxs-lookup"><span data-stu-id="d3761-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="d3761-160">已知类型只能与类和结构关联，而不能与接口关联。</span><span class="sxs-lookup"><span data-stu-id="d3761-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="d3761-161">使用开放式泛型方法的已知类型</span><span class="sxs-lookup"><span data-stu-id="d3761-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="d3761-162">可能需要将泛型类型作为已知类型添加。</span><span class="sxs-lookup"><span data-stu-id="d3761-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="d3761-163">但是，不能将开放式泛型类型作为参数传递到 `KnownTypeAttribute` 属性。</span><span class="sxs-lookup"><span data-stu-id="d3761-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="d3761-164">通过使用替代机制可以解决此问题：编写一个返回要添加到已知类型集合的类型列表的方法。</span><span class="sxs-lookup"><span data-stu-id="d3761-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="d3761-165">然后将方法名称指定为 `KnownTypeAttribute` 属性的字符串参数（由于某些限制所致）。</span><span class="sxs-lookup"><span data-stu-id="d3761-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="d3761-166">方法必须存在于应用 `KnownTypeAttribute` 属性的类型上，不得接受参数，且必须返回可以分配给 <xref:System.Collections.IEnumerable> 的 <xref:System.Type>的对象。</span><span class="sxs-lookup"><span data-stu-id="d3761-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="d3761-167">不能将具有方法名称的 `KnownTypeAttribute` 属性与实际类型在同一类型上的 `KnownTypeAttribute` 属性组合在一起。</span><span class="sxs-lookup"><span data-stu-id="d3761-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="d3761-168">此外，不能将具有方法名称的多个 `KnownTypeAttribute` 应用于同一类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="d3761-169">请参见下面的类。</span><span class="sxs-lookup"><span data-stu-id="d3761-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="d3761-170">`theDrawing` 字段包含泛型类 `ColorDrawing` 和泛型类 `BlackAndWhiteDrawing`的实例，这两个泛型类都是从泛型类 `Drawing`继承的。</span><span class="sxs-lookup"><span data-stu-id="d3761-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="d3761-171">通常，必须将它们添加到已知类型，但下面不是有效的属性语法。</span><span class="sxs-lookup"><span data-stu-id="d3761-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="d3761-172">因此，必须创建一个方法以返回这些类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="d3761-173">在下面的代码中演示了编写此类型的正确方法。</span><span class="sxs-lookup"><span data-stu-id="d3761-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="d3761-174">添加已知类型的其他方法</span><span class="sxs-lookup"><span data-stu-id="d3761-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="d3761-175">此外，可以通过配置文件添加已知类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="d3761-176">如果不控制需要已知类型才能正确反序列化的类型（例如，将第三方类型库与 Windows Communication Foundation （WCF）结合使用，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="d3761-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="d3761-177">下面的配置文件演示如何在配置文件中指定已知类型。</span><span class="sxs-lookup"><span data-stu-id="d3761-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="d3761-178">在前面的配置文件中，名为 `MyCompany.Library.Shape` 的数据协定类型被声明具有已知类型 `MyCompany.Library.Circle` 。</span><span class="sxs-lookup"><span data-stu-id="d3761-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3761-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3761-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="d3761-180">已知类型</span><span class="sxs-lookup"><span data-stu-id="d3761-180">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="d3761-181">数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="d3761-181">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="d3761-182">设计服务协定</span><span class="sxs-lookup"><span data-stu-id="d3761-182">Designing Service Contracts</span></span>](../designing-service-contracts.md)
