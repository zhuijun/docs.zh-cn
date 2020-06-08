---
title: ICorProfilerCallback3::ProfilerDetachSucceeded 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: 93406dddf7babd8cf61032666737b993c2f721f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499592"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="408ae-102">ICorProfilerCallback3::ProfilerDetachSucceeded 方法</span><span class="sxs-lookup"><span data-stu-id="408ae-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="408ae-103">通知探查器公共语言运行时 (CLR) 将要卸载探查器 DLL。</span><span class="sxs-lookup"><span data-stu-id="408ae-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408ae-104">语法</span><span class="sxs-lookup"><span data-stu-id="408ae-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="408ae-105">返回值</span><span class="sxs-lookup"><span data-stu-id="408ae-105">Return Value</span></span>  
 <span data-ttu-id="408ae-106">将忽略来自此回调的返回值。</span><span class="sxs-lookup"><span data-stu-id="408ae-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="408ae-107">注解</span><span class="sxs-lookup"><span data-stu-id="408ae-107">Remarks</span></span>  
 <span data-ttu-id="408ae-108">在所有线程均退出探查器的代码之后，发出`ProfilerDetachSucceeded` 回调。</span><span class="sxs-lookup"><span data-stu-id="408ae-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="408ae-109">当调用此方法时，探查器应执行任何不适合用于其析构函数的的最后执行的任务，例如通知其 UI 或日志记录组件。</span><span class="sxs-lookup"><span data-stu-id="408ae-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="408ae-110">但是，探查器不能在此回调期间（如[ICorProfilerInfo](icorprofilerinfo-interface.md)或接口）对 CLR 提供的接口调用函数 `IMetaData*` 。</span><span class="sxs-lookup"><span data-stu-id="408ae-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="408ae-111">CLR 在 Windows 应用程序事件日志中创建条目，用于表示分离操作成功。</span><span class="sxs-lookup"><span data-stu-id="408ae-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="408ae-112">探查器从此回调返回后，CLR 将释放探查器对象并卸载探查器 DLL。</span><span class="sxs-lookup"><span data-stu-id="408ae-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="408ae-113">因此，探查器不可执行任何会导致探查器 DLL 从此回调返回后其内部进行执行的操作。</span><span class="sxs-lookup"><span data-stu-id="408ae-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="408ae-114">例如，它不能创建线程或注册计时器回调。</span><span class="sxs-lookup"><span data-stu-id="408ae-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408ae-115">要求</span><span class="sxs-lookup"><span data-stu-id="408ae-115">Requirements</span></span>  
 <span data-ttu-id="408ae-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="408ae-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408ae-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="408ae-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="408ae-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="408ae-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="408ae-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408ae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408ae-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="408ae-120">See also</span></span>

- [<span data-ttu-id="408ae-121">元数据接口</span><span class="sxs-lookup"><span data-stu-id="408ae-121">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
- [<span data-ttu-id="408ae-122">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="408ae-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="408ae-123">分析接口</span><span class="sxs-lookup"><span data-stu-id="408ae-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="408ae-124">分析</span><span class="sxs-lookup"><span data-stu-id="408ae-124">Profiling</span></span>](index.md)
