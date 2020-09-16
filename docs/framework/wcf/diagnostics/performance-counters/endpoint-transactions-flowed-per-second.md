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
# <a name="endpoint-transactions-flowed-per-second"></a>终结点：Transactions Flowed Per Second（每秒流动的事务数）
计数器名称：Transactions Flowed Per Second（每秒流动的事务数）。  
  
## <a name="description"></a>说明  
 一秒内流向此终结点上的操作的事务数。 只要发送到终结点的消息中出现事务 ID，此计数器即会递增。  
  
 此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
