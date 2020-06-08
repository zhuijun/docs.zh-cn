---
title: ICorProfilerInfo2::GetThreadAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 70535f8bcee95c2596c43617eb5893e2d92a355b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496772"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="0dd00-102">ICorProfilerInfo2::GetThreadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="0dd00-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="0dd00-103">获取指定线程当前正在执行代码的应用程序域的 ID。</span><span class="sxs-lookup"><span data-stu-id="0dd00-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd00-104">语法</span><span class="sxs-lookup"><span data-stu-id="0dd00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dd00-105">参数</span><span class="sxs-lookup"><span data-stu-id="0dd00-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0dd00-106">中指定线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="0dd00-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="0dd00-107">弄指向应用程序域的 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="0dd00-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dd00-108">要求</span><span class="sxs-lookup"><span data-stu-id="0dd00-108">Requirements</span></span>  
 <span data-ttu-id="0dd00-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0dd00-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dd00-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0dd00-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0dd00-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dd00-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dd00-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dd00-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd00-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0dd00-113">See also</span></span>

- [<span data-ttu-id="0dd00-114">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="0dd00-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0dd00-115">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="0dd00-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
