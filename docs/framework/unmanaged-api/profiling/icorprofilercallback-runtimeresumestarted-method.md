---
title: ICorProfilerCallback::RuntimeResumeStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: 08e76e295e30ede48733ab35870ec965eb157f60
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499865"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="cd1a9-102">ICorProfilerCallback::RuntimeResumeStarted 方法</span><span class="sxs-lookup"><span data-stu-id="cd1a9-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="cd1a9-103">通知探查器运行时正在恢复所有运行时线程。</span><span class="sxs-lookup"><span data-stu-id="cd1a9-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd1a9-104">语法</span><span class="sxs-lookup"><span data-stu-id="cd1a9-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="cd1a9-105">要求</span><span class="sxs-lookup"><span data-stu-id="cd1a9-105">Requirements</span></span>  
 <span data-ttu-id="cd1a9-106">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd1a9-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd1a9-107">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd1a9-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd1a9-108">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd1a9-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd1a9-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd1a9-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1a9-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd1a9-110">See also</span></span>

- [<span data-ttu-id="cd1a9-111">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="cd1a9-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cd1a9-112">RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="cd1a9-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
