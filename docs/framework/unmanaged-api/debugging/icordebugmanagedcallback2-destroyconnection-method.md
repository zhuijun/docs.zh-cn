---
title: ICorDebugManagedCallback2::DestroyConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: a3093f33f2220b22b7b4b373f6d79a341abf8c9c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501932"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="8d6f4-102">ICorDebugManagedCallback2::DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="8d6f4-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="8d6f4-103">通知调试器指定的连接已终止。</span><span class="sxs-lookup"><span data-stu-id="8d6f4-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d6f4-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d6f4-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d6f4-105">参数</span><span class="sxs-lookup"><span data-stu-id="8d6f4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8d6f4-106">中指向 ICorDebugProcess 对象的指针，该对象表示包含已销毁的连接的进程。</span><span class="sxs-lookup"><span data-stu-id="8d6f4-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="8d6f4-107">中已销毁的连接的 ID。</span><span class="sxs-lookup"><span data-stu-id="8d6f4-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d6f4-108">注解</span><span class="sxs-lookup"><span data-stu-id="8d6f4-108">Remarks</span></span>  
 <span data-ttu-id="8d6f4-109">`DestroyConnection`当主机在[宿主 API](../hosting/index.md)中调用[ICLRDebugManager：： EndConnection](../hosting/iclrdebugmanager-endconnection-method.md)时，将触发回调。</span><span class="sxs-lookup"><span data-stu-id="8d6f4-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d6f4-110">要求</span><span class="sxs-lookup"><span data-stu-id="8d6f4-110">Requirements</span></span>  
 <span data-ttu-id="8d6f4-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d6f4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d6f4-112">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d6f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d6f4-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d6f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d6f4-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d6f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6f4-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d6f4-115">See also</span></span>

- [<span data-ttu-id="8d6f4-116">ICorDebugManagedCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="8d6f4-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="8d6f4-117">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="8d6f4-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
