---
title: IHostAssemblyManager::GetNonHostStoreAssemblies 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: 9a1440be7011130b16d7112ae15026eb74856190
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501583"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="aef80-102">IHostAssemblyManager::GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="aef80-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="aef80-103">获取一个指向[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)的接口指针，该指针表示宿主需要公共语言运行时（CLR）加载的程序集的列表。</span><span class="sxs-lookup"><span data-stu-id="aef80-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef80-104">语法</span><span class="sxs-lookup"><span data-stu-id="aef80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef80-105">参数</span><span class="sxs-lookup"><span data-stu-id="aef80-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="aef80-106">弄指向的地址的指针 `ICLRAssemblyReferenceList` ，该地址包含对宿主预期 CLR 加载的程序集的引用的列表。</span><span class="sxs-lookup"><span data-stu-id="aef80-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aef80-107">返回值</span><span class="sxs-lookup"><span data-stu-id="aef80-107">Return Value</span></span>  
  
|<span data-ttu-id="aef80-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aef80-108">HRESULT</span></span>|<span data-ttu-id="aef80-109">说明</span><span class="sxs-lookup"><span data-stu-id="aef80-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aef80-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aef80-110">S_OK</span></span>|<span data-ttu-id="aef80-111">`GetNonHostStoreAssemblies`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="aef80-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="aef80-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aef80-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aef80-113">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="aef80-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aef80-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aef80-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aef80-115">调用超时。</span><span class="sxs-lookup"><span data-stu-id="aef80-115">The call timed out.</span></span>|  
|<span data-ttu-id="aef80-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aef80-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aef80-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="aef80-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aef80-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aef80-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aef80-119">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="aef80-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aef80-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aef80-120">E_FAIL</span></span>|<span data-ttu-id="aef80-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="aef80-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aef80-122">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="aef80-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aef80-123">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="aef80-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aef80-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aef80-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aef80-125">没有足够的内存可用于创建请求的引用列表 `ICLRAssemblyReferenceList` 。</span><span class="sxs-lookup"><span data-stu-id="aef80-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aef80-126">注解</span><span class="sxs-lookup"><span data-stu-id="aef80-126">Remarks</span></span>  
 <span data-ttu-id="aef80-127">CLR 使用以下一组准则来解析引用：</span><span class="sxs-lookup"><span data-stu-id="aef80-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="aef80-128">首先，它会咨询返回的程序集引用的列表 `GetNonHostStoreAssemblies` 。</span><span class="sxs-lookup"><span data-stu-id="aef80-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="aef80-129">如果该程序集出现在列表中，则 CLR 正常绑定到该程序集。</span><span class="sxs-lookup"><span data-stu-id="aef80-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="aef80-130">如果程序集未出现在列表中，并且宿主已提供[IHostAssemblyStore](ihostassemblystore-interface.md)的实现，则 CLR 将调用[IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md) ，以允许主机提供要绑定到的程序集。</span><span class="sxs-lookup"><span data-stu-id="aef80-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="aef80-131">否则，CLR 无法绑定到程序集。</span><span class="sxs-lookup"><span data-stu-id="aef80-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="aef80-132">如果主机设置 `ppReferenceList` 为 null，则 CLR 首先探测全局程序集缓存，调用 `ProvideAssembly` ，然后探测应用程序基以解析程序集引用。</span><span class="sxs-lookup"><span data-stu-id="aef80-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aef80-133">初始化后，CLR 只调用 `GetNonHostStoreAssemblies` 一次。</span><span class="sxs-lookup"><span data-stu-id="aef80-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="aef80-134">不会再次调用方法。</span><span class="sxs-lookup"><span data-stu-id="aef80-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef80-135">要求</span><span class="sxs-lookup"><span data-stu-id="aef80-135">Requirements</span></span>  
 <span data-ttu-id="aef80-136">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aef80-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef80-137">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="aef80-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aef80-138">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="aef80-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aef80-139">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef80-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef80-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aef80-140">See also</span></span>

- [<span data-ttu-id="aef80-141">ICLRAssemblyReferenceList 接口</span><span class="sxs-lookup"><span data-stu-id="aef80-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="aef80-142">IHostAssemblyManager 接口</span><span class="sxs-lookup"><span data-stu-id="aef80-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="aef80-143">IHostAssemblyStore 接口</span><span class="sxs-lookup"><span data-stu-id="aef80-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
