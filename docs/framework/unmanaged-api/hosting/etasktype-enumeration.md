---
title: ETaskType 枚举
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 0fa72568df77c4916a3c6676e1dcca7c0c616c4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493313"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="8ba09-102">ETaskType 枚举</span><span class="sxs-lookup"><span data-stu-id="8ba09-102">ETaskType Enumeration</span></span>
<span data-ttu-id="8ba09-103">包含一些值，这些值指示由[ICLRTask](iclrtask-interface.md)或[IHostTask](ihosttask-interface.md)接口表示的任务的类型。</span><span class="sxs-lookup"><span data-stu-id="8ba09-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ba09-104">语法</span><span class="sxs-lookup"><span data-stu-id="8ba09-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="8ba09-105">成员</span><span class="sxs-lookup"><span data-stu-id="8ba09-105">Members</span></span>  
  
|<span data-ttu-id="8ba09-106">成员</span><span class="sxs-lookup"><span data-stu-id="8ba09-106">Member</span></span>|<span data-ttu-id="8ba09-107">描述</span><span class="sxs-lookup"><span data-stu-id="8ba09-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="8ba09-108">接口表示应用程序域卸载任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="8ba09-109">接口表示调试器帮助器任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="8ba09-110">接口表示终结器任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="8ba09-111">接口表示垃圾回收任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="8ba09-112">接口表示一个 "入口线程" 任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="8ba09-113">接口表示 i/o 线程任务或完成端口线程任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="8ba09-114">接口表示计时器线程任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="8ba09-115">接口表示等待线程任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="8ba09-116">接口表示工作线程任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="8ba09-117">任务未知。</span><span class="sxs-lookup"><span data-stu-id="8ba09-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="8ba09-118">接口表示用户任务。</span><span class="sxs-lookup"><span data-stu-id="8ba09-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ba09-119">要求</span><span class="sxs-lookup"><span data-stu-id="8ba09-119">Requirements</span></span>  
 <span data-ttu-id="8ba09-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba09-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ba09-121">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8ba09-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ba09-122">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8ba09-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ba09-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ba09-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba09-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ba09-124">See also</span></span>

- [<span data-ttu-id="8ba09-125">承载枚举</span><span class="sxs-lookup"><span data-stu-id="8ba09-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
