---
title: ICorProfilerInfo::GetThreadInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 532288364b2db1e6be49b9e6f87019b1e41e6866
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497915"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="cb50f-102">ICorProfilerInfo::GetThreadInfo 方法</span><span class="sxs-lookup"><span data-stu-id="cb50f-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="cb50f-103">获取指定线程的当前 Win32 线程标识。</span><span class="sxs-lookup"><span data-stu-id="cb50f-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb50f-104">语法</span><span class="sxs-lookup"><span data-stu-id="cb50f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb50f-105">参数</span><span class="sxs-lookup"><span data-stu-id="cb50f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cb50f-106">中要获取其当前 Win32 ID 的线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="cb50f-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="cb50f-107">弄指向指定线程的当前 Win32 线程 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="cb50f-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb50f-108">要求</span><span class="sxs-lookup"><span data-stu-id="cb50f-108">Requirements</span></span>  
 <span data-ttu-id="cb50f-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb50f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb50f-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb50f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb50f-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb50f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb50f-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb50f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb50f-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb50f-113">See also</span></span>

- [<span data-ttu-id="cb50f-114">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="cb50f-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
