---
title: 如何：创建类或结构的基本数据协定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 0fd7bbea4d6e8d315566aa798ed89a0fd2657f58
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599030"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="2c5dc-102">如何：创建类或结构的基本数据协定</span><span class="sxs-lookup"><span data-stu-id="2c5dc-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="2c5dc-103">本主题演示使用类或结构创建数据协定的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="2c5dc-104">有关数据协定及其使用方式的详细信息，请参阅[使用数据协定](using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-104">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="2c5dc-105">有关演练创建基本 Windows Communication Foundation （WCF）服务和客户端的步骤的教程，请参阅[入门教程](../getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="2c5dc-106">对于包含基本服务和客户端的工作示例应用程序，请参阅[基本数据协定](../samples/basic-data-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="2c5dc-107">创建类或结构的基本数据协定</span><span class="sxs-lookup"><span data-stu-id="2c5dc-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="2c5dc-108">通过将 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用于类来声明该类型具有数据协定。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="2c5dc-109">请注意，包括不带属性的公共类型在内的所有公共类型都是可序列化的。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="2c5dc-110">如果不存在 <xref:System.Runtime.Serialization.DataContractSerializer> 属性，<xref:System.Runtime.Serialization.DataContractAttribute> 将推断出一个数据协定。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="2c5dc-111">有关详细信息，请参阅[可序列化类型](serializable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-111">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="2c5dc-112">通过将 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (Attribute) 应用于每个成员来定义要序列化的成员（属性 (Property)、字段或事件）。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="2c5dc-113">这些成员称为数据成员。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-113">These members are called data members.</span></span> <span data-ttu-id="2c5dc-114">默认情况下，所有公共类型都是可序列化的。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-114">By default, all public types are serializable.</span></span> <span data-ttu-id="2c5dc-115">有关详细信息，请参阅[可序列化类型](serializable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-115">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2c5dc-116">您可以将 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性应用于私有字段，这会导致向其他人公开此数据。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="2c5dc-117">请确保成员不包含敏感数据。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c5dc-118">示例</span><span class="sxs-lookup"><span data-stu-id="2c5dc-118">Example</span></span>  
 <span data-ttu-id="2c5dc-119">下面的示例演示如何通过将 `Person` 和 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用于类及其成员来创建 <xref:System.Runtime.Serialization.DataMemberAttribute> 类型的数据协定。</span><span class="sxs-lookup"><span data-stu-id="2c5dc-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2c5dc-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c5dc-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="2c5dc-121">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="2c5dc-121">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="2c5dc-122">入门教程</span><span class="sxs-lookup"><span data-stu-id="2c5dc-122">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="2c5dc-123">入门</span><span class="sxs-lookup"><span data-stu-id="2c5dc-123">Getting Started</span></span>](../samples/getting-started-sample.md)
