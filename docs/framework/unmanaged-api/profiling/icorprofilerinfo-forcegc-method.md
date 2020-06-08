---
title: ICorProfilerInfo::ForceGC 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 9bc6619f3ef383c7bf60a310a87f056cfc43cddf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498669"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="92224-102">ICorProfilerInfo::ForceGC 方法</span><span class="sxs-lookup"><span data-stu-id="92224-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="92224-103">强制在公共语言运行时（CLR）内发生垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="92224-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92224-104">语法</span><span class="sxs-lookup"><span data-stu-id="92224-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="92224-105">备注</span><span class="sxs-lookup"><span data-stu-id="92224-105">Remarks</span></span>  
 <span data-ttu-id="92224-106">`ForceGC`只能从从未运行托管代码并且在其堆栈上没有任何探查器回调的线程调用方法。</span><span class="sxs-lookup"><span data-stu-id="92224-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="92224-107">最方便的实现是在探查器中创建一个单独的线程，该线程在 `ForceGC` 收到信号时调用。</span><span class="sxs-lookup"><span data-stu-id="92224-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92224-108">要求</span><span class="sxs-lookup"><span data-stu-id="92224-108">Requirements</span></span>  
 <span data-ttu-id="92224-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92224-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92224-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92224-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92224-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92224-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92224-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92224-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92224-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92224-113">See also</span></span>

- [<span data-ttu-id="92224-114">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="92224-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
