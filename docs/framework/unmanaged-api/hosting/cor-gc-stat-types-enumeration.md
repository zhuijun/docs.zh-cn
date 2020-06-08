---
title: COR_GC_STAT_TYPES 枚举
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501685"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES 枚举
指定要为垃圾回收记录的统计信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>备注  
 此枚举指定[COR_GC_STATS](cor-gc-stats-structure.md)结构中的哪些统计信息由[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法设置。  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`COR_GC_COUNTS`|记录为每个代执行的垃圾回收数。|  
|`COR_GC_MEMORYUSAGE`|记录内存使用情况和垃圾回收大小统计信息。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** GCHost，GCHost  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [COR_GC_STATS 结构](cor-gc-stats-structure.md)
- [承载枚举](hosting-enumerations.md)
