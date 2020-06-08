---
title: IMetaDataEmit2::DefineGenericParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503804"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="69286-102">IMetaDataEmit2::DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="69286-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="69286-103">创建泛型类型参数的定义，并获取该泛型类型参数的令牌。</span><span class="sxs-lookup"><span data-stu-id="69286-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69286-104">语法</span><span class="sxs-lookup"><span data-stu-id="69286-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69286-105">参数</span><span class="sxs-lookup"><span data-stu-id="69286-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="69286-106">中`mdTypeDef`或 `mdMethodDef` 标记，它表示要为其定义泛型参数的方法或构造函数。</span><span class="sxs-lookup"><span data-stu-id="69286-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="69286-107">中泛型参数的索引。</span><span class="sxs-lookup"><span data-stu-id="69286-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="69286-108">中描述泛型参数类型的[CorGenericParamAttr](corgenericparamattr-enumeration.md)枚举的值。</span><span class="sxs-lookup"><span data-stu-id="69286-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="69286-109">中参数的名称。</span><span class="sxs-lookup"><span data-stu-id="69286-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="69286-110">中此参数保留供将来进行扩展。</span><span class="sxs-lookup"><span data-stu-id="69286-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="69286-111">中类型约束的零终止数组。</span><span class="sxs-lookup"><span data-stu-id="69286-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="69286-112">数组成员必须是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元数据标记。</span><span class="sxs-lookup"><span data-stu-id="69286-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="69286-113">弄表示泛型参数的标记。</span><span class="sxs-lookup"><span data-stu-id="69286-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69286-114">要求</span><span class="sxs-lookup"><span data-stu-id="69286-114">Requirements</span></span>  
 <span data-ttu-id="69286-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69286-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69286-116">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="69286-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69286-117">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="69286-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="69286-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69286-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69286-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69286-119">See also</span></span>

- [<span data-ttu-id="69286-120">IMetaDataEmit2 接口</span><span class="sxs-lookup"><span data-stu-id="69286-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="69286-121">IMetaDataEmit 接口</span><span class="sxs-lookup"><span data-stu-id="69286-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
