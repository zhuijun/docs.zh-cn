---
title: 终结点：Transactions Flowed Per Second（每秒流动的事务数）
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 9391651eaaca130ef47ddee9daa95b1f8c116892
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553787"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="6bda5-102">终结点：Transactions Flowed Per Second（每秒流动的事务数）</span><span class="sxs-lookup"><span data-stu-id="6bda5-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="6bda5-103">计数器名称：Transactions Flowed Per Second（每秒流动的事务数）。</span><span class="sxs-lookup"><span data-stu-id="6bda5-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6bda5-104">说明</span><span class="sxs-lookup"><span data-stu-id="6bda5-104">Description</span></span>  
 <span data-ttu-id="6bda5-105">一秒内流向此终结点上的操作的事务数。</span><span class="sxs-lookup"><span data-stu-id="6bda5-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="6bda5-106">只要发送到终结点的消息中出现事务 ID，此计数器即会递增。</span><span class="sxs-lookup"><span data-stu-id="6bda5-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="6bda5-107">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="6bda5-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6bda5-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="6bda5-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
