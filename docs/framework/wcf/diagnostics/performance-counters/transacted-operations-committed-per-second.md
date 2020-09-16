---
title: Transacted Operations Committed Per Second（每秒提交的事务处理操作次数）
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 047640e9b5cc22f2d443832fb7bd5afd47aef5be
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550633"
---
# <a name="transacted-operations-committed-per-second"></a>Transacted Operations Committed Per Second（每秒提交的事务处理操作次数）
计数器名称：Transacted Operations Committed Per Second（每秒提交的事务处理操作次数）。  
  
## <a name="description"></a>说明  
 此服务中每秒提交的事务处理操作的数量。  
  
 此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
