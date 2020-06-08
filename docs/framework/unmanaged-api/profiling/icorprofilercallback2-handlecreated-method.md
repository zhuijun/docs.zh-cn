---
title: ICorProfilerCallback2::HandleCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 772f0c00bb850e35a6f5bf7fa4df2b3052999df5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499787"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="b4df2-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="b4df2-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="b4df2-103">通知代码探查器已创建垃圾回收句柄。</span><span class="sxs-lookup"><span data-stu-id="b4df2-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4df2-104">语法</span><span class="sxs-lookup"><span data-stu-id="b4df2-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4df2-105">参数</span><span class="sxs-lookup"><span data-stu-id="b4df2-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="b4df2-106">中垃圾回收的句柄的 ID。</span><span class="sxs-lookup"><span data-stu-id="b4df2-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="b4df2-107">中为其创建垃圾回收句柄的对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="b4df2-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4df2-108">要求</span><span class="sxs-lookup"><span data-stu-id="b4df2-108">Requirements</span></span>  
 <span data-ttu-id="b4df2-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4df2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4df2-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4df2-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4df2-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4df2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4df2-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4df2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4df2-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4df2-113">See also</span></span>

- [<span data-ttu-id="b4df2-114">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="b4df2-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b4df2-115">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="b4df2-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
