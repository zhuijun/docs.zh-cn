---
title: IMetaDataImport::EnumSignatures 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 652ebf1be6a58e08da27aaed5b2e84a8f2aee98a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503765"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="3e8db-102">IMetaDataImport::EnumSignatures 方法</span><span class="sxs-lookup"><span data-stu-id="3e8db-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="3e8db-103">枚举当前范围内表示独立签名的 Signature 标记。</span><span class="sxs-lookup"><span data-stu-id="3e8db-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8db-104">语法</span><span class="sxs-lookup"><span data-stu-id="3e8db-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e8db-105">参数</span><span class="sxs-lookup"><span data-stu-id="3e8db-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3e8db-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="3e8db-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3e8db-107">第一次调用此方法时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="3e8db-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="3e8db-108">弄用于存储签名令牌的数组。</span><span class="sxs-lookup"><span data-stu-id="3e8db-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3e8db-109">[in] `rSignatures` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="3e8db-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="3e8db-110">弄中返回的签名令牌数 `rSignatures` 。</span><span class="sxs-lookup"><span data-stu-id="3e8db-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e8db-111">返回值</span><span class="sxs-lookup"><span data-stu-id="3e8db-111">Return Value</span></span>  
  
|<span data-ttu-id="3e8db-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e8db-112">HRESULT</span></span>|<span data-ttu-id="3e8db-113">说明</span><span class="sxs-lookup"><span data-stu-id="3e8db-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3e8db-114">`EnumSignatures`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="3e8db-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3e8db-115">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="3e8db-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3e8db-116">在这种情况下， `pcSignatures` 为零。</span><span class="sxs-lookup"><span data-stu-id="3e8db-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e8db-117">注解</span><span class="sxs-lookup"><span data-stu-id="3e8db-117">Remarks</span></span>  
 <span data-ttu-id="3e8db-118">签名令牌由[IMetaDataEmit：： GetTokenFromSig](imetadataemit-gettokenfromsig-method.md)方法创建。</span><span class="sxs-lookup"><span data-stu-id="3e8db-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e8db-119">要求</span><span class="sxs-lookup"><span data-stu-id="3e8db-119">Requirements</span></span>  
 <span data-ttu-id="3e8db-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e8db-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e8db-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="3e8db-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e8db-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="3e8db-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e8db-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e8db-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8db-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e8db-124">See also</span></span>

- [<span data-ttu-id="3e8db-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="3e8db-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3e8db-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="3e8db-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
