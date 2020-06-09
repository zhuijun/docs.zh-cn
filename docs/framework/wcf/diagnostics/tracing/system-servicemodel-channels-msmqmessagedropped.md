---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601891"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="14cac-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="14cac-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="14cac-103">MSMQ 已删除该消息。</span><span class="sxs-lookup"><span data-stu-id="14cac-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="14cac-104">描述</span><span class="sxs-lookup"><span data-stu-id="14cac-104">Description</span></span>  
 <span data-ttu-id="14cac-105">该跟踪指示已丢弃 MSMQ 消息。</span><span class="sxs-lookup"><span data-stu-id="14cac-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="14cac-106">当 Windows Communication Foundation （WCF）（与 NetMsmqBinding 或 MsmqIntegrationBinding 一起使用时）无法处理 MSMQ 消息时，可以将其删除。</span><span class="sxs-lookup"><span data-stu-id="14cac-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="14cac-107">这些消息称为病毒消息。</span><span class="sxs-lookup"><span data-stu-id="14cac-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="14cac-108">当 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 属性设置为 `Drop` 时，将丢弃病毒消息。</span><span class="sxs-lookup"><span data-stu-id="14cac-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="14cac-109">丢弃的消息会从队列中移除而不再可恢复。</span><span class="sxs-lookup"><span data-stu-id="14cac-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="14cac-110">若要详细了解消息何时变为病毒以及如何配置服务以相应地处理这些消息，请参阅[病毒消息处理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="14cac-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14cac-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14cac-111">See also</span></span>

- [<span data-ttu-id="14cac-112">跟踪</span><span class="sxs-lookup"><span data-stu-id="14cac-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="14cac-113">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="14cac-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="14cac-114">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="14cac-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="14cac-115">病毒消息处理</span><span class="sxs-lookup"><span data-stu-id="14cac-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
