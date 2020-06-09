---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: f0e49fcfa13bb9932a88a4e79d617343c080bb3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598367"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="6a7e5-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="6a7e5-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="6a7e5-103">拒绝的病毒消息。</span><span class="sxs-lookup"><span data-stu-id="6a7e5-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6a7e5-104">描述</span><span class="sxs-lookup"><span data-stu-id="6a7e5-104">Description</span></span>  

 <span data-ttu-id="6a7e5-105">该跟踪指示遇到病毒消息并随后将其拒绝。</span><span class="sxs-lookup"><span data-stu-id="6a7e5-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="6a7e5-106">当 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 属性设置为 `Reject` 时，将会出现此情况。</span><span class="sxs-lookup"><span data-stu-id="6a7e5-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="6a7e5-107">拒绝的消息将传递回发送方的[死信队列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7e5-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="6a7e5-108">若要详细了解消息何时变为病毒以及如何配置服务以相应地处理这些消息，请参阅[病毒消息处理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7e5-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="6a7e5-109">有关 MSMQ 中的拒绝消息的含义的详细信息，请参阅[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。</span><span class="sxs-lookup"><span data-stu-id="6a7e5-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7e5-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a7e5-110">See also</span></span>

- [<span data-ttu-id="6a7e5-111">跟踪</span><span class="sxs-lookup"><span data-stu-id="6a7e5-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="6a7e5-112">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="6a7e5-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6a7e5-113">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="6a7e5-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="6a7e5-114">病毒消息处理</span><span class="sxs-lookup"><span data-stu-id="6a7e5-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="6a7e5-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="6a7e5-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
