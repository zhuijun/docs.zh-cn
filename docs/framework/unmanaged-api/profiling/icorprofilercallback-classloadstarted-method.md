---
title: ICorProfilerCallback::ClassLoadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500359"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="d5154-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d5154-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="d5154-103">通知探查器正在加载某个类。</span><span class="sxs-lookup"><span data-stu-id="d5154-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5154-104">语法</span><span class="sxs-lookup"><span data-stu-id="d5154-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5154-105">参数</span><span class="sxs-lookup"><span data-stu-id="d5154-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="d5154-106">\[in] 标识正在加载的类。</span><span class="sxs-lookup"><span data-stu-id="d5154-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5154-107">注解</span><span class="sxs-lookup"><span data-stu-id="d5154-107">Remarks</span></span>  
 <span data-ttu-id="d5154-108">在 `classId` 调用[ICorProfilerCallback：： ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)方法之前，的值对信息请求无效。</span><span class="sxs-lookup"><span data-stu-id="d5154-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5154-109">要求</span><span class="sxs-lookup"><span data-stu-id="d5154-109">Requirements</span></span>  
 <span data-ttu-id="d5154-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5154-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5154-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5154-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5154-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5154-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5154-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5154-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5154-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5154-114">See also</span></span>

- [<span data-ttu-id="d5154-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="d5154-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
