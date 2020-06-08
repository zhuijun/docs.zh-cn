---
title: ICorProfilerCallback::ExceptionSearchCatcherFound 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 70c03d34bdf9bd315994b2bfa09631efac2565ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500216"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="1474e-102">ICorProfilerCallback::ExceptionSearchCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="1474e-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="1474e-103">通知探查器，异常处理的搜索阶段已找到引发的异常的处理程序。</span><span class="sxs-lookup"><span data-stu-id="1474e-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1474e-104">语法</span><span class="sxs-lookup"><span data-stu-id="1474e-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1474e-105">参数</span><span class="sxs-lookup"><span data-stu-id="1474e-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="1474e-106">\[in] 包含异常处理程序的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="1474e-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="1474e-107">要求</span><span class="sxs-lookup"><span data-stu-id="1474e-107">Requirements</span></span>  
 <span data-ttu-id="1474e-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1474e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1474e-109">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1474e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1474e-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1474e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1474e-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1474e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1474e-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1474e-112">See also</span></span>

- [<span data-ttu-id="1474e-113">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="1474e-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
