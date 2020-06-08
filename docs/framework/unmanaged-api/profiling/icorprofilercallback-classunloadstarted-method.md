---
title: ICorProfilerCallback::ClassUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 86402abca5386f34256f1f44f674f1e1898ad5fd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500346"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="2daa9-102">ICorProfilerCallback::ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="2daa9-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="2daa9-103">通知探查器正在卸载某个类。</span><span class="sxs-lookup"><span data-stu-id="2daa9-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2daa9-104">语法</span><span class="sxs-lookup"><span data-stu-id="2daa9-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2daa9-105">参数</span><span class="sxs-lookup"><span data-stu-id="2daa9-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="2daa9-106">\[in] 标识正在卸载的类。</span><span class="sxs-lookup"><span data-stu-id="2daa9-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="2daa9-107">注解</span><span class="sxs-lookup"><span data-stu-id="2daa9-107">Remarks</span></span>  
 <span data-ttu-id="2daa9-108">在 `classId` 方法返回后，的值对信息请求无效 `ClassUnloadStarted` -这是探查器获取有关此类的信息的最后机会。</span><span class="sxs-lookup"><span data-stu-id="2daa9-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2daa9-109">要求</span><span class="sxs-lookup"><span data-stu-id="2daa9-109">Requirements</span></span>  
 <span data-ttu-id="2daa9-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2daa9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2daa9-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2daa9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2daa9-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2daa9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2daa9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2daa9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2daa9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2daa9-114">See also</span></span>

- [<span data-ttu-id="2daa9-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="2daa9-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2daa9-116">ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="2daa9-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
