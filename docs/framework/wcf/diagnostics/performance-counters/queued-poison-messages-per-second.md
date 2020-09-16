---
title: 每秒排队病毒消息数
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 39118b515949e6ad4f6ff651037cd757a6dd9bbf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552643"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="47460-102">每秒排队病毒消息数</span><span class="sxs-lookup"><span data-stu-id="47460-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="47460-103">计数器名称：Queued Poison Messages Per Second（每秒排队病毒消息数）。</span><span class="sxs-lookup"><span data-stu-id="47460-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47460-104">说明</span><span class="sxs-lookup"><span data-stu-id="47460-104">Description</span></span>  
 <span data-ttu-id="47460-105">此服务中每秒由排队传输标记为病毒消息的消息数。</span><span class="sxs-lookup"><span data-stu-id="47460-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="47460-106">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="47460-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="47460-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="47460-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
