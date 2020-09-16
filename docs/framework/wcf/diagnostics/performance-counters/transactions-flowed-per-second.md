---
title: Transactions Flowed Per Second（每秒流动的事务数）
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: d55856a5d820df2c668863a2a3e853995a113143
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552201"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="01c6b-102">Transactions Flowed Per Second（每秒流动的事务数）</span><span class="sxs-lookup"><span data-stu-id="01c6b-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="01c6b-103">计数器名称：Transactions Flowed Per Second（每秒流动的事务数）</span><span class="sxs-lookup"><span data-stu-id="01c6b-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="01c6b-104">说明</span><span class="sxs-lookup"><span data-stu-id="01c6b-104">Description</span></span>  
 <span data-ttu-id="01c6b-105">一秒内向此操作流动的事务数量。</span><span class="sxs-lookup"><span data-stu-id="01c6b-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="01c6b-106">每当发送到此操作的消息中存在事务 ID 时，此计数器就会增加。</span><span class="sxs-lookup"><span data-stu-id="01c6b-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="01c6b-107">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="01c6b-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="01c6b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="01c6b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
