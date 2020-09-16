---
title: 每秒丢弃的排队消息数
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 22b6091693b6a4c8eac9816e8ac15660f4636ec9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552747"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="d923b-102">每秒丢弃的排队消息数</span><span class="sxs-lookup"><span data-stu-id="d923b-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="d923b-103">计数器名称：Queued Messages Dropped Per Second（每秒丢弃的排队消息数）。</span><span class="sxs-lookup"><span data-stu-id="d923b-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d923b-104">说明</span><span class="sxs-lookup"><span data-stu-id="d923b-104">Description</span></span>  
 <span data-ttu-id="d923b-105">此服务处的排队传输机制每秒丢弃的消息数。</span><span class="sxs-lookup"><span data-stu-id="d923b-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="d923b-106">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="d923b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d923b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d923b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
