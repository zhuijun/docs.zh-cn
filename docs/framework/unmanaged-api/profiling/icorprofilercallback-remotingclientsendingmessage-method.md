---
title: ICorProfilerCallback::RemotingClientSendingMessage 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: 820a37c8ca16f4962bf1d72b1f0f404cffd92a1a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499956"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="2a134-102">ICorProfilerCallback::RemotingClientSendingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="2a134-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="2a134-103">通知探查器客户端正在向服务器发送请求。</span><span class="sxs-lookup"><span data-stu-id="2a134-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a134-104">语法</span><span class="sxs-lookup"><span data-stu-id="2a134-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a134-105">参数</span><span class="sxs-lookup"><span data-stu-id="2a134-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="2a134-106">中与以下条件下的[ICorProfilerCallback：： RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md)中提供的值对应的值：</span><span class="sxs-lookup"><span data-stu-id="2a134-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="2a134-107">远程处理 GUID cookie 处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="2a134-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="2a134-108">通道成功传输消息。</span><span class="sxs-lookup"><span data-stu-id="2a134-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="2a134-109">GUID cookie 在服务器端进程中处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="2a134-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="2a134-110">这样就可以轻松地配对远程调用和逻辑调用堆栈的创建。</span><span class="sxs-lookup"><span data-stu-id="2a134-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="2a134-111">中`true`如果调用是异步的，则该值为; 否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="2a134-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a134-112">要求</span><span class="sxs-lookup"><span data-stu-id="2a134-112">Requirements</span></span>  
 <span data-ttu-id="2a134-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a134-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a134-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a134-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a134-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a134-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a134-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a134-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a134-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a134-117">See also</span></span>

- [<span data-ttu-id="2a134-118">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="2a134-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
