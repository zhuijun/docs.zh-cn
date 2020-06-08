---
title: ICLRMetaHost::EnumerateLoadedRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504168"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="bb45e-102">ICLRMetaHost::EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="bb45e-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="bb45e-103">返回一个枚举，该枚举包含给定进程中加载的每个版本的公共语言运行时（CLR）的有效[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)接口指针。</span><span class="sxs-lookup"><span data-stu-id="bb45e-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="bb45e-104">此方法取代了[GetVersionFromProcess](getversionfromprocess-function.md)函数。</span><span class="sxs-lookup"><span data-stu-id="bb45e-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb45e-105">语法</span><span class="sxs-lookup"><span data-stu-id="bb45e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb45e-106">参数</span><span class="sxs-lookup"><span data-stu-id="bb45e-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="bb45e-107">中要检查加载的运行时的进程的句柄。</span><span class="sxs-lookup"><span data-stu-id="bb45e-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="bb45e-108">弄<xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>与进程加载的每个 CLR 相对应的[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)接口的枚举。</span><span class="sxs-lookup"><span data-stu-id="bb45e-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb45e-109">返回值</span><span class="sxs-lookup"><span data-stu-id="bb45e-109">Return Value</span></span>  
 <span data-ttu-id="bb45e-110">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="bb45e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bb45e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb45e-111">HRESULT</span></span>|<span data-ttu-id="bb45e-112">说明</span><span class="sxs-lookup"><span data-stu-id="bb45e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb45e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb45e-113">S_OK</span></span>|<span data-ttu-id="bb45e-114">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="bb45e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="bb45e-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bb45e-115">E_POINTER</span></span>|<span data-ttu-id="bb45e-116">`ppEnumerator` 为 null。</span><span class="sxs-lookup"><span data-stu-id="bb45e-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb45e-117">注解</span><span class="sxs-lookup"><span data-stu-id="bb45e-117">Remarks</span></span>  
 <span data-ttu-id="bb45e-118">此方法列出所有加载的运行时，即使它们是用弃用的函数（如[CorBindToRuntime](corbindtoruntime-function.md)）加载的。</span><span class="sxs-lookup"><span data-stu-id="bb45e-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb45e-119">要求</span><span class="sxs-lookup"><span data-stu-id="bb45e-119">Requirements</span></span>  
 <span data-ttu-id="bb45e-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb45e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb45e-121">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="bb45e-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bb45e-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="bb45e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb45e-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb45e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb45e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb45e-124">See also</span></span>

- [<span data-ttu-id="bb45e-125">ICLRMetaHost 接口</span><span class="sxs-lookup"><span data-stu-id="bb45e-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="bb45e-126">承载</span><span class="sxs-lookup"><span data-stu-id="bb45e-126">Hosting</span></span>](index.md)
