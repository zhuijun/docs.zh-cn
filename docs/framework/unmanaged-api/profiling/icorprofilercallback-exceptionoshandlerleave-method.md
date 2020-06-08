---
title: ICorProfilerCallback::ExceptionOSHandlerLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: 5ba45cf526a6ebca6975a75d06308d089770ad5b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500255"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="9d0fe-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="9d0fe-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="9d0fe-103">未实现。</span><span class="sxs-lookup"><span data-stu-id="9d0fe-103">Not implemented.</span></span> <span data-ttu-id="9d0fe-104">需要非托管异常信息的探查器必须通过其他方式获取此信息。</span><span class="sxs-lookup"><span data-stu-id="9d0fe-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0fe-105">语法</span><span class="sxs-lookup"><span data-stu-id="9d0fe-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9d0fe-106">要求</span><span class="sxs-lookup"><span data-stu-id="9d0fe-106">Requirements</span></span>  
 <span data-ttu-id="9d0fe-107">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d0fe-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d0fe-108">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d0fe-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d0fe-109">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d0fe-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d0fe-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d0fe-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0fe-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d0fe-111">See also</span></span>

- [<span data-ttu-id="9d0fe-112">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="9d0fe-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
