---
title: IMetaDataImport::EnumModuleRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: fe7350e6d8e400ae37b5b8b7854a56f3c5c53ea7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491738"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="4f38d-102">IMetaDataImport::EnumModuleRefs 方法</span><span class="sxs-lookup"><span data-stu-id="4f38d-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="4f38d-103">枚举表示导入的模块的 ModuleRef 标记。</span><span class="sxs-lookup"><span data-stu-id="4f38d-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f38d-104">语法</span><span class="sxs-lookup"><span data-stu-id="4f38d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f38d-105">参数</span><span class="sxs-lookup"><span data-stu-id="4f38d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4f38d-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="4f38d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4f38d-107">第一次调用此方法时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="4f38d-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="4f38d-108">弄用于存储 ModuleRef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="4f38d-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4f38d-109">[in] `rModuleRefs` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="4f38d-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="4f38d-110">弄中返回的 ModuleRef 令牌数 `rModuleRefs` 。</span><span class="sxs-lookup"><span data-stu-id="4f38d-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f38d-111">返回值</span><span class="sxs-lookup"><span data-stu-id="4f38d-111">Return Value</span></span>  
  
|<span data-ttu-id="4f38d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f38d-112">HRESULT</span></span>|<span data-ttu-id="4f38d-113">说明</span><span class="sxs-lookup"><span data-stu-id="4f38d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4f38d-114">`EnumModuleRefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="4f38d-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4f38d-115">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="4f38d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4f38d-116">在这种情况下， `pcModuleRefs` 为零。</span><span class="sxs-lookup"><span data-stu-id="4f38d-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f38d-117">要求</span><span class="sxs-lookup"><span data-stu-id="4f38d-117">Requirements</span></span>  
 <span data-ttu-id="4f38d-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f38d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f38d-119">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="4f38d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f38d-120">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="4f38d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f38d-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f38d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f38d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f38d-122">See also</span></span>

- [<span data-ttu-id="4f38d-123">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="4f38d-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4f38d-124">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="4f38d-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
