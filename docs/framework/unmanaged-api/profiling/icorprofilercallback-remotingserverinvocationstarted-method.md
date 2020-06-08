---
title: ICorProfilerCallback::RemotingServerInvocationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
ms.openlocfilehash: 3725b73ab55f6e4dc789a1fde8d1224695a174d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499930"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="605cc-102">ICorProfilerCallback::RemotingServerInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="605cc-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="605cc-103">通知探查器进程正在调用方法以响应远程方法调用请求。</span><span class="sxs-lookup"><span data-stu-id="605cc-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605cc-104">语法</span><span class="sxs-lookup"><span data-stu-id="605cc-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="605cc-105">要求</span><span class="sxs-lookup"><span data-stu-id="605cc-105">Requirements</span></span>  
 <span data-ttu-id="605cc-106">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="605cc-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="605cc-107">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="605cc-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="605cc-108">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="605cc-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="605cc-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="605cc-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605cc-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="605cc-110">See also</span></span>

- [<span data-ttu-id="605cc-111">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="605cc-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
