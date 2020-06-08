---
title: ICorProfilerCallback::ManagedToUnmanagedTransition 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 9b53030fe860e02b0afd0dce3055ac3cf29e3491
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499995"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="e5d10-102">ICorProfilerCallback::ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="e5d10-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="e5d10-103">通知探查器已发生从托管代码到非托管代码的转换。</span><span class="sxs-lookup"><span data-stu-id="e5d10-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d10-104">语法</span><span class="sxs-lookup"><span data-stu-id="e5d10-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5d10-105">参数</span><span class="sxs-lookup"><span data-stu-id="e5d10-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e5d10-106">中正在调用的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="e5d10-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="e5d10-107">中一个[COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md)枚举的值，该值指示是否由于从托管代码调用非托管代码而发生转换，或者是否是由非托管函数调用的托管函数返回。</span><span class="sxs-lookup"><span data-stu-id="e5d10-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5d10-108">注解</span><span class="sxs-lookup"><span data-stu-id="e5d10-108">Remarks</span></span>  
 <span data-ttu-id="e5d10-109">如果的值 `reason` 为 COR_PRF_TRANSITION_CALL，则函数 ID 为非托管函数的 ID，该函数从未使用实时编译器进行编译。</span><span class="sxs-lookup"><span data-stu-id="e5d10-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="e5d10-110">非托管函数具有与之关联的基本信息，如名称和某些元数据。</span><span class="sxs-lookup"><span data-stu-id="e5d10-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="e5d10-111">如果使用隐式平台调用（PInvoke）调用了非托管函数，则运行时无法确定调用的目标，的值 `functionId` 将为 null。</span><span class="sxs-lookup"><span data-stu-id="e5d10-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="e5d10-112">有关隐式 PInvoke 的详细信息，请参阅[使用 c + + 互操作（隐式 pinvoke）](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。</span><span class="sxs-lookup"><span data-stu-id="e5d10-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d10-113">要求</span><span class="sxs-lookup"><span data-stu-id="e5d10-113">Requirements</span></span>  
 <span data-ttu-id="e5d10-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5d10-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5d10-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5d10-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5d10-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5d10-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5d10-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5d10-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d10-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5d10-118">See also</span></span>

- [<span data-ttu-id="e5d10-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="e5d10-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e5d10-120">UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="e5d10-120">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="e5d10-121">在 c + + 中使用显式 PInvoke （DllImport 特性）</span><span class="sxs-lookup"><span data-stu-id="e5d10-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
