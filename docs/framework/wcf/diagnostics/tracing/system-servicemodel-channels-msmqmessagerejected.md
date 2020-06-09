---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578046"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="56577-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="56577-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="56577-103">MSMQ 已拒绝该消息。</span><span class="sxs-lookup"><span data-stu-id="56577-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="56577-104">描述</span><span class="sxs-lookup"><span data-stu-id="56577-104">Description</span></span>  
 <span data-ttu-id="56577-105">此跟踪指示已拒绝 MSMQ 消息。</span><span class="sxs-lookup"><span data-stu-id="56577-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="56577-106">Windows Communication Foundation （WCF）（与 NetMsmqBinding 或 MsmqIntegrationBinding 一起使用时）无法处理 MSMQ 消息时，该消息可能会被拒绝。</span><span class="sxs-lookup"><span data-stu-id="56577-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="56577-107">这些消息称为病毒消息。</span><span class="sxs-lookup"><span data-stu-id="56577-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="56577-108">当 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 属性设置为 `Reject` 时，将拒绝病毒消息。</span><span class="sxs-lookup"><span data-stu-id="56577-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="56577-109">拒绝的消息将传递回发送方的[死信队列](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)。</span><span class="sxs-lookup"><span data-stu-id="56577-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="56577-110">若要详细了解消息何时变为病毒以及如何配置服务以相应地处理这些消息，请参阅[病毒消息处理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="56577-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="56577-111">有关 MSMQ 中的拒绝消息的含义的详细信息，请参阅[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。</span><span class="sxs-lookup"><span data-stu-id="56577-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56577-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56577-112">See also</span></span>

- [<span data-ttu-id="56577-113">跟踪</span><span class="sxs-lookup"><span data-stu-id="56577-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="56577-114">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="56577-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="56577-115">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="56577-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="56577-116">病毒消息处理</span><span class="sxs-lookup"><span data-stu-id="56577-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="56577-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="56577-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
