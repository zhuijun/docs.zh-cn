---
title: ICorProfilerCallback::AssemblyUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: d00e67d29921edc6b7487ceeb12aaa9e9f9bd0ac
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500411"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="fd88a-102">ICorProfilerCallback::AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fd88a-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="fd88a-103">通知探查器已卸载程序集。</span><span class="sxs-lookup"><span data-stu-id="fd88a-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd88a-104">语法</span><span class="sxs-lookup"><span data-stu-id="fd88a-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd88a-105">参数</span><span class="sxs-lookup"><span data-stu-id="fd88a-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="fd88a-106">\[in] 标识正在卸载的程序集。</span><span class="sxs-lookup"><span data-stu-id="fd88a-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="fd88a-107">\[in] 一个 HRESULT，指示程序集是否已成功卸载。</span><span class="sxs-lookup"><span data-stu-id="fd88a-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd88a-108">注解</span><span class="sxs-lookup"><span data-stu-id="fd88a-108">Remarks</span></span>  
 <span data-ttu-id="fd88a-109">在 `assemblyId` [ICorProfilerCallback：： AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md)方法返回后，的值对信息请求无效。</span><span class="sxs-lookup"><span data-stu-id="fd88a-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="fd88a-110">在回调后，卸载程序集的某些部分可能会继续 `AssemblyUnloadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="fd88a-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="fd88a-111">中的 HRESULT 失败 `hrStatus` 表示失败。</span><span class="sxs-lookup"><span data-stu-id="fd88a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fd88a-112">但是，中的成功 HRESULT `hrStatus` 仅指示卸载程序集的第一部分已成功。</span><span class="sxs-lookup"><span data-stu-id="fd88a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd88a-113">要求</span><span class="sxs-lookup"><span data-stu-id="fd88a-113">Requirements</span></span>  
 <span data-ttu-id="fd88a-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd88a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd88a-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd88a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd88a-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd88a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd88a-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd88a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd88a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd88a-118">See also</span></span>

- [<span data-ttu-id="fd88a-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="fd88a-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
