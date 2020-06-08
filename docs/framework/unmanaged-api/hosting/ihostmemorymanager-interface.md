---
title: IHostMemoryManager 接口
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: 09b4a06892cdc450eed9dead503a990b6f19804e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501503"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="dec6b-102">IHostMemoryManager 接口</span><span class="sxs-lookup"><span data-stu-id="dec6b-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="dec6b-103">提供一些方法，这些方法允许公共语言运行时（CLR）通过主机进行虚拟内存请求，而不是使用标准 Win32 虚拟内存函数。</span><span class="sxs-lookup"><span data-stu-id="dec6b-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dec6b-104">方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-104">Methods</span></span>  
  
|<span data-ttu-id="dec6b-105">方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-105">Method</span></span>|<span data-ttu-id="dec6b-106">说明</span><span class="sxs-lookup"><span data-stu-id="dec6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dec6b-107">AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="dec6b-108">向宿主通知公共语言运行时（CLR）已从操作系统中获取指定内存。</span><span class="sxs-lookup"><span data-stu-id="dec6b-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="dec6b-109">CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-109">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="dec6b-110">获取一个接口指针，该指针指向用于从主机创建的堆请求内存分配的[IHostMAlloc](ihostmalloc-interface.md)实例。</span><span class="sxs-lookup"><span data-stu-id="dec6b-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="dec6b-111">GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="dec6b-112">获取主机报告的当前正使用的物理内存量。</span><span class="sxs-lookup"><span data-stu-id="dec6b-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="dec6b-113">NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="dec6b-114">向宿主通知 CLR 将尝试使用指定的内存。</span><span class="sxs-lookup"><span data-stu-id="dec6b-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="dec6b-115">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="dec6b-116">注册一个指针，该指针指向主机调用以通知 CLR 当前计算机上的当前内存负载的回调函数。</span><span class="sxs-lookup"><span data-stu-id="dec6b-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="dec6b-117">ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="dec6b-118">向宿主通知 CLR 已使用指定的内存完成。</span><span class="sxs-lookup"><span data-stu-id="dec6b-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="dec6b-119">VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="dec6b-120">用作相应 Win32 函数的逻辑包装，该函数可在调用进程的虚拟地址空间中保留或提交页区域。</span><span class="sxs-lookup"><span data-stu-id="dec6b-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="dec6b-121">VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="dec6b-122">用作相应 Win32 函数的逻辑包装，该函数释放、解除或释放和解除调用进程的虚拟地址空间中的页面区域。</span><span class="sxs-lookup"><span data-stu-id="dec6b-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="dec6b-123">VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="dec6b-124">用作相应 Win32 函数的逻辑包装，该函数更改调用进程的虚拟地址空间中已提交页面区域的保护。</span><span class="sxs-lookup"><span data-stu-id="dec6b-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="dec6b-125">VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="dec6b-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="dec6b-126">用作相应 Win32 函数的逻辑包装，它检索有关调用进程的虚拟地址空间中的一系列页面的信息。</span><span class="sxs-lookup"><span data-stu-id="dec6b-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dec6b-127">注解</span><span class="sxs-lookup"><span data-stu-id="dec6b-127">Remarks</span></span>  
 <span data-ttu-id="dec6b-128">`IHostMemoryManager`还为 CLR 提供一些方法，用于获取一个指针，通过该指针可以在堆上发出内存请求并在进程中获取由主机报告的内存压力级别。</span><span class="sxs-lookup"><span data-stu-id="dec6b-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dec6b-129">要求</span><span class="sxs-lookup"><span data-stu-id="dec6b-129">Requirements</span></span>  
 <span data-ttu-id="dec6b-130">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dec6b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dec6b-131">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dec6b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dec6b-132">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="dec6b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dec6b-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dec6b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec6b-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dec6b-134">See also</span></span>

- [<span data-ttu-id="dec6b-135">IHostMalloc 接口</span><span class="sxs-lookup"><span data-stu-id="dec6b-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="dec6b-136">承载接口</span><span class="sxs-lookup"><span data-stu-id="dec6b-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
