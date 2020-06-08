---
title: ICorProfilerInfo::GetCurrentThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498396"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="34ea3-102">ICorProfilerInfo::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="34ea3-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="34ea3-103">获取当前线程的 ID （如果它是托管线程）。</span><span class="sxs-lookup"><span data-stu-id="34ea3-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34ea3-104">语法</span><span class="sxs-lookup"><span data-stu-id="34ea3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34ea3-105">参数</span><span class="sxs-lookup"><span data-stu-id="34ea3-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="34ea3-106">弄指向托管线程的返回 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="34ea3-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34ea3-107">注解</span><span class="sxs-lookup"><span data-stu-id="34ea3-107">Remarks</span></span>  
 <span data-ttu-id="34ea3-108">如果当前线程是内部运行时线程或其他非托管线程，则 `GetCurrentThreadID` 返回 CORPROF_E_NOT_MANAGED_THREAD 作为 HRESULT，并且参数的返回值 `pThreadId` 将为 null。</span><span class="sxs-lookup"><span data-stu-id="34ea3-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34ea3-109">要求</span><span class="sxs-lookup"><span data-stu-id="34ea3-109">Requirements</span></span>  
 <span data-ttu-id="34ea3-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34ea3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34ea3-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34ea3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34ea3-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34ea3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34ea3-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34ea3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ea3-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34ea3-114">See also</span></span>

- [<span data-ttu-id="34ea3-115">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="34ea3-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
