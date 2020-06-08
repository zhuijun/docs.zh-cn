---
title: ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498994"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="abbf3-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="abbf3-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="abbf3-103">[.NET Framework 4.7 及更高版本中支持]</span><span class="sxs-lookup"><span data-stu-id="abbf3-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="abbf3-104">当动态方法的 JIT 编译开始时，通知探查器。</span><span class="sxs-lookup"><span data-stu-id="abbf3-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abbf3-105">语法</span><span class="sxs-lookup"><span data-stu-id="abbf3-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abbf3-106">参数</span><span class="sxs-lookup"><span data-stu-id="abbf3-106">Parameters</span></span>  
<span data-ttu-id="abbf3-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="abbf3-107">[in] `functionId`</span></span>  
<span data-ttu-id="abbf3-108">开始 JIT 编译的内存中函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="abbf3-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="abbf3-109">[in] `fIsSafeToBlock` 
 `true`指示阻止可能会导致运行时等待调用线程从该回调返回;`false`指示阻止操作不会影响运行时的操作。</span><span class="sxs-lookup"><span data-stu-id="abbf3-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="abbf3-110">[in] `pILHeader`指向该方法的 IL 标头的第一个字节的指针。</span><span class="sxs-lookup"><span data-stu-id="abbf3-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="abbf3-111">[in] `cbILHeader`IL 标头中的字节数。</span><span class="sxs-lookup"><span data-stu-id="abbf3-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="abbf3-112">注解</span><span class="sxs-lookup"><span data-stu-id="abbf3-112">Remarks</span></span>  

<span data-ttu-id="abbf3-113">只要 JIT 编译动态方法，就会触发此回调。</span><span class="sxs-lookup"><span data-stu-id="abbf3-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="abbf3-114">这包括各种 IL 存根和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="abbf3-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="abbf3-115">其目标是为探查器编写者提供足够的信息，以便向用户标识编译的方法。</span><span class="sxs-lookup"><span data-stu-id="abbf3-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="abbf3-116">`functionId`由于动态方法没有元数据，因此不能使用值来解析为其元数据标记。</span><span class="sxs-lookup"><span data-stu-id="abbf3-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="abbf3-117">`pILHeader`指针仅在回调期间有效。</span><span class="sxs-lookup"><span data-stu-id="abbf3-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="abbf3-118">要求</span><span class="sxs-lookup"><span data-stu-id="abbf3-118">Requirements</span></span>  
 <span data-ttu-id="abbf3-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abbf3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abbf3-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abbf3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abbf3-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abbf3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abbf3-122">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="abbf3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbf3-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abbf3-123">See also</span></span>

- [<span data-ttu-id="abbf3-124">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="abbf3-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="abbf3-125">ICorProfilerCallback8 接口</span><span class="sxs-lookup"><span data-stu-id="abbf3-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
