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
# <a name="transacted-operations-aborted-per-second"></a>Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）
计数器名称：Transacted Operations Aborted Per Second（每秒中止的事务处理操作次数）。  
  
## <a name="description"></a>说明  
 在此服务中一秒内已中止的事务性操作的数量。  
  
 此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
