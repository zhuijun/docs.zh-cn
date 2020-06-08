---
title: ICorProfilerCallback::AssemblyLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500437"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="a3d3a-102">ICorProfilerCallback::AssemblyLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="a3d3a-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="a3d3a-103">通知探查器程序集已完成加载。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d3a-104">语法</span><span class="sxs-lookup"><span data-stu-id="a3d3a-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3d3a-105">参数</span><span class="sxs-lookup"><span data-stu-id="a3d3a-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="a3d3a-106">\[in] 标识已加载的程序集。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="a3d3a-107">\[in] 一个 HRESULT，指示程序集是否已成功加载。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3d3a-108">注解</span><span class="sxs-lookup"><span data-stu-id="a3d3a-108">Remarks</span></span>  
 <span data-ttu-id="a3d3a-109">在 `assemblyId` 调用方法之前，的值对信息请求无效 `AssemblyLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="a3d3a-110">在回调后，加载程序集的某些部分可能会继续 `AssemblyLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="a3d3a-111">中的 HRESULT 失败 `hrStatus` 表示失败。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a3d3a-112">但是，中的成功 HRESULT `hrStatus` 仅指示加载程序集的第一部分已成功完成。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3d3a-113">要求</span><span class="sxs-lookup"><span data-stu-id="a3d3a-113">Requirements</span></span>  
 <span data-ttu-id="a3d3a-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d3a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d3a-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3d3a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3d3a-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3d3a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3d3a-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3d3a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d3a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3d3a-118">See also</span></span>

- [<span data-ttu-id="a3d3a-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="a3d3a-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
