---
title: COR_PRF_SNAPSHOT_INFO 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6168c5b27868a261871b292e17ca02b04ae89917
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500775"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO 枚举
指定在每次调用探查器的[StackSnapshotCallback](stacksnapshotcallback-function.md)函数时要通过堆栈快照传递回多少数据。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>成员  
  
|成员|说明|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|指示必须为所有 `StackSnapshotCallback` 参数（参数除外）传递值 `context` 。|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|指示必须为所有 `StackSnapshotCallback` 参数（包括参数）传递值 `context` 。|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|指示将使用更简单的替代堆栈遍历算法。|  
  
## <a name="remarks"></a>注解  
 枚举提供的值 `COR_PRF_SNAPSHOT_INFO` 将作为参数传递给[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [DoStackSnapshot 方法](icorprofilerinfo2-dostacksnapshot-method.md)
- [分析枚举](profiling-enumerations.md)
