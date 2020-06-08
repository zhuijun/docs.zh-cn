---
title: ICorProfilerCallback::ThreadAssignedToOSThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 182a82300183046ccb4a93a79af0dd8f23848c20
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503167"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="bccee-102">ICorProfilerCallback::ThreadAssignedToOSThread 方法</span><span class="sxs-lookup"><span data-stu-id="bccee-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="bccee-103">通知探查器使用特定操作系统线程实现了托管线程。</span><span class="sxs-lookup"><span data-stu-id="bccee-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccee-104">语法</span><span class="sxs-lookup"><span data-stu-id="bccee-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bccee-105">参数</span><span class="sxs-lookup"><span data-stu-id="bccee-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="bccee-106">中托管线程的标识符。</span><span class="sxs-lookup"><span data-stu-id="bccee-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="bccee-107">中操作系统线程的标识符。</span><span class="sxs-lookup"><span data-stu-id="bccee-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bccee-108">注解</span><span class="sxs-lookup"><span data-stu-id="bccee-108">Remarks</span></span>  
 <span data-ttu-id="bccee-109">`ThreadAssignedToOSThread`回调存在，以便探查器能够在操作系统线程的纤程之间保持准确映射到托管线程。</span><span class="sxs-lookup"><span data-stu-id="bccee-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bccee-110">要求</span><span class="sxs-lookup"><span data-stu-id="bccee-110">Requirements</span></span>  
 <span data-ttu-id="bccee-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bccee-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccee-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bccee-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bccee-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bccee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bccee-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccee-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bccee-115">See also</span></span>

- [<span data-ttu-id="bccee-116">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="bccee-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
