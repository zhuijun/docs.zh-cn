---
title: ICorProfilerCallback::ModuleLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503362"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="3af6b-102">ICorProfilerCallback::ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="3af6b-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="3af6b-103">通知探查器模块已完成加载。</span><span class="sxs-lookup"><span data-stu-id="3af6b-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af6b-104">语法</span><span class="sxs-lookup"><span data-stu-id="3af6b-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3af6b-105">参数</span><span class="sxs-lookup"><span data-stu-id="3af6b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3af6b-106">中已完成加载的模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="3af6b-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3af6b-107">中一个 HRESULT，指示是否已成功加载该模块。</span><span class="sxs-lookup"><span data-stu-id="3af6b-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3af6b-108">注解</span><span class="sxs-lookup"><span data-stu-id="3af6b-108">Remarks</span></span>  
 <span data-ttu-id="3af6b-109">在 `moduleId` 调用方法之前，的值对信息请求无效 `ModuleLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="3af6b-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="3af6b-110">在回调后，加载模块的某些部分可能会继续 `ModuleLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="3af6b-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="3af6b-111">中的 HRESULT 失败 `hrStatus` 表示失败。</span><span class="sxs-lookup"><span data-stu-id="3af6b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3af6b-112">但是，中的成功 HRESULT `hrStatus` 仅指示加载模块的第一部分已成功。</span><span class="sxs-lookup"><span data-stu-id="3af6b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3af6b-113">要求</span><span class="sxs-lookup"><span data-stu-id="3af6b-113">Requirements</span></span>  
 <span data-ttu-id="3af6b-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3af6b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3af6b-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3af6b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3af6b-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3af6b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3af6b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3af6b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af6b-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3af6b-118">See also</span></span>

- [<span data-ttu-id="3af6b-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="3af6b-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3af6b-120">ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="3af6b-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
