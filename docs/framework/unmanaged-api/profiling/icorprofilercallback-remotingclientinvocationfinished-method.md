---
title: ICorProfilerCallback::RemotingClientInvocationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
ms.openlocfilehash: f5786db1f17e8a463dc78f9c93464145be3a8f32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499982"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="4b47b-102">ICorProfilerCallback::RemotingClientInvocationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="4b47b-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="4b47b-103">通知探查器远程处理调用已在客户端上完成运行。</span><span class="sxs-lookup"><span data-stu-id="4b47b-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b47b-104">语法</span><span class="sxs-lookup"><span data-stu-id="4b47b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b47b-105">备注</span><span class="sxs-lookup"><span data-stu-id="4b47b-105">Remarks</span></span>  
 <span data-ttu-id="4b47b-106">如果远程处理调用是同步的，则它还会在服务器上运行到完成。</span><span class="sxs-lookup"><span data-stu-id="4b47b-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="4b47b-107">如果远程处理调用是异步的，则在处理调用时可能仍会出现回复。</span><span class="sxs-lookup"><span data-stu-id="4b47b-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="4b47b-108">如果需要答复，则会作为对[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)的调用，以及对的其他调用 `RemotingClientInvocationFinished` 以指示异步调用所需的辅助处理。</span><span class="sxs-lookup"><span data-stu-id="4b47b-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="4b47b-109">以下每对回调都将在同一线程上进行：</span><span class="sxs-lookup"><span data-stu-id="4b47b-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="4b47b-110">`RemotingClientInvocationStarted`和[ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="4b47b-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="4b47b-111">[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)和[ICorProfilerCallback：： RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="4b47b-111">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="4b47b-112">[ICorProfilerCallback：： RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md)和[ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="4b47b-112">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="4b47b-113">应注意远程处理回调的以下问题：</span><span class="sxs-lookup"><span data-stu-id="4b47b-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="4b47b-114">远程处理函数的执行不会由探查器 API 反射，因此无法正确地接收从客户端调用并在服务器上执行的函数的通知。</span><span class="sxs-lookup"><span data-stu-id="4b47b-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="4b47b-115">实际调用是通过代理对象进行的;对于探查器，似乎某些函数是 JIT 编译的，但从未使用过。</span><span class="sxs-lookup"><span data-stu-id="4b47b-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="4b47b-116">探查器不会为异步远程处理事件接收准确的通知。</span><span class="sxs-lookup"><span data-stu-id="4b47b-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b47b-117">要求</span><span class="sxs-lookup"><span data-stu-id="4b47b-117">Requirements</span></span>  
 <span data-ttu-id="4b47b-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b47b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b47b-119">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b47b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b47b-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b47b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b47b-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b47b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b47b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b47b-122">See also</span></span>

- [<span data-ttu-id="4b47b-123">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="4b47b-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
