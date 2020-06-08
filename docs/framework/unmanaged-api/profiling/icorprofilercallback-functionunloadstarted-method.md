---
title: ICorProfilerCallback::FunctionUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 320aaf074452fd02cd8ee8e80194a4c35b831eb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503375"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="c8894-102">ICorProfilerCallback::FunctionUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="c8894-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="c8894-103">通知探查器运行时已开始卸载某个函数。</span><span class="sxs-lookup"><span data-stu-id="c8894-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8894-104">语法</span><span class="sxs-lookup"><span data-stu-id="c8894-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="c8894-105">参数</span><span class="sxs-lookup"><span data-stu-id="c8894-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c8894-106">\[in] 正在卸载的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="c8894-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8894-107">注解</span><span class="sxs-lookup"><span data-stu-id="c8894-107">Remarks</span></span>  
 <span data-ttu-id="c8894-108">`functionId`此方法返回到调用方后，该参数的值不再有效。</span><span class="sxs-lookup"><span data-stu-id="c8894-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8894-109">要求</span><span class="sxs-lookup"><span data-stu-id="c8894-109">Requirements</span></span>  
 <span data-ttu-id="c8894-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8894-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8894-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8894-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8894-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8894-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8894-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8894-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8894-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8894-114">See also</span></span>

- [<span data-ttu-id="c8894-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="c8894-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
