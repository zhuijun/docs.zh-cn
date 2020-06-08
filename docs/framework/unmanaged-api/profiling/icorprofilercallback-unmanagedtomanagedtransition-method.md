---
title: ICorProfilerCallback::UnmanagedToManagedTransition 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 8734fa9c9418b818cbe14ebe87ce2af6fa59c078
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499839"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="cebed-102">ICorProfilerCallback::UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="cebed-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="cebed-103">通知探查器已发生从非托管代码到托管代码的转换。</span><span class="sxs-lookup"><span data-stu-id="cebed-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cebed-104">语法</span><span class="sxs-lookup"><span data-stu-id="cebed-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cebed-105">参数</span><span class="sxs-lookup"><span data-stu-id="cebed-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cebed-106">中正在调用的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="cebed-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="cebed-107">中一个[COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md)枚举的值，该值指示是否由于从非托管代码调用托管代码而发生了转换，或是否是由托管函数调用的非托管函数返回。</span><span class="sxs-lookup"><span data-stu-id="cebed-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cebed-108">注解</span><span class="sxs-lookup"><span data-stu-id="cebed-108">Remarks</span></span>  
 <span data-ttu-id="cebed-109">如果的值 `reason` 为 COR_PRF_TRANSITION_RETURN 且不为 `functionId` null，则函数 ID 为非托管函数的，并且永远不会使用实时（JIT）编译器编译。</span><span class="sxs-lookup"><span data-stu-id="cebed-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="cebed-110">非托管函数有一些与之关联的基本信息，如名称和某些元数据。</span><span class="sxs-lookup"><span data-stu-id="cebed-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="cebed-111">如果 COR_PRF_TRANSITION_CALL 的值 `reason` ，则可能已调用的函数（即托管函数）尚未进行 JIT 编译。</span><span class="sxs-lookup"><span data-stu-id="cebed-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cebed-112">要求</span><span class="sxs-lookup"><span data-stu-id="cebed-112">Requirements</span></span>  
 <span data-ttu-id="cebed-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cebed-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cebed-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cebed-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cebed-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cebed-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cebed-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cebed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebed-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cebed-117">See also</span></span>

- [<span data-ttu-id="cebed-118">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="cebed-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cebed-119">ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="cebed-119">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="cebed-120">在 c + + 中使用显式 PInvoke （DllImport 特性）</span><span class="sxs-lookup"><span data-stu-id="cebed-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="cebed-121">使用 c + + 互操作（隐式 PInvoke）</span><span class="sxs-lookup"><span data-stu-id="cebed-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
