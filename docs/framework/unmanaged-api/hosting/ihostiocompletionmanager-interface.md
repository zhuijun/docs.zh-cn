---
title: IHostIoCompletionManager 接口
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 095872f8d4bd4f7d3351b8b3e3f8f8445b615cd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501529"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="c7b59-102">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="c7b59-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="c7b59-103">提供允许公共语言运行时（CLR）与主机提供的 i/o 完成端口进行交互的方法。</span><span class="sxs-lookup"><span data-stu-id="c7b59-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7b59-104">方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-104">Methods</span></span>  
  
|<span data-ttu-id="c7b59-105">方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-105">Method</span></span>|<span data-ttu-id="c7b59-106">说明</span><span class="sxs-lookup"><span data-stu-id="c7b59-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7b59-107">Bind 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-107">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="c7b59-108">将句柄绑定到 i/o 完成端口。</span><span class="sxs-lookup"><span data-stu-id="c7b59-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="c7b59-109">CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-109">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="c7b59-110">关闭通过先前对的调用创建的端口 `CreateIoCompletionPort` 。</span><span class="sxs-lookup"><span data-stu-id="c7b59-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="c7b59-111">CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-111">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="c7b59-112">请求宿主创建新的 i/o 完成端口。</span><span class="sxs-lookup"><span data-stu-id="c7b59-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="c7b59-113">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-113">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="c7b59-114">获取当前未处理请求的 i/o 完成线程数。</span><span class="sxs-lookup"><span data-stu-id="c7b59-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="c7b59-115">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-115">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="c7b59-116">获取宿主打算追加到 i/o 请求的任何自定义数据的大小。</span><span class="sxs-lookup"><span data-stu-id="c7b59-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="c7b59-117">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-117">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="c7b59-118">获取主机可为服务 i/o 请求分配的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="c7b59-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="c7b59-119">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-119">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="c7b59-120">获取主机提供的用于处理 i/o 请求的最小线程数。</span><span class="sxs-lookup"><span data-stu-id="c7b59-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="c7b59-121">InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-121">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="c7b59-122">向宿主提供初始化有关 i/o 请求的任何自定义数据的机会。</span><span class="sxs-lookup"><span data-stu-id="c7b59-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="c7b59-123">SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-123">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="c7b59-124">向宿主提供一个接口指针，该指针指向 CLR 实现的[ICLRIoCompletionManager](iclriocompletionmanager-interface.md)实例。</span><span class="sxs-lookup"><span data-stu-id="c7b59-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="c7b59-125">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-125">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="c7b59-126">设置主机 allots i/o 请求的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="c7b59-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="c7b59-127">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c7b59-127">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="c7b59-128">设置主机应为 i/o 完成分配的最小线程数。</span><span class="sxs-lookup"><span data-stu-id="c7b59-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b59-129">注解</span><span class="sxs-lookup"><span data-stu-id="c7b59-129">Remarks</span></span>  
 <span data-ttu-id="c7b59-130">`IHostIoCompletionManager`对应于 `ICLRIoCompletionManager` CLR 实现的接口。</span><span class="sxs-lookup"><span data-stu-id="c7b59-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="c7b59-131">CLR 调用的方法将 `IHostIoCompletionManager` 句柄绑定到主机提供的端口，并且宿主将调用的方法 `ICLRIoCompletionManager` 来报告 i/o 请求的完成。</span><span class="sxs-lookup"><span data-stu-id="c7b59-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b59-132">要求</span><span class="sxs-lookup"><span data-stu-id="c7b59-132">Requirements</span></span>  
 <span data-ttu-id="c7b59-133">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7b59-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b59-134">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c7b59-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7b59-135">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="c7b59-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7b59-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b59-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b59-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7b59-137">See also</span></span>

- [<span data-ttu-id="c7b59-138">承载接口</span><span class="sxs-lookup"><span data-stu-id="c7b59-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
