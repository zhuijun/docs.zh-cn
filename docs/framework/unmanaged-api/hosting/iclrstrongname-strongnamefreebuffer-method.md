---
title: ICLRStrongName::StrongNameFreeBuffer 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503999"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="ef809-102">ICLRStrongName::StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="ef809-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="ef809-103">释放先前调用强名称方法（如[ICLRStrongName：： StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)、 [ICLRStrongName：： StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)或[ICLRStrongName：： StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)）时分配的内存。</span><span class="sxs-lookup"><span data-stu-id="ef809-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef809-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef809-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef809-105">参数</span><span class="sxs-lookup"><span data-stu-id="ef809-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="ef809-106">中指向要释放的内存的指针。</span><span class="sxs-lookup"><span data-stu-id="ef809-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef809-107">返回值</span><span class="sxs-lookup"><span data-stu-id="ef809-107">Return Value</span></span>  
 <span data-ttu-id="ef809-108">`S_OK`如果该方法已成功完成，则为;否则，表示失败的 HRESULT 值（请参阅列表的[常见 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="ef809-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef809-109">要求</span><span class="sxs-lookup"><span data-stu-id="ef809-109">Requirements</span></span>  
 <span data-ttu-id="ef809-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef809-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef809-111">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="ef809-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ef809-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="ef809-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef809-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef809-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef809-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef809-114">See also</span></span>

- [<span data-ttu-id="ef809-115">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="ef809-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
