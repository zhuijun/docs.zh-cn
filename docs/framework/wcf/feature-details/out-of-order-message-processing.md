---
title: 无序消息处理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598718"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="1d7e1-102">无序消息处理</span><span class="sxs-lookup"><span data-stu-id="1d7e1-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="1d7e1-103">工作流服务可能依赖于按特定顺序发送的消息。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="1d7e1-104">工作流服务包含一个或多个 <xref:System.ServiceModel.Activities.Receive> 活动，而每个 <xref:System.ServiceModel.Activities.Receive> 活动需要一条特定消息。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="1d7e1-105">如果无法保证单独传递传输，客户端发送的消息可能会延迟，从而可能无法按工作流服务所需的顺序传递消息。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="1d7e1-106">实现无需按特定顺序传送消息的工作流服务时，通常使用并行活动来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="1d7e1-107">对于更复杂的应用程序协议，工作流将很快变得极其复杂。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="1d7e1-108">使用 Windows Communication Foundation （WCF）中的无序消息处理功能，您可以创建这样的工作流，而无需所有复杂的嵌套并行活动。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="1d7e1-109">只支持对支持的通道 <xref:System.ServiceModel.Channels.ReceiveContext> （例如 WCF MSMQ 绑定）进行不序消息处理。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="1d7e1-110">启用无序消息处理</span><span class="sxs-lookup"><span data-stu-id="1d7e1-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="1d7e1-111">在 WorkflowService 上将 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 属性设置为`true` 即会启用无序消息处理。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="1d7e1-112">下面的示例演示如何在代码中设置 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="1d7e1-113">还可以将 `AllowBufferedReceive` 特性应用到 XAML 中的工作流服务，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="1d7e1-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d7e1-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d7e1-114">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="1d7e1-115">工作流服务</span><span class="sxs-lookup"><span data-stu-id="1d7e1-115">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="1d7e1-116">队列和可靠会话</span><span class="sxs-lookup"><span data-stu-id="1d7e1-116">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
