---
title: 如何：创建双工协定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598978"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="0ef8f-102">如何：创建双工协定</span><span class="sxs-lookup"><span data-stu-id="0ef8f-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="0ef8f-103">本主题演示了创建使用双工（双向）协定的方法所需的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="0ef8f-104">双工协定使得客户端和服务器可以独立地相互通信，这样双方都可以启动对另一方的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="0ef8f-105">双工协定是可供 Windows Communication Foundation （WCF）服务使用的三种消息模式之一。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="0ef8f-106">另外两种消息模式是单向模式和请求-答复模式。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="0ef8f-107">双工协定由客户端和服务器之间的两个单向协定组成，并且不需要方法调用是相关的。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="0ef8f-108">当服务必须向客户端查询更多信息或在客户端上显式引发事件时，使用这种协定。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="0ef8f-109">有关创建双工协定的客户端应用程序的详细信息，请参阅[如何：使用双工协定访问服务](how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="0ef8f-110">有关工作示例，请参阅[双工](../samples/duplex.md)示例。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-110">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="0ef8f-111">创建双工协定</span><span class="sxs-lookup"><span data-stu-id="0ef8f-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="0ef8f-112">创建组成双工协定的服务器方的接口。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="0ef8f-113">将 <xref:System.ServiceModel.ServiceContractAttribute> 类应用到该接口。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="0ef8f-114">在接口中声明方法签名。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="0ef8f-115">将 <xref:System.ServiceModel.OperationContractAttribute> 类应用于每个方法签名，该方法签名必须是公共协定的一部分。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="0ef8f-116">创建回调接口以定义服务可以在客户端上调用的操作组。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="0ef8f-117">在回调接口中声明方法签名。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="0ef8f-118">将 <xref:System.ServiceModel.OperationContractAttribute> 类应用于每个方法签名，该方法签名必须是公共协定的一部分。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="0ef8f-119">通过将主接口中的 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 属性设置为回调接口的类型，将两个接口链接到一个双工协定中。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="0ef8f-120">在客户端上调用方法</span><span class="sxs-lookup"><span data-stu-id="0ef8f-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="0ef8f-121">在主协定的服务实现中，声明回调接口的变量。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="0ef8f-122">将变量设置为通过 <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> 类的 <xref:System.ServiceModel.OperationContext> 方法返回的对象引用。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="0ef8f-123">调用由回调接口定义的方法。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef8f-124">示例</span><span class="sxs-lookup"><span data-stu-id="0ef8f-124">Example</span></span>  
 <span data-ttu-id="0ef8f-125">下面的代码示例演示双工通信。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="0ef8f-126">服务的协定包含用于向前移动和向后移动的服务操作。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="0ef8f-127">客户端的协定包含用于报告其位置的服务操作。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="0ef8f-128">应用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 属性允许自动生成使用 Web 服务描述语言 (WSDL) 的服务协定定义。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="0ef8f-129">使用配置的[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)可检索 WSDL 文档和（可选）客户端的代码和配置。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="0ef8f-130">公开双工服务的终结点必须是安全的。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="0ef8f-131">当服务接收双工消息时，它会查看传入消息中的 ReplyTo，以确定要发送答复的位置。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="0ef8f-132">如果通道不安全，则不受信任的客户端可能使用目标计算机的 ReplyTo 发送恶意消息，从而导致目标计算机发生拒绝服务。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="0ef8f-133">对于常规的规则请求-答复消息，这不是问题，因为将会忽略 ReplyTo 并在传入原始消息的通道上发送响应。</span><span class="sxs-lookup"><span data-stu-id="0ef8f-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef8f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ef8f-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="0ef8f-135">如何：使用双工协定访问服务</span><span class="sxs-lookup"><span data-stu-id="0ef8f-135">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="0ef8f-136">双工</span><span class="sxs-lookup"><span data-stu-id="0ef8f-136">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="0ef8f-137">设计和实现服务</span><span class="sxs-lookup"><span data-stu-id="0ef8f-137">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="0ef8f-138">如何：定义服务协定</span><span class="sxs-lookup"><span data-stu-id="0ef8f-138">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="0ef8f-139">会话</span><span class="sxs-lookup"><span data-stu-id="0ef8f-139">Session</span></span>](../samples/session.md)
