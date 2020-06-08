---
title: ICorProfilerCallback::AppDomainCreationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500489"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="65552-102">ICorProfilerCallback::AppDomainCreationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="65552-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="65552-103">通知探查器已创建应用程序域。</span><span class="sxs-lookup"><span data-stu-id="65552-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65552-104">语法</span><span class="sxs-lookup"><span data-stu-id="65552-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="65552-105">参数</span><span class="sxs-lookup"><span data-stu-id="65552-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="65552-106">\[中的] 标识已创建的域。</span><span class="sxs-lookup"><span data-stu-id="65552-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="65552-107">\[in] 一个 HRESULT，指示是否已成功完成创建应用程序域。</span><span class="sxs-lookup"><span data-stu-id="65552-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="65552-108">注解</span><span class="sxs-lookup"><span data-stu-id="65552-108">Remarks</span></span>  
 <span data-ttu-id="65552-109">在调用方法之前，应用程序 ID 对于任何信息请求均无效 `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="65552-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="65552-110">在回调后，某些加载应用程序域的部分可能会继续 `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="65552-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="65552-111">中的 HRESULT 失败 `hrStatus` 表示失败。</span><span class="sxs-lookup"><span data-stu-id="65552-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="65552-112">但是，中的成功 HRESULT `hrStatus` 仅指示创建应用程序域的第一部分已成功。</span><span class="sxs-lookup"><span data-stu-id="65552-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65552-113">要求</span><span class="sxs-lookup"><span data-stu-id="65552-113">Requirements</span></span>  
 <span data-ttu-id="65552-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65552-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65552-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65552-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65552-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65552-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65552-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65552-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65552-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65552-118">See also</span></span>

- [<span data-ttu-id="65552-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="65552-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
