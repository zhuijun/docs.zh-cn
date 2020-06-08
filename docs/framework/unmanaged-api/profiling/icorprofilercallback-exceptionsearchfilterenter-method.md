---
title: ICorProfilerCallback::ExceptionSearchFilterEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: 304b8da670786851a70e38e6623d44b1bde71a04
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500229"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="5e433-102">ICorProfilerCallback::ExceptionSearchFilterEnter 方法</span><span class="sxs-lookup"><span data-stu-id="5e433-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="5e433-103">通知探查器异常处理的搜索阶段已开始执行用户定义的异常筛选器。</span><span class="sxs-lookup"><span data-stu-id="5e433-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e433-104">语法</span><span class="sxs-lookup"><span data-stu-id="5e433-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e433-105">参数</span><span class="sxs-lookup"><span data-stu-id="5e433-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="5e433-106">\[in] 包含筛选器的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="5e433-106">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e433-107">要求</span><span class="sxs-lookup"><span data-stu-id="5e433-107">Requirements</span></span>  
 <span data-ttu-id="5e433-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e433-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e433-109">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e433-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e433-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e433-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e433-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e433-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e433-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e433-112">See also</span></span>

- [<span data-ttu-id="5e433-113">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="5e433-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5e433-114">ExceptionSearchFilterLeave 方法</span><span class="sxs-lookup"><span data-stu-id="5e433-114">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
