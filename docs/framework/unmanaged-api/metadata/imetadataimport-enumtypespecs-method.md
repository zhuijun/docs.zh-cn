---
title: IMetaDataImport::EnumTypeSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503713"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="a0533-102">IMetaDataImport::EnumTypeSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="a0533-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="a0533-103">枚举当前元数据范围内定义的 TypeSpec 标记。</span><span class="sxs-lookup"><span data-stu-id="a0533-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0533-104">语法</span><span class="sxs-lookup"><span data-stu-id="a0533-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0533-105">参数</span><span class="sxs-lookup"><span data-stu-id="a0533-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a0533-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="a0533-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a0533-107">此方法的第一次调用时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="a0533-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="a0533-108">弄用于存储 TypeSpec 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="a0533-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a0533-109">[in] `rTypeSpecs` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="a0533-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="a0533-110">弄中返回的 TypeSpec 标记的数目 `rTypeSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="a0533-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0533-111">返回值</span><span class="sxs-lookup"><span data-stu-id="a0533-111">Return Value</span></span>  
  
|<span data-ttu-id="a0533-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0533-112">HRESULT</span></span>|<span data-ttu-id="a0533-113">说明</span><span class="sxs-lookup"><span data-stu-id="a0533-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a0533-114">`EnumTypeSpecs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="a0533-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a0533-115">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="a0533-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a0533-116">在这种情况下， `pcTypeSpecs` 为零。</span><span class="sxs-lookup"><span data-stu-id="a0533-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0533-117">注解</span><span class="sxs-lookup"><span data-stu-id="a0533-117">Remarks</span></span>  
 <span data-ttu-id="a0533-118">TypeSpec 标记由[IMetaDataEmit：： GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md)方法创建。</span><span class="sxs-lookup"><span data-stu-id="a0533-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0533-119">要求</span><span class="sxs-lookup"><span data-stu-id="a0533-119">Requirements</span></span>  
 <span data-ttu-id="a0533-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0533-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0533-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="a0533-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0533-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="a0533-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0533-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0533-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0533-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0533-124">See also</span></span>

- [<span data-ttu-id="a0533-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="a0533-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a0533-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="a0533-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
