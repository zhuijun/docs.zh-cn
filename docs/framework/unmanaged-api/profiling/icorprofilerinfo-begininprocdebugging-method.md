---
title: ICorProfilerInfo::BeginInprocDebugging 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: f0b118ef109d0adb17a28b60c091390b8e4280c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498656"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="fe2ce-102">ICorProfilerInfo::BeginInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="fe2ce-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="fe2ce-103">初始化进程内调试支持。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="fe2ce-104">此方法在 .NET Framework 版本2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2ce-105">语法</span><span class="sxs-lookup"><span data-stu-id="fe2ce-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe2ce-106">参数</span><span class="sxs-lookup"><span data-stu-id="fe2ce-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="fe2ce-107">中将此值设置为 `true` 以仅初始化当前线程的调试支持; 将其设置为 `false` 以初始化对所有线程的调试支持。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="fe2ce-108">弄指向用于标识调试会话的返回值的指针。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe2ce-109">注解</span><span class="sxs-lookup"><span data-stu-id="fe2ce-109">Remarks</span></span>  
 <span data-ttu-id="fe2ce-110">CLR 调试服务支持 .NET Framework 版本1.0 和1.1 中的有限进程内调试。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="fe2ce-111">进程内调试使探查器能够使用调试 API 的检查部分。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="fe2ce-112">不过，由于客户反馈，已从版本2.0 中的 .NET Framework 中删除进程内调试，并将其替换为一组功能，这些功能与分析 API 行更详细。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe2ce-113">要求</span><span class="sxs-lookup"><span data-stu-id="fe2ce-113">Requirements</span></span>  
 <span data-ttu-id="fe2ce-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe2ce-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe2ce-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe2ce-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe2ce-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe2ce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe2ce-117">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="fe2ce-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2ce-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe2ce-118">See also</span></span>

- [<span data-ttu-id="fe2ce-119">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="fe2ce-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
