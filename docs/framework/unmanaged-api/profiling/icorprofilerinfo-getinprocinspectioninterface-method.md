---
title: ICorProfilerInfo::GetInprocInspectionInterface 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: 2fe0b314f761cf3c7a3a926d40c69302d0ece000
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498084"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="b6ac6-102">ICorProfilerInfo::GetInprocInspectionInterface 方法</span><span class="sxs-lookup"><span data-stu-id="b6ac6-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="b6ac6-103">获取一个对象，该对象可查询 "ICorDebugProcess" 接口。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="b6ac6-104">此方法在 .NET Framework 版本2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ac6-105">语法</span><span class="sxs-lookup"><span data-stu-id="b6ac6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ac6-106">参数</span><span class="sxs-lookup"><span data-stu-id="b6ac6-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="b6ac6-107">可在接口上查询的[out](/cpp/atl/iunknown)对象 `ICorDebugProcess` 。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6ac6-108">注解</span><span class="sxs-lookup"><span data-stu-id="b6ac6-108">Remarks</span></span>  
 <span data-ttu-id="b6ac6-109">公共语言运行时（CLR）调试 API 在 .NET Framework 版本1.0 中支持有限的进程内调试。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="b6ac6-110">进程内调试使探查器能够使用调试 API 的检查部分。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="b6ac6-111">由于客户反馈，已从版本2.0 中的 .NET Framework 中删除进程内调试，并将其替换为一组功能，这些功能与分析 API 是一种更多的功能。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ac6-112">要求</span><span class="sxs-lookup"><span data-stu-id="b6ac6-112">Requirements</span></span>  
 <span data-ttu-id="b6ac6-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6ac6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ac6-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6ac6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6ac6-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ac6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ac6-116">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="b6ac6-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ac6-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6ac6-117">See also</span></span>

- [<span data-ttu-id="b6ac6-118">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="b6ac6-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
