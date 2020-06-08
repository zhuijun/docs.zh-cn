---
title: ICLRStrongName::StrongNameSignatureVerificationEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: 5bd985a6870ae6f4cc2302b6a11e8e139180d839
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503986"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="78280-102">ICLRStrongName::StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="78280-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="78280-103">获取一个值，该值指示所提供的路径处的程序集清单是否包含强名称签名。</span><span class="sxs-lookup"><span data-stu-id="78280-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78280-104">语法</span><span class="sxs-lookup"><span data-stu-id="78280-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78280-105">参数</span><span class="sxs-lookup"><span data-stu-id="78280-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="78280-106">中要验证的程序集的可移植可执行文件（.exe 或 .dll）文件的路径。</span><span class="sxs-lookup"><span data-stu-id="78280-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="78280-107">[in] `true`若要执行验证，即使需要重写注册表设置，否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="78280-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="78280-108">[out] `true`如果验证了强名称签名，则为;否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="78280-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="78280-109">`pfWasVerified``false`如果验证因为注册表设置而成功，则也会设置为。</span><span class="sxs-lookup"><span data-stu-id="78280-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78280-110">返回值</span><span class="sxs-lookup"><span data-stu-id="78280-110">Return Value</span></span>  
 <span data-ttu-id="78280-111">`S_OK`如果验证成功，则为;否则，表示失败的 HRESULT 值（请参阅列表的[常见 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="78280-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78280-112">注解</span><span class="sxs-lookup"><span data-stu-id="78280-112">Remarks</span></span>  
 <span data-ttu-id="78280-113">[ICLRStrongName：： StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md)方法提供类似于[ICLRStrongName：： StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md)方法的功能。</span><span class="sxs-lookup"><span data-stu-id="78280-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="78280-114">但是， [ICLRStrongName：： StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md)的第二个输入参数和输出参数的类型为， `BOOLEAN` 而不是 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="78280-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78280-115">要求</span><span class="sxs-lookup"><span data-stu-id="78280-115">Requirements</span></span>  
 <span data-ttu-id="78280-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78280-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78280-117">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="78280-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="78280-118">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="78280-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78280-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78280-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78280-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78280-120">See also</span></span>

- [<span data-ttu-id="78280-121">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="78280-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="78280-122">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="78280-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
