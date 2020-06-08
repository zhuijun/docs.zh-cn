---
title: ICorProfilerCallback2::ThreadNameChanged 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 3eb108ed20d0fd1287cb82eb4d552206aeae15d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499722"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="6b03e-102">ICorProfilerCallback2::ThreadNameChanged 方法</span><span class="sxs-lookup"><span data-stu-id="6b03e-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="6b03e-103">通知代码探查器线程的名称已更改。</span><span class="sxs-lookup"><span data-stu-id="6b03e-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b03e-104">语法</span><span class="sxs-lookup"><span data-stu-id="6b03e-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b03e-105">参数</span><span class="sxs-lookup"><span data-stu-id="6b03e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="6b03e-106">中线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="6b03e-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6b03e-107">中线程的新名称的长度。</span><span class="sxs-lookup"><span data-stu-id="6b03e-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="6b03e-108">中线程的新名称。</span><span class="sxs-lookup"><span data-stu-id="6b03e-108">[in] The new name of the thread.</span></span> <span data-ttu-id="6b03e-109">名称不以 null 结尾。</span><span class="sxs-lookup"><span data-stu-id="6b03e-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b03e-110">要求</span><span class="sxs-lookup"><span data-stu-id="6b03e-110">Requirements</span></span>  
 <span data-ttu-id="6b03e-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b03e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b03e-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b03e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b03e-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b03e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b03e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b03e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b03e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b03e-115">See also</span></span>

- [<span data-ttu-id="6b03e-116">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="6b03e-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6b03e-117">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="6b03e-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
