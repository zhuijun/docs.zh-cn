---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596202"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="9ca5f-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="9ca5f-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="9ca5f-103">已向无响应的协调程序发送重播消息重试。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ca5f-104">描述</span><span class="sxs-lookup"><span data-stu-id="9ca5f-104">Description</span></span>  
 <span data-ttu-id="9ca5f-105">如果本地事务管理器因未在给定的时间内收到响应而需要向上级协调程序重新发送重播消息，则进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9ca5f-106">疑难解答</span><span class="sxs-lookup"><span data-stu-id="9ca5f-106">Troubleshooting</span></span>  
 <span data-ttu-id="9ca5f-107">调查导致响应未及时传送的潜在网络或产品问题。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="9ca5f-108">如果看到很多这样的消息，可能表明基础结构有问题或响应时间异常长。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="9ca5f-109">这两种问题都会明显降低系统中事务的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca5f-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ca5f-110">See also</span></span>

- [<span data-ttu-id="9ca5f-111">跟踪</span><span class="sxs-lookup"><span data-stu-id="9ca5f-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="9ca5f-112">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="9ca5f-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9ca5f-113">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="9ca5f-113">Administration and Diagnostics</span></span>](../index.md)
