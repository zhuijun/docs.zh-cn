---
title: 数据协定等效性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: b96a32f5e11ed4808f8f35d02802afd1f48c3072
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601317"
---
# <a name="data-contract-equivalence"></a><span data-ttu-id="ef1fa-102">数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="ef1fa-102">Data Contract Equivalence</span></span>
<span data-ttu-id="ef1fa-103">对于客户端要将某种类型的数据成功发送到服务，或者服务要将数据成功发送到客户端的情况，接收端上并不一定必须存在此发送数据类型。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-103">For a client to successfully send data of a certain type to a service, or a service to successfully send data to a client, the sent type does not necessarily have to exist on the receiving end.</span></span> <span data-ttu-id="ef1fa-104">唯一的需求是两种类型的数据协定应该等效。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-104">The only requirement is that the data contracts of both types be equivalent.</span></span> <span data-ttu-id="ef1fa-105">（有时不需要严格等效性，如[数据协定版本控制](data-contract-versioning.md)中所述。）</span><span class="sxs-lookup"><span data-stu-id="ef1fa-105">(Sometimes, strict equivalence is not required, as discussed in [Data Contract Versioning](data-contract-versioning.md).)</span></span>  
  
 <span data-ttu-id="ef1fa-106">要使数据协定等效，其命名空间和名称必须相同。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-106">For data contracts to be equivalent, they must have the same namespace and name.</span></span> <span data-ttu-id="ef1fa-107">此外，某一端上的每个数据成员还必须在另一端上具有等效的数据成员。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-107">Additionally, each data member on one side must have an equivalent data member on the other side.</span></span>  
  
 <span data-ttu-id="ef1fa-108">要使数据成员等效，其名称必须相同。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-108">For data members to be equivalent, they must have the same name.</span></span> <span data-ttu-id="ef1fa-109">此外，它们还必须表示同一类型的数据，也就是说，其数据协定必须等效。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-109">Additionally, they must represent the same type of data; that is, their data contracts must be equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef1fa-110">请注意，数据协定名称和命名空间以及数据成员名称均区分大小写。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-110">Note that data contract names and namespaces, as well as data member names, are case-sensitive.</span></span>  
  
 <span data-ttu-id="ef1fa-111">有关数据协定名称和命名空间以及数据成员名称的详细信息，请参阅[数据协定名称](data-contract-names.md)。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-111">For more information about data contract names and namespaces, as well as data member names, see [Data Contract Names](data-contract-names.md).</span></span>  
  
 <span data-ttu-id="ef1fa-112">如果同一端（发送方或接收方）存在两种类型，而其数据协定又不等效（例如，它们的数据成员不同），则不应为它们指定相同的名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-112">If two types exist on the same side (sender or receiver) and their data contracts are not equivalent (for example, they have different data members), you should not give them the same name and namespace.</span></span> <span data-ttu-id="ef1fa-113">否则，可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-113">Doing so may cause exceptions to be thrown.</span></span>  
  
 <span data-ttu-id="ef1fa-114">以下类型的数据协定是等效的：</span><span class="sxs-lookup"><span data-stu-id="ef1fa-114">The data contracts for the following types are equivalent:</span></span>  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a><span data-ttu-id="ef1fa-115">数据成员顺序和数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="ef1fa-115">Data Member Order and Data Contract equivalence</span></span>  
 <span data-ttu-id="ef1fa-116">使用 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 类的 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性可能会影响数据协定等效性。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-116">Using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> class may affect data contract equivalence.</span></span> <span data-ttu-id="ef1fa-117">其成员必须以相同顺序出现，数据协定才能等效。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-117">The data contracts must have members that appear in the same order to be equivalent.</span></span> <span data-ttu-id="ef1fa-118">默认顺序是按字母顺序。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-118">The default order is alphabetical.</span></span> <span data-ttu-id="ef1fa-119">有关详细信息，请参阅[数据成员顺序](data-member-order.md)。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-119">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="ef1fa-120">例如，以下代码生成的数据协定是等效的。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-120">For example, the following code results in equivalent data contracts.</span></span>  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 <span data-ttu-id="ef1fa-121">但是，以下代码生成的数据协定不是等效的。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-121">However, the following does not result in an equivalent data contract.</span></span>  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a><span data-ttu-id="ef1fa-122">继承、接口和数据协定等效性</span><span class="sxs-lookup"><span data-stu-id="ef1fa-122">Inheritance, Interfaces, and Data Contract Equivalence</span></span>  
 <span data-ttu-id="ef1fa-123">确定等效性时，对于从其他数据协定继承的数据协定，将被视为一个包含所有基类型的数据成员的数据协定。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-123">When determining equivalence, a data contract that inherits from another data contract is treated as if it is just one data contract that includes all of the data members from the base type.</span></span> <span data-ttu-id="ef1fa-124">请记住，数据成员的顺序必须匹配，并且基类型成员排在派生类型成员之前。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-124">Keep in mind that the order of the data members must match and that base type members precede derived type members in the order.</span></span> <span data-ttu-id="ef1fa-125">此外，如下面的代码示例所示，如果两个数据成员的顺序值相同，则这两个数据成员的顺序为按字母顺序。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-125">Furthermore, if, as in the following code example, two data members have the same order value, the ordering for those data members is alphabetical.</span></span> <span data-ttu-id="ef1fa-126">有关详细信息，请参阅[数据成员顺序](data-member-order.md)。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-126">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="ef1fa-127">在下面的示例中，类型为 `Employee` 的数据协定等效于类型为 `Worker` 的数据协定。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-127">In the following example, the data contract for type `Employee` is equivalent to the data contract for the type `Worker`.</span></span>  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 <span data-ttu-id="ef1fa-128">在客户端和服务之间传递参数和返回值时，如果接收终结点要求来自派生类的数据协定，则不能发送来自基类的数据协定。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-128">When passing parameters and return values between a client and a service, a data contract from a base class cannot be sent when the receiving endpoint expects a data contract from a derived class.</span></span> <span data-ttu-id="ef1fa-129">这一点符合面向对象的编程原则。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-129">This is in accordance with object-oriented programming tenets.</span></span> <span data-ttu-id="ef1fa-130">在前面的示例中， `Person` 不能在需要时发送类型的对象 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-130">In the previous example, an object of type `Person` cannot be sent when an `Employee` is expected.</span></span>  
  
 <span data-ttu-id="ef1fa-131">如果要求来自基类的数据协定，则可发送来自派生类的数据协定，但前提是接收终结点通过 <xref:System.Runtime.Serialization.KnownTypeAttribute>“知道”该派生类型。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-131">A data contract from a derived class can be sent when a data contract from a base class is expected, but only if the receiving endpoint "knows" of the derived type using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="ef1fa-132">有关详细信息，请参阅[数据协定已知类型](data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-132">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="ef1fa-133">在前面的示例中，当要求 `Employee` 时，可以发送 `Person` 类型的对象，但前提是接收方代码使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 将它包含在已知类型列表中。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-133">In the previous example, an object of type `Employee` can be sent when a `Person` is expected, but only if the receiver code employs the <xref:System.Runtime.Serialization.KnownTypeAttribute> to include it in the list of known types.</span></span>  
  
 <span data-ttu-id="ef1fa-134">在应用程序之间传递参数和返回值时，如果所需类型为接口，则等效于所需类型为 <xref:System.Object> 类型。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-134">When passing parameters and return values between applications, if the expected type is an interface, it is equivalent to the expected type being of type <xref:System.Object>.</span></span> <span data-ttu-id="ef1fa-135">由于每种类型最终都派生自 <xref:System.Object>，因此所有数据协定最终都派生自 <xref:System.Object> 的数据协定。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-135">Because every type ultimately derives from <xref:System.Object>, every data contract ultimately derives from the data contract for <xref:System.Object>.</span></span> <span data-ttu-id="ef1fa-136">这样，在要求使用接口时，就可以传递任何数据协定类型。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-136">Thus, any data contract type can be passed when an interface is expected.</span></span> <span data-ttu-id="ef1fa-137">若要成功使用接口，还需要执行其他步骤;有关详细信息，请参阅[数据协定已知类型](data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ef1fa-137">Additional steps are required to successfully work with interfaces; for more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1fa-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef1fa-138">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="ef1fa-139">数据成员顺序</span><span class="sxs-lookup"><span data-stu-id="ef1fa-139">Data Member Order</span></span>](data-member-order.md)
- [<span data-ttu-id="ef1fa-140">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="ef1fa-140">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="ef1fa-141">数据协定名称</span><span class="sxs-lookup"><span data-stu-id="ef1fa-141">Data Contract Names</span></span>](data-contract-names.md)
