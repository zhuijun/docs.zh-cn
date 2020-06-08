---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 6d732c6c2871cc5e042b8504db26aabb19963f8c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500502"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="4e98d-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="4e98d-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="4e98d-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="4e98d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4e98d-104">通知程序集引用的公共语言运行时（CLR），探查器计划将其添加到[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回调中。</span><span class="sxs-lookup"><span data-stu-id="4e98d-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e98d-105">语法</span><span class="sxs-lookup"><span data-stu-id="4e98d-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e98d-106">参数</span><span class="sxs-lookup"><span data-stu-id="4e98d-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="4e98d-107">指向[COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md)结构的指针，该结构为 CLR 提供有关在执行程序集引用闭包审核时应考虑的程序集引用的信息。</span><span class="sxs-lookup"><span data-stu-id="4e98d-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="4e98d-108">注解</span><span class="sxs-lookup"><span data-stu-id="4e98d-108">Remarks</span></span>  
 <span data-ttu-id="4e98d-109">探查器为其计划从 `wszAssemblyPath` [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回调的参数中指定的程序集引用的每个目标程序集调用此方法。</span><span class="sxs-lookup"><span data-stu-id="4e98d-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="4e98d-110">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)接口对象传递给探查器的[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回调，同时传递给参数中的程序集路径和名称 `wszAssemblyPath` 。</span><span class="sxs-lookup"><span data-stu-id="4e98d-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e98d-111">要求</span><span class="sxs-lookup"><span data-stu-id="4e98d-111">Requirements</span></span>  
 <span data-ttu-id="4e98d-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e98d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e98d-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e98d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e98d-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e98d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e98d-115">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e98d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e98d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e98d-116">See also</span></span>

- [<span data-ttu-id="4e98d-117">ICorProfilerAssemblyReferenceProvider 方法</span><span class="sxs-lookup"><span data-stu-id="4e98d-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="4e98d-118">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="4e98d-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="4e98d-119">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="4e98d-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
