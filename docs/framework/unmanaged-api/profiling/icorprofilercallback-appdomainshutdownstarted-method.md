---
title: ICorProfilerCallback::AppDomainShutdownStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 1b973cdeaffbec0dad1f2d082c44e8001647fdcc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500450"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="82f78-102">ICorProfilerCallback::AppDomainShutdownStarted 方法</span><span class="sxs-lookup"><span data-stu-id="82f78-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="82f78-103">通知探查器正在从进程中卸载应用程序域。</span><span class="sxs-lookup"><span data-stu-id="82f78-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f78-104">语法</span><span class="sxs-lookup"><span data-stu-id="82f78-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82f78-105">参数</span><span class="sxs-lookup"><span data-stu-id="82f78-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="82f78-106">\[中的] 标识存储应用程序的程序集的域。</span><span class="sxs-lookup"><span data-stu-id="82f78-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="82f78-107">注解</span><span class="sxs-lookup"><span data-stu-id="82f78-107">Remarks</span></span>  
 <span data-ttu-id="82f78-108">`appDomainId`此方法返回后，的值对任何信息请求都无效 `AppDomainShutdownStarted` -这是探查器获取有关此应用程序域的信息的最后机会。</span><span class="sxs-lookup"><span data-stu-id="82f78-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f78-109">要求</span><span class="sxs-lookup"><span data-stu-id="82f78-109">Requirements</span></span>  
 <span data-ttu-id="82f78-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82f78-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f78-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82f78-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82f78-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82f78-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82f78-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f78-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f78-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82f78-114">See also</span></span>

- [<span data-ttu-id="82f78-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="82f78-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
