---
title: 在会话中对排队消息进行分组
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 66f51267f20f8cdad8feeedf37435ccfa733146e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597353"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="e7b73-102">在会话中对排队消息进行分组</span><span class="sxs-lookup"><span data-stu-id="e7b73-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="e7b73-103">Windows Communication Foundation （WCF）提供了一个会话，该会话允许将一组相关消息组合在一起，以便由单个接收应用程序进行处理。</span><span class="sxs-lookup"><span data-stu-id="e7b73-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="e7b73-104">属于一个会话的消息必须属于同一事务。</span><span class="sxs-lookup"><span data-stu-id="e7b73-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="e7b73-105">因为所有消息都属于同一事务，所以如果有一个消息未能得到处理，整个会话都将回滚。</span><span class="sxs-lookup"><span data-stu-id="e7b73-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="e7b73-106">会话对于死信队列和病毒队列具有类似的行为。</span><span class="sxs-lookup"><span data-stu-id="e7b73-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="e7b73-107">在为会话配置的排队绑定上设置的生存时间 (TTL) 属性被应用于整个会话。</span><span class="sxs-lookup"><span data-stu-id="e7b73-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="e7b73-108">如果在 TTL 过期前仅发送了会话中的一部分消息，则会将整个会话都放到死信队列中。</span><span class="sxs-lookup"><span data-stu-id="e7b73-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="e7b73-109">与此类似，如果会话中有消息未能发送到应用程序队列中的应用程序，则会将整个会话都放到病毒队列（如果可用）中。</span><span class="sxs-lookup"><span data-stu-id="e7b73-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="e7b73-110">消息分组示例</span><span class="sxs-lookup"><span data-stu-id="e7b73-110">Message Grouping Example</span></span>  
 <span data-ttu-id="e7b73-111">例如，在将订单处理应用程序作为 WCF 服务实现时，对消息进行分组很有用。</span><span class="sxs-lookup"><span data-stu-id="e7b73-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="e7b73-112">例如，某个客户端向此应用程序提交一个包含许多项的订单。</span><span class="sxs-lookup"><span data-stu-id="e7b73-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="e7b73-113">对于每个项，该客户端都要调用一次服务，每次调用都会产生一个要发送的消息。</span><span class="sxs-lookup"><span data-stu-id="e7b73-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="e7b73-114">有可能发生服务器 A 接收第一个项，而服务器 B 接收第二个项的情况。</span><span class="sxs-lookup"><span data-stu-id="e7b73-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="e7b73-115">每次添加一个项时，处理该项的服务器都必须找到相应的订单并将该项添加到订单中 — 这样做效率非常低。</span><span class="sxs-lookup"><span data-stu-id="e7b73-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="e7b73-116">如果只使用单个服务器来处理所有请求，仍然会非常低效，因为该服务器必须跟踪当前正在处理的所有订单并确定新项属于哪个订单。</span><span class="sxs-lookup"><span data-stu-id="e7b73-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="e7b73-117">将单个订单的所有请求分为一组可大大简化这样一个应用程序的实现。</span><span class="sxs-lookup"><span data-stu-id="e7b73-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="e7b73-118">客户端应用程序在一个会话中发送单个订单的所有项，因此当服务处理该订单时，它可以一次性处理整个会话。</span><span class="sxs-lookup"><span data-stu-id="e7b73-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="e7b73-119">过程</span><span class="sxs-lookup"><span data-stu-id="e7b73-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="e7b73-120">设置服务协定以使用会话</span><span class="sxs-lookup"><span data-stu-id="e7b73-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="e7b73-121">定义一个需要会话的服务协定。</span><span class="sxs-lookup"><span data-stu-id="e7b73-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="e7b73-122"><xref:System.ServiceModel.ServiceContractAttribute>通过指定以下内容，通过属性执行此操作：</span><span class="sxs-lookup"><span data-stu-id="e7b73-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="e7b73-123">将该协定中的操作标记为单向操作，因为这些方法不返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="e7b73-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="e7b73-124"><xref:System.ServiceModel.OperationContractAttribute>通过指定以下内容来完成此操作：</span><span class="sxs-lookup"><span data-stu-id="e7b73-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="e7b73-125">实现该服务协定并指定一个类型为 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> 的 <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e7b73-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e7b73-126">这样，对于每个会话，仅实例化服务一次。</span><span class="sxs-lookup"><span data-stu-id="e7b73-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="e7b73-127">每个服务操作都需要一个事务。</span><span class="sxs-lookup"><span data-stu-id="e7b73-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="e7b73-128">可使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性予以指定。</span><span class="sxs-lookup"><span data-stu-id="e7b73-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="e7b73-129">负责完成该事务的操作还应将 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e7b73-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. <span data-ttu-id="e7b73-130">配置一个终结点，该终结点使用系统提供的 `NetMsmqBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="e7b73-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="e7b73-131">使用 <xref:System.Messaging> 创建一个事务性队列。</span><span class="sxs-lookup"><span data-stu-id="e7b73-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="e7b73-132">还可以使用消息队列 (MSMQ) 或 MMC 创建该队列。</span><span class="sxs-lookup"><span data-stu-id="e7b73-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="e7b73-133">如果你这样做，请创建一个事务性队列。</span><span class="sxs-lookup"><span data-stu-id="e7b73-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="e7b73-134">使用 <xref:System.ServiceModel.ServiceHost> 为该服务创建一个服务主机。</span><span class="sxs-lookup"><span data-stu-id="e7b73-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="e7b73-135">打开服务主机使服务处于可用状态。</span><span class="sxs-lookup"><span data-stu-id="e7b73-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="e7b73-136">关闭服务主机。</span><span class="sxs-lookup"><span data-stu-id="e7b73-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="e7b73-137">设置客户端</span><span class="sxs-lookup"><span data-stu-id="e7b73-137">To set up a client</span></span>  
  
1. <span data-ttu-id="e7b73-138">创建一个要写入事务性队列的事务范围。</span><span class="sxs-lookup"><span data-stu-id="e7b73-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="e7b73-139">使用[Svcutil.exe 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)工具创建 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="e7b73-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="e7b73-140">下订单。</span><span class="sxs-lookup"><span data-stu-id="e7b73-140">Place the order.</span></span>  
  
4. <span data-ttu-id="e7b73-141">关闭 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="e7b73-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7b73-142">示例</span><span class="sxs-lookup"><span data-stu-id="e7b73-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e7b73-143">描述</span><span class="sxs-lookup"><span data-stu-id="e7b73-143">Description</span></span>  
 <span data-ttu-id="e7b73-144">下面的示例提供 `IProcessOrder` 服务的代码和一个使用此服务的客户端的代码。</span><span class="sxs-lookup"><span data-stu-id="e7b73-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="e7b73-145">其中显示了 WCF 如何使用排队会话来提供分组行为。</span><span class="sxs-lookup"><span data-stu-id="e7b73-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="e7b73-146">服务代码</span><span class="sxs-lookup"><span data-stu-id="e7b73-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="e7b73-147">客户端代码</span><span class="sxs-lookup"><span data-stu-id="e7b73-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="e7b73-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7b73-148">See also</span></span>

- [<span data-ttu-id="e7b73-149">会话和队列</span><span class="sxs-lookup"><span data-stu-id="e7b73-149">Sessions and Queues</span></span>](../samples/sessions-and-queues.md)
- [<span data-ttu-id="e7b73-150">队列概述</span><span class="sxs-lookup"><span data-stu-id="e7b73-150">Queues Overview</span></span>](queues-overview.md)
