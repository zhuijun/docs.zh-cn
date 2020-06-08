---
title: ICorProfilerCallback::RemotingClientInvocationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
ms.openlocfilehash: 8a042e71690b5ae77c1e4cda7be394a163ab2774
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503258"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="0daa3-102">ICorProfilerCallback::RemotingClientInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0daa3-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="0daa3-103">通知探查器已开始远程调用。</span><span class="sxs-lookup"><span data-stu-id="0daa3-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0daa3-104">语法</span><span class="sxs-lookup"><span data-stu-id="0daa3-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0daa3-105">备注</span><span class="sxs-lookup"><span data-stu-id="0daa3-105">Remarks</span></span>  
 <span data-ttu-id="0daa3-106">此事件对于同步和异步调用是相同的。</span><span class="sxs-lookup"><span data-stu-id="0daa3-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="0daa3-107">以下每对回调都将在同一线程上进行：</span><span class="sxs-lookup"><span data-stu-id="0daa3-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="0daa3-108">`RemotingClientInvocationStarted`和[ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="0daa3-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="0daa3-109">[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)和[ICorProfilerCallback：： RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="0daa3-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="0daa3-110">[ICorProfilerCallback：： RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md)和[ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="0daa3-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="0daa3-111">应注意远程处理回调的以下问题：</span><span class="sxs-lookup"><span data-stu-id="0daa3-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="0daa3-112">远程处理函数的执行不会由探查器 API 反射，因此无法正确地接收从客户端调用并在服务器上执行的函数的通知。</span><span class="sxs-lookup"><span data-stu-id="0daa3-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="0daa3-113">实际调用是通过代理对象进行的;对于探查器，似乎某些函数是 JIT 编译的，但从未使用过。</span><span class="sxs-lookup"><span data-stu-id="0daa3-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="0daa3-114">探查器不会为异步远程处理事件接收准确的通知。</span><span class="sxs-lookup"><span data-stu-id="0daa3-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0daa3-115">要求</span><span class="sxs-lookup"><span data-stu-id="0daa3-115">Requirements</span></span>  
 <span data-ttu-id="0daa3-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0daa3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0daa3-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0daa3-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0daa3-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0daa3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0daa3-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0daa3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0daa3-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0daa3-120">See also</span></span>

- [<span data-ttu-id="0daa3-121">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="0daa3-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
