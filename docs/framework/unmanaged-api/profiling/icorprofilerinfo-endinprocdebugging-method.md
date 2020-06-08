---
title: ICorProfilerInfo::EndInprocDebugging 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: afbb007b6293e6e9cff92281a6f5e93b1e7924ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502972"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="8c0b5-102">ICorProfilerInfo::EndInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="8c0b5-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="8c0b5-103">关闭进程内调试会话。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="8c0b5-104">此方法在 .NET Framework 版本2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c0b5-105">语法</span><span class="sxs-lookup"><span data-stu-id="8c0b5-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c0b5-106">参数</span><span class="sxs-lookup"><span data-stu-id="8c0b5-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="8c0b5-107">中一个值，该值标识调试会话。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="8c0b5-108">此值必须与在[ICorProfilerInfo：： BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md)方法中接收的值相同。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c0b5-109">注解</span><span class="sxs-lookup"><span data-stu-id="8c0b5-109">Remarks</span></span>  
 <span data-ttu-id="8c0b5-110">必须在同一回调方法中调用[ICorProfilerInfo：： BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md)和 `EndInprocDebugging` 。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-110">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="8c0b5-111">CLR 调试服务支持 .NET Framework 版本1.0 和1.1 中的有限进程内调试。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="8c0b5-112">进程内调试使探查器能够使用调试 API 的检查部分。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="8c0b5-113">不过，由于客户反馈，已从版本2.0 中的 .NET Framework 中删除进程内调试，并将其替换为一组功能，这些功能与分析 API 行更详细。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c0b5-114">要求</span><span class="sxs-lookup"><span data-stu-id="8c0b5-114">Requirements</span></span>  
 <span data-ttu-id="8c0b5-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c0b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0b5-116">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c0b5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c0b5-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c0b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c0b5-118">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="8c0b5-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0b5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c0b5-119">See also</span></span>

- [<span data-ttu-id="8c0b5-120">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="8c0b5-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
