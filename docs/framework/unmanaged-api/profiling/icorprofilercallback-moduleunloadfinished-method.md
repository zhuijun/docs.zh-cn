---
title: ICorProfilerCallback::ModuleUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: fd35f47c004d1ffb235cefe1cd2a1eb2c1fffaef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503310"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="9cb85-102">ICorProfilerCallback::ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9cb85-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="9cb85-103">通知探查器模块已完成卸载。</span><span class="sxs-lookup"><span data-stu-id="9cb85-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb85-104">语法</span><span class="sxs-lookup"><span data-stu-id="9cb85-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb85-105">参数</span><span class="sxs-lookup"><span data-stu-id="9cb85-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9cb85-106">中已卸载的模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="9cb85-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="9cb85-107">中一个 HRESULT，指示该模块是否已成功卸载。</span><span class="sxs-lookup"><span data-stu-id="9cb85-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb85-108">注解</span><span class="sxs-lookup"><span data-stu-id="9cb85-108">Remarks</span></span>  
 <span data-ttu-id="9cb85-109">在 `moduleId` [ICorProfilerCallback：： ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md)方法返回后，的值对信息请求无效。</span><span class="sxs-lookup"><span data-stu-id="9cb85-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="9cb85-110">卸载类的某些部分可能会在回调后继续 `ModuleUnloadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="9cb85-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="9cb85-111">中的 HRESULT 失败 `hrStatus` 表示失败。</span><span class="sxs-lookup"><span data-stu-id="9cb85-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9cb85-112">但是，中的成功 HRESULT `hrStatus` 仅指示卸载模块的第一部分已成功。</span><span class="sxs-lookup"><span data-stu-id="9cb85-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb85-113">要求</span><span class="sxs-lookup"><span data-stu-id="9cb85-113">Requirements</span></span>  
 <span data-ttu-id="9cb85-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cb85-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb85-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9cb85-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9cb85-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cb85-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cb85-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb85-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb85-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9cb85-118">See also</span></span>

- [<span data-ttu-id="9cb85-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="9cb85-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
