---
title: ICorRuntimeHost::CreateEvidence 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 264f16fc9e767584229376e67f5aee6db1069025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501607"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="fdec3-102">ICorRuntimeHost::CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="fdec3-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="fdec3-103">获取类型的接口指针 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> ，该指针允许主机创建要传递给[CreateDomain](icorruntimehost-createdomain-method.md)或[CreateDomainEx](icorruntimehost-createdomainex-method.md)方法的安全证据。</span><span class="sxs-lookup"><span data-stu-id="fdec3-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdec3-104">语法</span><span class="sxs-lookup"><span data-stu-id="fdec3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdec3-105">参数</span><span class="sxs-lookup"><span data-stu-id="fdec3-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="fdec3-106">弄一个接口指针，指向 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 用于创建安全证据的实例。</span><span class="sxs-lookup"><span data-stu-id="fdec3-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="fdec3-107">此指针的类型为 `IUnknown` ，因此调用方通常应 `QueryInterface` 在此接口上调用以获取指向的指针 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="fdec3-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdec3-108">返回值</span><span class="sxs-lookup"><span data-stu-id="fdec3-108">Return Value</span></span>  
  
|<span data-ttu-id="fdec3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdec3-109">HRESULT</span></span>|<span data-ttu-id="fdec3-110">说明</span><span class="sxs-lookup"><span data-stu-id="fdec3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdec3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdec3-111">S_OK</span></span>|<span data-ttu-id="fdec3-112">操作成功。</span><span class="sxs-lookup"><span data-stu-id="fdec3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="fdec3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fdec3-113">S_FALSE</span></span>|<span data-ttu-id="fdec3-114">操作未能完成。</span><span class="sxs-lookup"><span data-stu-id="fdec3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="fdec3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdec3-115">E_FAIL</span></span>|<span data-ttu-id="fdec3-116">发生了未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="fdec3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fdec3-117">如果方法返回 E_FAIL，则公共语言运行时（CLR）在该过程中将不再可用。</span><span class="sxs-lookup"><span data-stu-id="fdec3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="fdec3-118">对任何宿主 Api 的后续调用都会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fdec3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fdec3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdec3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdec3-120">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="fdec3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdec3-121">注解</span><span class="sxs-lookup"><span data-stu-id="fdec3-121">Remarks</span></span>  
 <span data-ttu-id="fdec3-122">此方法返回一个不能从本机代码中填充的空集合。</span><span class="sxs-lookup"><span data-stu-id="fdec3-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="fdec3-123">应 <xref:System.Security.Policy.Evidence> 改用方法。</span><span class="sxs-lookup"><span data-stu-id="fdec3-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdec3-124">要求</span><span class="sxs-lookup"><span data-stu-id="fdec3-124">Requirements</span></span>  
 <span data-ttu-id="fdec3-125">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdec3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdec3-126">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fdec3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdec3-127">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="fdec3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdec3-128">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="fdec3-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdec3-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdec3-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="fdec3-130">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="fdec3-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
