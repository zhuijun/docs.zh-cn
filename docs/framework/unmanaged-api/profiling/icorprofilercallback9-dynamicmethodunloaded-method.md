---
title: ICorProfilerCallback9：:D ynamicMethodUnloaded 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498968"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="500da-102">ICorProfilerCallback9：:D ynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="500da-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="500da-103">[.NET Framework 4.7.2 和更高版本中支持]</span><span class="sxs-lookup"><span data-stu-id="500da-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="500da-104">每当对动态方法进行垃圾回收并随后卸载时，通知探查器。</span><span class="sxs-lookup"><span data-stu-id="500da-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="500da-105">语法</span><span class="sxs-lookup"><span data-stu-id="500da-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="500da-106">参数</span><span class="sxs-lookup"><span data-stu-id="500da-106">Parameters</span></span>  
<span data-ttu-id="500da-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="500da-107">[in] `functionId`</span></span>  
<span data-ttu-id="500da-108">已被垃圾回收和卸载的内存中函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="500da-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="500da-109">要求</span><span class="sxs-lookup"><span data-stu-id="500da-109">Requirements</span></span>  
 <span data-ttu-id="500da-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="500da-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="500da-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="500da-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="500da-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="500da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="500da-113">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="500da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500da-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="500da-114">See also</span></span>

- [<span data-ttu-id="500da-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="500da-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="500da-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="500da-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="500da-117">ICorProfilerCallback9 接口</span><span class="sxs-lookup"><span data-stu-id="500da-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="500da-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="500da-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
