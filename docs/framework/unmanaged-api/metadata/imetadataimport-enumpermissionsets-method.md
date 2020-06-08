---
title: IMetaDataImport::EnumPermissionSets 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: 79b1493d262288c1d85a56538810e35a73441595
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491746"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="401e0-102">IMetaDataImport::EnumPermissionSets 方法</span><span class="sxs-lookup"><span data-stu-id="401e0-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="401e0-103">枚举指定的元数据范围内的对象的权限。</span><span class="sxs-lookup"><span data-stu-id="401e0-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401e0-104">语法</span><span class="sxs-lookup"><span data-stu-id="401e0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="401e0-105">参数</span><span class="sxs-lookup"><span data-stu-id="401e0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="401e0-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="401e0-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="401e0-107">第一次调用此方法时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="401e0-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="401e0-108">中一个元数据令牌，用于限制搜索范围，或为 NULL 以搜索尽可能大的范围。</span><span class="sxs-lookup"><span data-stu-id="401e0-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="401e0-109">中表示 <xref:System.Security.Permissions.SecurityAction> 要包含在中的值的标志 `rPermission` ，若要返回所有操作，则为零。</span><span class="sxs-lookup"><span data-stu-id="401e0-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="401e0-110">弄用于存储权限令牌的数组。</span><span class="sxs-lookup"><span data-stu-id="401e0-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="401e0-111">[in] `rPermission` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="401e0-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="401e0-112">弄中返回的权限令牌数 `rPermission` 。</span><span class="sxs-lookup"><span data-stu-id="401e0-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="401e0-113">返回值</span><span class="sxs-lookup"><span data-stu-id="401e0-113">Return Value</span></span>  
  
|<span data-ttu-id="401e0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="401e0-114">HRESULT</span></span>|<span data-ttu-id="401e0-115">说明</span><span class="sxs-lookup"><span data-stu-id="401e0-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="401e0-116">`EnumPermissionSets`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="401e0-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="401e0-117">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="401e0-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="401e0-118">在这种情况下， `pcTokens` 为零。</span><span class="sxs-lookup"><span data-stu-id="401e0-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="401e0-119">要求</span><span class="sxs-lookup"><span data-stu-id="401e0-119">Requirements</span></span>  
 <span data-ttu-id="401e0-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="401e0-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401e0-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="401e0-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="401e0-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="401e0-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="401e0-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401e0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401e0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="401e0-124">See also</span></span>

- [<span data-ttu-id="401e0-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="401e0-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="401e0-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="401e0-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
