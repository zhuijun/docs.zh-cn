---
title: Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: bf7d13f04f0bad315c879f1b4299a78e9515cc56
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550646"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="cd60c-102">Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）</span><span class="sxs-lookup"><span data-stu-id="cd60c-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="cd60c-103">计数器名称：Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）。</span><span class="sxs-lookup"><span data-stu-id="cd60c-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cd60c-104">说明</span><span class="sxs-lookup"><span data-stu-id="cd60c-104">Description</span></span>  
 <span data-ttu-id="cd60c-105">在此服务中一秒内已中止的事务性操作的数量。</span><span class="sxs-lookup"><span data-stu-id="cd60c-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="cd60c-106">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="cd60c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cd60c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cd60c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
