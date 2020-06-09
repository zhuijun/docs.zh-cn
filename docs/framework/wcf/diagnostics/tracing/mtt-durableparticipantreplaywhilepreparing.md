---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589127"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="20bf9-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="20bf9-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="20bf9-103">WS-AT 协议服务从不响应 Prepare 的持久参与者接收到重播消息。</span><span class="sxs-lookup"><span data-stu-id="20bf9-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="20bf9-104">因此，中止了事务。</span><span class="sxs-lookup"><span data-stu-id="20bf9-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="20bf9-105">描述</span><span class="sxs-lookup"><span data-stu-id="20bf9-105">Description</span></span>  
 <span data-ttu-id="20bf9-106">如果持久参与者仍然在准备时接收到重播消息，则进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="20bf9-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="20bf9-107">这是此状态的非法消息，将中止事务。</span><span class="sxs-lookup"><span data-stu-id="20bf9-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="20bf9-108">疑难解答</span><span class="sxs-lookup"><span data-stu-id="20bf9-108">Troubleshooting</span></span>

<span data-ttu-id="20bf9-109">如果收到此错误，则可能表示持久参与者（包括从属 TransactionManagers）已从失败中恢复;但是，它不能确定事务结果并请求其状态。</span><span class="sxs-lookup"><span data-stu-id="20bf9-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bf9-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20bf9-110">See also</span></span>

- [<span data-ttu-id="20bf9-111">跟踪</span><span class="sxs-lookup"><span data-stu-id="20bf9-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="20bf9-112">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="20bf9-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="20bf9-113">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="20bf9-113">Administration and Diagnostics</span></span>](../index.md)
