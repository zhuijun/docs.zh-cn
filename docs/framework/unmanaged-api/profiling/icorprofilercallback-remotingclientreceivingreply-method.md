---
title: ICorProfilerCallback::RemotingClientReceivingReply 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 0a21924008bcbfa0894218f57aee559a564f8003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499969"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="50d05-102">ICorProfilerCallback::RemotingClientReceivingReply 方法</span><span class="sxs-lookup"><span data-stu-id="50d05-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="50d05-103">通知探查器远程处理调用的服务器端部分已完成，并且客户端现在正在接收，并即将处理答复。</span><span class="sxs-lookup"><span data-stu-id="50d05-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d05-104">语法</span><span class="sxs-lookup"><span data-stu-id="50d05-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="50d05-105">参数</span><span class="sxs-lookup"><span data-stu-id="50d05-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="50d05-106">中与以下条件下的[ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)中提供的值对应的值：</span><span class="sxs-lookup"><span data-stu-id="50d05-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="50d05-107">远程处理 GUID cookie 处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="50d05-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="50d05-108">通道成功传输消息。</span><span class="sxs-lookup"><span data-stu-id="50d05-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="50d05-109">GUID cookie 在服务器端进程中处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="50d05-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="50d05-110">这样就可以轻松地配对远程调用。</span><span class="sxs-lookup"><span data-stu-id="50d05-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="50d05-111">中`true`如果调用是异步的，则该值为; 否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="50d05-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50d05-112">要求</span><span class="sxs-lookup"><span data-stu-id="50d05-112">Requirements</span></span>  
 <span data-ttu-id="50d05-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50d05-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50d05-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50d05-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50d05-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50d05-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50d05-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50d05-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d05-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50d05-117">See also</span></span>

- [<span data-ttu-id="50d05-118">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="50d05-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
