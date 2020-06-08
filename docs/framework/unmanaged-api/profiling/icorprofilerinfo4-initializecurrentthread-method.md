---
title: ICorProfilerInfo4::InitializeCurrentThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 1f3ff3e9b68aa30f424f4b2fe6c7cacd2cddd544
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495926"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread 方法
在同一线程上的后续探查器 API 调用之前初始化当前线程，以便避免死锁。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>备注  
 建议在 `InitializeCurrentThread` 存在挂起的线程时，调用将调用探查器 API 的任何线程。 此方法通常由创建自己的线程的探查器使用，用来调用[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法，在目标线程挂起时执行堆栈遍历。 通过在 `InitializeCurrentThread` 探查器首次创建采样线程时调用一次，探查器可以确保在第一次调用期间，CLR 在第一次调用期间要执行的延迟的每个线程初始化 `DoStackSnapshot` 现在可以在没有其他线程挂起时安全地发生。  
  
> [!NOTE]
> `InitializeCurrentThread`预先执行初始化来完成接受锁定的任务，可能会死锁。 `InitializeCurrentThread`仅当没有挂起的线程时才调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorProfilerInfo4 接口](icorprofilerinfo4-interface.md)
- [分析接口](profiling-interfaces.md)
- [分析](index.md)
