---
title: IMetaDataImport::EnumFieldsWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 68261b165847a5c3ee29adbc4908451fb00c5443
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492260"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="436c7-102">IMetaDataImport::EnumFieldsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="436c7-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="436c7-103">枚举具有指定名称的指定类型的 FieldDef 标记。</span><span class="sxs-lookup"><span data-stu-id="436c7-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="436c7-104">语法</span><span class="sxs-lookup"><span data-stu-id="436c7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="436c7-105">参数</span><span class="sxs-lookup"><span data-stu-id="436c7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="436c7-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="436c7-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="436c7-107">中要枚举其字段的类型的标记。</span><span class="sxs-lookup"><span data-stu-id="436c7-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="436c7-108">中用于限制枚举的作用域的字段名称。</span><span class="sxs-lookup"><span data-stu-id="436c7-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="436c7-109">弄用于存储 FieldDef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="436c7-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="436c7-110">[in] `rFields` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="436c7-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="436c7-111">弄中返回的 FieldDef 令牌的实际数量 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="436c7-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="436c7-112">注解</span><span class="sxs-lookup"><span data-stu-id="436c7-112">Remarks</span></span>  
 <span data-ttu-id="436c7-113">与[IMetaDataImport：： EnumFields](imetadataimport-enumfields-method.md)不同，会 `EnumFieldsWithName` 丢弃所有不具有指定名称的字段标记。</span><span class="sxs-lookup"><span data-stu-id="436c7-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="436c7-114">返回值</span><span class="sxs-lookup"><span data-stu-id="436c7-114">Return Value</span></span>  
  
|<span data-ttu-id="436c7-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="436c7-115">HRESULT</span></span>|<span data-ttu-id="436c7-116">说明</span><span class="sxs-lookup"><span data-stu-id="436c7-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="436c7-117">`EnumFieldsWithName`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="436c7-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="436c7-118">没有要枚举的字段。</span><span class="sxs-lookup"><span data-stu-id="436c7-118">There are no fields to enumerate.</span></span> <span data-ttu-id="436c7-119">在这种情况下， `pcTokens` 为零。</span><span class="sxs-lookup"><span data-stu-id="436c7-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="436c7-120">要求</span><span class="sxs-lookup"><span data-stu-id="436c7-120">Requirements</span></span>  
 <span data-ttu-id="436c7-121">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="436c7-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="436c7-122">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="436c7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="436c7-123">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="436c7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="436c7-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="436c7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436c7-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="436c7-125">See also</span></span>

- [<span data-ttu-id="436c7-126">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="436c7-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="436c7-127">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="436c7-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
