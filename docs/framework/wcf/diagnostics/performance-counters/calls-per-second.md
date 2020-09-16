---
title: Calls Per Second（每秒调用次数）
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: b0dfe5350583db318b0f335867342e5ef2371bff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541677"
---
# <a name="calls-per-second"></a>Calls Per Second（每秒调用次数）
计数器名称：Calls Per Second（每秒调用次数）  
  
## <a name="description"></a>说明  
 一秒内对此操作调用的次数。  
  
 此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
