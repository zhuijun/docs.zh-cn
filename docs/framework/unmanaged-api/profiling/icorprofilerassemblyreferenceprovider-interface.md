---
title: ICorProfilerAssemblyReferenceProvider 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 17fb3de830d1aed2214631bbe8254a7f58030025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500515"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="0bef6-102">ICorProfilerAssemblyReferenceProvider 方法</span><span class="sxs-lookup"><span data-stu-id="0bef6-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="0bef6-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="0bef6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0bef6-104">启用探查器以通知程序集引用的公共语言运行时（CLR），探查器将在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回调中添加这些引用。</span><span class="sxs-lookup"><span data-stu-id="0bef6-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bef6-105">方法</span><span class="sxs-lookup"><span data-stu-id="0bef6-105">Methods</span></span>  
  
|<span data-ttu-id="0bef6-106">方法</span><span class="sxs-lookup"><span data-stu-id="0bef6-106">Method</span></span>|<span data-ttu-id="0bef6-107">说明</span><span class="sxs-lookup"><span data-stu-id="0bef6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bef6-108">AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="0bef6-108">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="0bef6-109">向 CLR 通知探查器计划在[ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回调中添加的程序集引用。</span><span class="sxs-lookup"><span data-stu-id="0bef6-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bef6-110">注解</span><span class="sxs-lookup"><span data-stu-id="0bef6-110">Remarks</span></span>  
 <span data-ttu-id="0bef6-111">CLR 将探查器的 `ICorProfilerAssemblyReferenceProvider` 接口对象传递给[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回调。</span><span class="sxs-lookup"><span data-stu-id="0bef6-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="0bef6-112">这使探查器能够通知程序集引用的 CLR，探查器计划稍后将其添加到[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)中。</span><span class="sxs-lookup"><span data-stu-id="0bef6-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="0bef6-113">回调中。</span><span class="sxs-lookup"><span data-stu-id="0bef6-113">callback.</span></span> <span data-ttu-id="0bef6-114">这提高了 CLR 的程序集引用闭包审核器，及其用于确定是否可以共享程序集的算法的准确性。</span><span class="sxs-lookup"><span data-stu-id="0bef6-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="0bef6-115">此接口只能在将此接口对象传递给探查器的[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回调中使用。</span><span class="sxs-lookup"><span data-stu-id="0bef6-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bef6-116">要求</span><span class="sxs-lookup"><span data-stu-id="0bef6-116">Requirements</span></span>  
 <span data-ttu-id="0bef6-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bef6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bef6-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0bef6-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0bef6-119">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bef6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bef6-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0bef6-120">See also</span></span>

- [<span data-ttu-id="0bef6-121">分析接口</span><span class="sxs-lookup"><span data-stu-id="0bef6-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
