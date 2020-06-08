---
title: ICorDebugManagedCallback2::CreateConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501919"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="31d8d-102">ICorDebugManagedCallback2::CreateConnection 方法</span><span class="sxs-lookup"><span data-stu-id="31d8d-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="31d8d-103">通知调试器已创建新连接。</span><span class="sxs-lookup"><span data-stu-id="31d8d-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d8d-104">语法</span><span class="sxs-lookup"><span data-stu-id="31d8d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31d8d-105">参数</span><span class="sxs-lookup"><span data-stu-id="31d8d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="31d8d-106">中一个指向 "ICorDebugProcess" 对象的指针，该对象表示在其中创建连接的进程</span><span class="sxs-lookup"><span data-stu-id="31d8d-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="31d8d-107">中新连接的 ID。</span><span class="sxs-lookup"><span data-stu-id="31d8d-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="31d8d-108">中指向新连接名称的指针。</span><span class="sxs-lookup"><span data-stu-id="31d8d-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d8d-109">注解</span><span class="sxs-lookup"><span data-stu-id="31d8d-109">Remarks</span></span>  
 <span data-ttu-id="31d8d-110">`CreateConnection`在以下任一情况下，都将激发回调：</span><span class="sxs-lookup"><span data-stu-id="31d8d-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="31d8d-111">调试器附加到包含连接的进程时。</span><span class="sxs-lookup"><span data-stu-id="31d8d-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="31d8d-112">在这种情况下，运行时将 `CreateConnection` 为进程中的每个连接生成并调度一个事件和一个[ICorDebugManagedCallback2：： ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md)事件。</span><span class="sxs-lookup"><span data-stu-id="31d8d-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="31d8d-113">当主机在[托管 API](../hosting/index.md)中调用[ICLRDebugManager：： BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md)时。</span><span class="sxs-lookup"><span data-stu-id="31d8d-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d8d-114">要求</span><span class="sxs-lookup"><span data-stu-id="31d8d-114">Requirements</span></span>  
 <span data-ttu-id="31d8d-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31d8d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d8d-116">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31d8d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31d8d-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31d8d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31d8d-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d8d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d8d-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31d8d-119">See also</span></span>

- [<span data-ttu-id="31d8d-120">ICorDebugManagedCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="31d8d-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="31d8d-121">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="31d8d-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
