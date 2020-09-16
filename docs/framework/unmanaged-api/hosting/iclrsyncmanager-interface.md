---
title: ICLRSyncManager 接口
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: b0b9c0b7d178557806a9ab2893bff2d34dc408ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557731"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="6da59-102">ICLRSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="6da59-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="6da59-103">定义一些方法，这些方法允许宿主获取有关所请求任务的信息，并检测其同步实现中的死锁。</span><span class="sxs-lookup"><span data-stu-id="6da59-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6da59-104">方法</span><span class="sxs-lookup"><span data-stu-id="6da59-104">Methods</span></span>  
  
|<span data-ttu-id="6da59-105">方法</span><span class="sxs-lookup"><span data-stu-id="6da59-105">Method</span></span>|<span data-ttu-id="6da59-106">说明</span><span class="sxs-lookup"><span data-stu-id="6da59-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6da59-107">CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="6da59-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="6da59-108">请求公共语言运行时 (CLR) 为主机创建迭代器，以用于确定等待读取器-编写器锁的任务集。</span><span class="sxs-lookup"><span data-stu-id="6da59-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="6da59-109">DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="6da59-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="6da59-110">请求 CLR 销毁通过调用创建的迭代器 `CreateRWLockOwnerIterator` 。</span><span class="sxs-lookup"><span data-stu-id="6da59-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="6da59-111">GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="6da59-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="6da59-112">获取拥有指定监视器的任务。</span><span class="sxs-lookup"><span data-stu-id="6da59-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="6da59-113">GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="6da59-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="6da59-114">获取正在等待当前读取器-编写器锁的下一个任务。</span><span class="sxs-lookup"><span data-stu-id="6da59-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6da59-115">要求</span><span class="sxs-lookup"><span data-stu-id="6da59-115">Requirements</span></span>  
 <span data-ttu-id="6da59-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6da59-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6da59-117">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6da59-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6da59-118">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6da59-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6da59-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6da59-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6da59-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="6da59-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="6da59-121">IHostSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="6da59-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="6da59-122">[托管和非托管线程处理](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6da59-122">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="6da59-123">承载接口</span><span class="sxs-lookup"><span data-stu-id="6da59-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
