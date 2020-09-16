---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: c5401bae1d8e7f61939d8de321353f59f412f966
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535328"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="bd8d6-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="bd8d6-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="bd8d6-103">拒绝的病毒消息。</span><span class="sxs-lookup"><span data-stu-id="bd8d6-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bd8d6-104">说明</span><span class="sxs-lookup"><span data-stu-id="bd8d6-104">Description</span></span>  

 <span data-ttu-id="bd8d6-105">该跟踪指示遇到病毒消息并随后将其拒绝。</span><span class="sxs-lookup"><span data-stu-id="bd8d6-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="bd8d6-106">当 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 属性设置为 `Reject` 时，将会出现此情况。</span><span class="sxs-lookup"><span data-stu-id="bd8d6-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="bd8d6-107">拒绝的消息将传递回发送方的 [死信队列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="bd8d6-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="bd8d6-108">若要详细了解消息何时变为病毒以及如何配置服务以相应地处理这些消息，请参阅 [病毒消息处理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="bd8d6-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="bd8d6-109">有关 MSMQ 中的拒绝消息的含义的详细信息，请参阅 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="bd8d6-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8d6-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="bd8d6-110">See also</span></span>

- [<span data-ttu-id="bd8d6-111">跟踪</span><span class="sxs-lookup"><span data-stu-id="bd8d6-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="bd8d6-112">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="bd8d6-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bd8d6-113">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="bd8d6-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="bd8d6-114">病毒消息处理</span><span class="sxs-lookup"><span data-stu-id="bd8d6-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="bd8d6-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="bd8d6-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
