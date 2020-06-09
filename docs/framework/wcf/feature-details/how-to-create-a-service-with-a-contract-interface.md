---
title: 如何：使用协定接口创建服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597158"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="d7c74-102">如何：使用协定接口创建服务</span><span class="sxs-lookup"><span data-stu-id="d7c74-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="d7c74-103">创建 Windows Communication Foundation （WCF）协定的首选方式是使用接口。</span><span class="sxs-lookup"><span data-stu-id="d7c74-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="d7c74-104">此协定指定访问服务提供的操作所必需的消息的集合和结构。</span><span class="sxs-lookup"><span data-stu-id="d7c74-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="d7c74-105">此接口通过将 <xref:System.ServiceModel.ServiceContractAttribute> 类应用到该接口并将 <xref:System.ServiceModel.OperationContractAttribute> 类应用到要公开的方法来定义输入和输出类型。</span><span class="sxs-lookup"><span data-stu-id="d7c74-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="d7c74-106">有关服务协定的详细信息，请参阅[设计服务协定](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c74-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="d7c74-107">使用接口创建 WCF 协定</span><span class="sxs-lookup"><span data-stu-id="d7c74-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="d7c74-108">使用 Visual Basic、c # 或任何其他公共语言运行时语言创建新的接口。</span><span class="sxs-lookup"><span data-stu-id="d7c74-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="d7c74-109">将 <xref:System.ServiceModel.ServiceContractAttribute> 类应用到该接口。</span><span class="sxs-lookup"><span data-stu-id="d7c74-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="d7c74-110">定义该接口中的方法。</span><span class="sxs-lookup"><span data-stu-id="d7c74-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="d7c74-111">将类应用于 <xref:System.ServiceModel.OperationContractAttribute> 必须作为公共 WCF 协定的一部分公开的每个方法。</span><span class="sxs-lookup"><span data-stu-id="d7c74-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7c74-112">示例</span><span class="sxs-lookup"><span data-stu-id="d7c74-112">Example</span></span>  
 <span data-ttu-id="d7c74-113">下面的代码示例演示一个定义服务协定的接口。</span><span class="sxs-lookup"><span data-stu-id="d7c74-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="d7c74-114">默认情况下，应用了 <xref:System.ServiceModel.OperationContractAttribute> 类的方法使用请求-答复消息模式。</span><span class="sxs-lookup"><span data-stu-id="d7c74-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="d7c74-115">有关此消息模式的详细信息，请参阅[如何：创建请求-答复协定](how-to-create-a-request-reply-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c74-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="d7c74-116">您还可以通过设置属性 (Attribute) 的属性 (Property) 来创建和使用其他消息模式。</span><span class="sxs-lookup"><span data-stu-id="d7c74-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="d7c74-117">有关更多示例，请参阅[如何：创建单向协定](how-to-create-a-one-way-contract.md)和[如何：创建双工协定](how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c74-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c74-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7c74-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
