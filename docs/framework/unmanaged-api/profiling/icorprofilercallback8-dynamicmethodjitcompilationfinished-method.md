---
title: ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499072"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="aa7d5-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="aa7d5-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="aa7d5-103">[.NET Framework 4.7 及更高版本中支持]</span><span class="sxs-lookup"><span data-stu-id="aa7d5-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="aa7d5-104">当动态方法的 JIT 编译完成时，通知探查器。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa7d5-105">语法</span><span class="sxs-lookup"><span data-stu-id="aa7d5-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa7d5-106">参数</span><span class="sxs-lookup"><span data-stu-id="aa7d5-106">Parameters</span></span>  
<span data-ttu-id="aa7d5-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="aa7d5-107">[in] `functionId`</span></span>  
<span data-ttu-id="aa7d5-108">开始 JIT 编译的内存中函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="aa7d5-109">[in] `hrStatus`一个值，该值指示 JIT 编译是否成功。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="aa7d5-110">[in] `fIsSafeToBlock` 
 `true`指示阻止可能会导致运行时等待调用线程从该回调返回;`false`指示阻止操作不会影响运行时的操作。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="aa7d5-111">注解</span><span class="sxs-lookup"><span data-stu-id="aa7d5-111">Remarks</span></span>  

<span data-ttu-id="aa7d5-112">只要动态方法的 JIT 编译完成，就会触发此回调。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="aa7d5-113">这包括各种 IL 存根和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="aa7d5-114">其目标是为探查器编写者提供足够的信息，以便向用户标识编译的方法。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="aa7d5-115">`functionId`由于动态方法没有元数据，因此不能使用值来解析为其元数据标记。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa7d5-116">要求</span><span class="sxs-lookup"><span data-stu-id="aa7d5-116">Requirements</span></span>  
 <span data-ttu-id="aa7d5-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa7d5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa7d5-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa7d5-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa7d5-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa7d5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa7d5-120">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aa7d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7d5-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa7d5-121">See also</span></span>

- [<span data-ttu-id="aa7d5-122">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="aa7d5-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="aa7d5-123">ICorProfilerCallback8 接口</span><span class="sxs-lookup"><span data-stu-id="aa7d5-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
