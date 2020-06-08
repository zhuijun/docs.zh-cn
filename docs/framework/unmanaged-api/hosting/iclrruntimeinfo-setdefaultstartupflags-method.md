---
title: ICLRRuntimeInfo::SetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504012"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="e3a85-102">ICLRRuntimeInfo::SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="e3a85-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="e3a85-103">设置启动标志和将用于启动运行时的主机配置文件。</span><span class="sxs-lookup"><span data-stu-id="e3a85-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="e3a85-104">此方法取代了 `startupFlags` [CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函数中的参数使用。</span><span class="sxs-lookup"><span data-stu-id="e3a85-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a85-105">语法</span><span class="sxs-lookup"><span data-stu-id="e3a85-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3a85-106">参数</span><span class="sxs-lookup"><span data-stu-id="e3a85-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="e3a85-107">中要设置的主机启动标志。</span><span class="sxs-lookup"><span data-stu-id="e3a85-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="e3a85-108">使用与[CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函数相同的标志。</span><span class="sxs-lookup"><span data-stu-id="e3a85-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="e3a85-109">中要设置的主机配置文件的目录路径。</span><span class="sxs-lookup"><span data-stu-id="e3a85-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3a85-110">返回值</span><span class="sxs-lookup"><span data-stu-id="e3a85-110">Return Value</span></span>  
 <span data-ttu-id="e3a85-111">此方法返回以下特定的 HRESULT 以及指示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="e3a85-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e3a85-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3a85-112">HRESULT</span></span>|<span data-ttu-id="e3a85-113">说明</span><span class="sxs-lookup"><span data-stu-id="e3a85-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3a85-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3a85-114">S_OK</span></span>|<span data-ttu-id="e3a85-115">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="e3a85-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3a85-116">注解</span><span class="sxs-lookup"><span data-stu-id="e3a85-116">Remarks</span></span>  
 <span data-ttu-id="e3a85-117">多线程主机应同步对此方法的调用。</span><span class="sxs-lookup"><span data-stu-id="e3a85-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="e3a85-118">否则，线程 A 可能会 `SetStartupFlags` 在线程 b 完成对的调用 `SetStartupFlags` 和线程 b 启动运行时之前调用方法。</span><span class="sxs-lookup"><span data-stu-id="e3a85-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a85-119">要求</span><span class="sxs-lookup"><span data-stu-id="e3a85-119">Requirements</span></span>  
 <span data-ttu-id="e3a85-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3a85-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a85-121">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="e3a85-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e3a85-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="e3a85-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3a85-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a85-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a85-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3a85-124">See also</span></span>

- [<span data-ttu-id="e3a85-125">ICLRRuntimeInfo 接口</span><span class="sxs-lookup"><span data-stu-id="e3a85-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e3a85-126">承载接口</span><span class="sxs-lookup"><span data-stu-id="e3a85-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e3a85-127">承载</span><span class="sxs-lookup"><span data-stu-id="e3a85-127">Hosting</span></span>](index.md)
