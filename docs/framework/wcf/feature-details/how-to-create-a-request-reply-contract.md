---
title: 如何：创建请求-答复协定
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593433"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="4ccba-102">如何：创建请求-答复协定</span><span class="sxs-lookup"><span data-stu-id="4ccba-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="4ccba-103">请求-答复协定指定返回答复的方法。</span><span class="sxs-lookup"><span data-stu-id="4ccba-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="4ccba-104">必须根据此协定的条款发送答复并与请求相关联。</span><span class="sxs-lookup"><span data-stu-id="4ccba-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="4ccba-105">即使该方法不返回任何答复（采用 C# 语言时，返回 `void`，采用 Visual Basic 语言时，返回 `Sub`），基础结构也将创建一条空消息并将其发送给调用方。</span><span class="sxs-lookup"><span data-stu-id="4ccba-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="4ccba-106">若要防止发送空答复消息，请对操作使用单向协定。</span><span class="sxs-lookup"><span data-stu-id="4ccba-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="4ccba-107">创建请求-答复协定</span><span class="sxs-lookup"><span data-stu-id="4ccba-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="4ccba-108">用所选编程语言创建接口。</span><span class="sxs-lookup"><span data-stu-id="4ccba-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="4ccba-109">将 <xref:System.ServiceModel.ServiceContractAttribute> 特性应用于该接口。</span><span class="sxs-lookup"><span data-stu-id="4ccba-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="4ccba-110">将 <xref:System.ServiceModel.OperationContractAttribute> 特性应用于客户端可调用的每个方法。</span><span class="sxs-lookup"><span data-stu-id="4ccba-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="4ccba-111">可选。</span><span class="sxs-lookup"><span data-stu-id="4ccba-111">Optional.</span></span> <span data-ttu-id="4ccba-112">将 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性的值设置为 `true`，以防止发送空答复消息。</span><span class="sxs-lookup"><span data-stu-id="4ccba-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="4ccba-113">默认情况下，所有操作均是请求-答复协定。</span><span class="sxs-lookup"><span data-stu-id="4ccba-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccba-114">示例</span><span class="sxs-lookup"><span data-stu-id="4ccba-114">Example</span></span>  
 <span data-ttu-id="4ccba-115">下面的示例为提供 `Add` 和 `Subtract` 方法的计算器服务定义一个协定。</span><span class="sxs-lookup"><span data-stu-id="4ccba-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="4ccba-116">`Multiply` 方法不是协定的一部分，因为它没有通过 <xref:System.ServiceModel.OperationContractAttribute> 类进行标记，因此不可以由客户端访问。</span><span class="sxs-lookup"><span data-stu-id="4ccba-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="4ccba-117">有关如何指定操作协定的详细信息，请参阅 <xref:System.ServiceModel.OperationContractAttribute> 类和 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="4ccba-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="4ccba-118">在部署了服务之后，应用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 特性会导致在 Web 服务描述语言 (WSDL) 文档中自动生成服务协定定义。</span><span class="sxs-lookup"><span data-stu-id="4ccba-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="4ccba-119">通过将 `?wsdl` 追加到该服务的 HTTP 基址，可下载此文档。</span><span class="sxs-lookup"><span data-stu-id="4ccba-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="4ccba-120">例如 `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="4ccba-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ccba-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ccba-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="4ccba-122">设计服务协定</span><span class="sxs-lookup"><span data-stu-id="4ccba-122">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="4ccba-123">如何：创建双工协定</span><span class="sxs-lookup"><span data-stu-id="4ccba-123">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
