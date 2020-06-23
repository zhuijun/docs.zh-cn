---
title: 如何：以异步方式调用 WCF 服务操作
description: 了解如何使用事件驱动的异步调用模型创建可异步访问服务操作的 WCF 客户端。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: aa31f64473111800f4cd01907a0446c94f368456
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247229"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="98805-103">如何：以异步方式调用 WCF 服务操作</span><span class="sxs-lookup"><span data-stu-id="98805-103">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="98805-104">本文介绍客户端如何以异步方式访问服务操作。</span><span class="sxs-lookup"><span data-stu-id="98805-104">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="98805-105">本文中的服务实现 `ICalculator` 接口。</span><span class="sxs-lookup"><span data-stu-id="98805-105">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="98805-106">通过使用事件驱动的异步调用模型，客户端可以对此接口异步调用操作。</span><span class="sxs-lookup"><span data-stu-id="98805-106">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="98805-107">（有关基于事件的异步调用模型的详细信息，请参阅[采用基于事件的异步模式进行多线程编程](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)）。</span><span class="sxs-lookup"><span data-stu-id="98805-107">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="98805-108">有关演示如何在服务中异步实现操作的示例，请参阅[如何：实现异步服务操作](../how-to-implement-an-asynchronous-service-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="98805-108">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="98805-109">有关同步和异步操作的详细信息，请参阅[同步和异步操作](../synchronous-and-asynchronous-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="98805-109">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98805-110">使用 <xref:System.ServiceModel.ChannelFactory%601> 时，不支持事件驱动的异步调用模型。</span><span class="sxs-lookup"><span data-stu-id="98805-110">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="98805-111">有关使用进行异步调用的信息 <xref:System.ServiceModel.ChannelFactory%601> ，请参阅[如何：使用通道工厂以异步方式调用操作](how-to-call-operations-asynchronously-using-a-channel-factory.md)。</span><span class="sxs-lookup"><span data-stu-id="98805-111">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="98805-112">过程</span><span class="sxs-lookup"><span data-stu-id="98805-112">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="98805-113">以异步方式调用 WCF 服务操作</span><span class="sxs-lookup"><span data-stu-id="98805-113">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="98805-114">同时运行带的[元数据实用工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)工具 `/async` 和 `/tcv:Version35` 命令选项，如下面的命令中所示。</span><span class="sxs-lookup"><span data-stu-id="98805-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="98805-115">这除了同步和标准的基于委托的异步操作，还会生成一个包含以下内容的 WCF 客户端类：</span><span class="sxs-lookup"><span data-stu-id="98805-115">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="98805-116">两个 <`operationName` > `Async` 操作，用于基于事件的异步调用方法。</span><span class="sxs-lookup"><span data-stu-id="98805-116">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="98805-117">例如：</span><span class="sxs-lookup"><span data-stu-id="98805-117">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="98805-118"><窗体的操作完成事件 `operationName` > `Completed` 与基于事件的异步调用方法一起使用。</span><span class="sxs-lookup"><span data-stu-id="98805-118">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="98805-119">例如：</span><span class="sxs-lookup"><span data-stu-id="98805-119">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="98805-120"><xref:System.EventArgs?displayProperty=nameWithType>每个操作的类型（窗体 <`operationName` > `CompletedEventArgs` ）用于基于事件的异步调用方法。</span><span class="sxs-lookup"><span data-stu-id="98805-120"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="98805-121">例如：</span><span class="sxs-lookup"><span data-stu-id="98805-121">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="98805-122">在调用应用程序中，创建一个要在异步操作完成时调用的回调方法，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="98805-122">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="98805-123">在调用操作之前，请使用类型 <的新泛型， <xref:System.EventHandler%601?displayProperty=nameWithType> `operationName` > `EventArgs` 将处理程序方法（在上一步中创建）添加到 <`operationName` > `Completed` 事件。</span><span class="sxs-lookup"><span data-stu-id="98805-123">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="98805-124">然后调用 <`operationName` > `Async` 方法。</span><span class="sxs-lookup"><span data-stu-id="98805-124">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="98805-125">例如：</span><span class="sxs-lookup"><span data-stu-id="98805-125">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="98805-126">示例</span><span class="sxs-lookup"><span data-stu-id="98805-126">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98805-127">基于事件的异步模型设计准则规定，如果返回了多个值，则一个值会作为 `Result` 属性返回，其他值会作为 <xref:System.EventArgs> 对象上的属性返回。</span><span class="sxs-lookup"><span data-stu-id="98805-127">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="98805-128">因此产生的结果之一是，如果客户端使用基于事件的异步命令选项导入元数据，且该操作返回多个值，则默认的 <xref:System.EventArgs> 对象返回一个值作为 `Result` 属性，返回的其余值是 <xref:System.EventArgs> 对象的属性。如果要将消息对象作为 `Result` 属性来接收并要使返回的值作为该对象上的属性，请使用 `/messageContract` 命令选项。</span><span class="sxs-lookup"><span data-stu-id="98805-128">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="98805-129">这会生成一个签名，该签名会将响应消息作为 `Result` 对象上的 <xref:System.EventArgs> 属性返回。</span><span class="sxs-lookup"><span data-stu-id="98805-129">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="98805-130">然后，所有内部返回值就都是响应消息对象的属性了。</span><span class="sxs-lookup"><span data-stu-id="98805-130">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="98805-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="98805-131">See also</span></span>

- [<span data-ttu-id="98805-132">如何：实现异步服务操作</span><span class="sxs-lookup"><span data-stu-id="98805-132">How to: Implement an Asynchronous Service Operation</span></span>](../how-to-implement-an-asynchronous-service-operation.md)
