---
title: IMetaDataImport::EnumTypeRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 0c7e96c50e59902cde4686f908047a86dd2b6a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503739"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="3f52a-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="3f52a-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="3f52a-103">枚举当前元数据范围内定义的 TypeRef 标记。</span><span class="sxs-lookup"><span data-stu-id="3f52a-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f52a-104">语法</span><span class="sxs-lookup"><span data-stu-id="3f52a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f52a-105">参数</span><span class="sxs-lookup"><span data-stu-id="3f52a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3f52a-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="3f52a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3f52a-107">第一次调用此方法时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="3f52a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="3f52a-108">弄用于存储 TypeRef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="3f52a-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3f52a-109">[in] `rTypeRefs` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="3f52a-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="3f52a-110">弄一个指针，指向中返回的 TypeRef 标记的数目 `rTypeRefs` 。</span><span class="sxs-lookup"><span data-stu-id="3f52a-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f52a-111">返回值</span><span class="sxs-lookup"><span data-stu-id="3f52a-111">Return Value</span></span>  
  
|<span data-ttu-id="3f52a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f52a-112">HRESULT</span></span>|<span data-ttu-id="3f52a-113">说明</span><span class="sxs-lookup"><span data-stu-id="3f52a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3f52a-114">`EnumTypeRefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="3f52a-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3f52a-115">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="3f52a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3f52a-116">在这种情况下， `pcTypeRefs` 为零。</span><span class="sxs-lookup"><span data-stu-id="3f52a-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f52a-117">注解</span><span class="sxs-lookup"><span data-stu-id="3f52a-117">Remarks</span></span>  
 <span data-ttu-id="3f52a-118">TypeRef 标记表示对类型的引用。</span><span class="sxs-lookup"><span data-stu-id="3f52a-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f52a-119">要求</span><span class="sxs-lookup"><span data-stu-id="3f52a-119">Requirements</span></span>  
 <span data-ttu-id="3f52a-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f52a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f52a-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="3f52a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f52a-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="3f52a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f52a-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f52a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f52a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f52a-124">See also</span></span>

- [<span data-ttu-id="3f52a-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="3f52a-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3f52a-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="3f52a-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
