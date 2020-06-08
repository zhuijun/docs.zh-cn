---
title: ICorProfilerInfo3::EnumJITedFunctions 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 3ebf4a7706b3d3495e4a617b4f86a50281115436
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496550"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="981ec-102">ICorProfilerInfo3::EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="981ec-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="981ec-103">返回之前 JIT 编译的所有函数的枚举器。</span><span class="sxs-lookup"><span data-stu-id="981ec-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981ec-104">语法</span><span class="sxs-lookup"><span data-stu-id="981ec-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="981ec-105">参数</span><span class="sxs-lookup"><span data-stu-id="981ec-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="981ec-106">弄指向[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="981ec-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="981ec-107">注解</span><span class="sxs-lookup"><span data-stu-id="981ec-107">Remarks</span></span>  
 <span data-ttu-id="981ec-108">此方法可能与 `JITCompilation` 回调（如[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)方法）重叠。</span><span class="sxs-lookup"><span data-stu-id="981ec-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="981ec-109">此方法返回的枚举器不包括从使用 Ngen.exe 生成的本机映像加载的函数。</span><span class="sxs-lookup"><span data-stu-id="981ec-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="981ec-110">对于字段的值，返回的枚举只包含 "0" `COR_PRF_FUNCTION::reJitId` 。</span><span class="sxs-lookup"><span data-stu-id="981ec-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="981ec-111">如果需要有效值 `COR_PRF_FUNCTION::reJitId` ，请使用[ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="981ec-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="981ec-112">要求</span><span class="sxs-lookup"><span data-stu-id="981ec-112">Requirements</span></span>  
 <span data-ttu-id="981ec-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="981ec-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="981ec-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="981ec-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="981ec-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="981ec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="981ec-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="981ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981ec-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="981ec-117">See also</span></span>

- [<span data-ttu-id="981ec-118">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="981ec-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="981ec-119">分析接口</span><span class="sxs-lookup"><span data-stu-id="981ec-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="981ec-120">分析</span><span class="sxs-lookup"><span data-stu-id="981ec-120">Profiling</span></span>](index.md)
