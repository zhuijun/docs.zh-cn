---
title: IHostAssemblyStore::ProvideAssembly 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
ms.openlocfilehash: 162def0d703ea81efc3df3ea5ee08b58e34822e6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501568"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="e11ef-102">IHostAssemblyStore::ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="e11ef-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="e11ef-103">获取对程序集的引用，该程序集未由从[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)返回的[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)引用。</span><span class="sxs-lookup"><span data-stu-id="e11ef-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="e11ef-104">公共语言运行时（CLR）对不 `ProvideAssembly` 显示在列表中的每个程序集都进行调用。</span><span class="sxs-lookup"><span data-stu-id="e11ef-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e11ef-105">语法</span><span class="sxs-lookup"><span data-stu-id="e11ef-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e11ef-106">参数</span><span class="sxs-lookup"><span data-stu-id="e11ef-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="e11ef-107">中指向[AssemblyBindInfo](assemblybindinfo-structure.md)实例的指针，主机使用该实例来确定特定的绑定特征，包括是否存在任何版本控制策略以及要绑定到的程序集。</span><span class="sxs-lookup"><span data-stu-id="e11ef-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="e11ef-108">弄指向此的请求程序集的唯一标识符的指针 `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="e11ef-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="e11ef-109">弄指向特定于主机的数据的指针，用于在不需要平台调用的情况下确定请求的程序集的证据。</span><span class="sxs-lookup"><span data-stu-id="e11ef-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="e11ef-110">`pHostContext`对应于 <xref:System.Reflection.Assembly.HostContext%2A> 托管类的属性 <xref:System.Reflection.Assembly> 。</span><span class="sxs-lookup"><span data-stu-id="e11ef-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="e11ef-111">弄指向 `IStream` 包含要加载的可移植可执行（PE）映像的地址的指针; 如果找不到该程序集，则为 null。</span><span class="sxs-lookup"><span data-stu-id="e11ef-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="e11ef-112">弄指向 `IStream` 包含程序调试（PDB）信息的地址的指针; 如果找不到 .pdb 文件，则为 null。</span><span class="sxs-lookup"><span data-stu-id="e11ef-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e11ef-113">返回值</span><span class="sxs-lookup"><span data-stu-id="e11ef-113">Return Value</span></span>  
  
|<span data-ttu-id="e11ef-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e11ef-114">HRESULT</span></span>|<span data-ttu-id="e11ef-115">说明</span><span class="sxs-lookup"><span data-stu-id="e11ef-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e11ef-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e11ef-116">S_OK</span></span>|<span data-ttu-id="e11ef-117">`ProvideAssembly`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="e11ef-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="e11ef-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e11ef-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e11ef-119">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="e11ef-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e11ef-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e11ef-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e11ef-121">调用超时。</span><span class="sxs-lookup"><span data-stu-id="e11ef-121">The call timed out.</span></span>|  
|<span data-ttu-id="e11ef-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e11ef-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e11ef-123">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="e11ef-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e11ef-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e11ef-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e11ef-125">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="e11ef-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e11ef-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e11ef-126">E_FAIL</span></span>|<span data-ttu-id="e11ef-127">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="e11ef-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e11ef-128">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="e11ef-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e11ef-129">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e11ef-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e11ef-130">COR_E_FILENOTFOUND （0x80070002）</span><span class="sxs-lookup"><span data-stu-id="e11ef-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="e11ef-131">找不到请求的程序集。</span><span class="sxs-lookup"><span data-stu-id="e11ef-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="e11ef-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e11ef-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e11ef-133">指定的缓冲区大小 `pAssemblyId` 不够大，无法容纳主机需要返回的标识符。</span><span class="sxs-lookup"><span data-stu-id="e11ef-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e11ef-134">注解</span><span class="sxs-lookup"><span data-stu-id="e11ef-134">Remarks</span></span>  
 <span data-ttu-id="e11ef-135">为返回的标识值 `pAssemblyId` 由主机指定。</span><span class="sxs-lookup"><span data-stu-id="e11ef-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="e11ef-136">标识符在进程的生存期内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e11ef-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="e11ef-137">CLR 使用此值作为流的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="e11ef-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="e11ef-138">它会对照的值检查每个值，以使其他对的 `pAssemblyId` 调用返回 `ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="e11ef-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="e11ef-139">如果主机为其他主机返回相同的 `pAssemblyId` 值 `IStream` ，则 CLR 将检查是否已映射该流的内容。</span><span class="sxs-lookup"><span data-stu-id="e11ef-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="e11ef-140">如果是这样，则运行时加载映像的现有副本，而不是映射一个新副本。</span><span class="sxs-lookup"><span data-stu-id="e11ef-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e11ef-141">要求</span><span class="sxs-lookup"><span data-stu-id="e11ef-141">Requirements</span></span>  
 <span data-ttu-id="e11ef-142">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e11ef-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e11ef-143">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e11ef-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e11ef-144">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="e11ef-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e11ef-145">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e11ef-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e11ef-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e11ef-146">See also</span></span>

- [<span data-ttu-id="e11ef-147">ICLRAssemblyReferenceList 接口</span><span class="sxs-lookup"><span data-stu-id="e11ef-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e11ef-148">IHostAssemblyManager 接口</span><span class="sxs-lookup"><span data-stu-id="e11ef-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="e11ef-149">IHostAssemblyStore 接口</span><span class="sxs-lookup"><span data-stu-id="e11ef-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
