---
title: IMetaDataImport2::GetGenericParamConstraintProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 8a1cdff313dae73e3f5e8918ff2ef395c80b115d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490622"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="e63d5-102">IMetaDataImport2::GetGenericParamConstraintProps 方法</span><span class="sxs-lookup"><span data-stu-id="e63d5-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="e63d5-103">获取与指定约束标记所表示的泛型参数约束关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="e63d5-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63d5-104">语法</span><span class="sxs-lookup"><span data-stu-id="e63d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e63d5-105">参数</span><span class="sxs-lookup"><span data-stu-id="e63d5-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="e63d5-106">中要为其返回元数据的泛型参数约束的标记。</span><span class="sxs-lookup"><span data-stu-id="e63d5-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="e63d5-107">弄指向表示受约束的泛型参数的标记的指针。</span><span class="sxs-lookup"><span data-stu-id="e63d5-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="e63d5-108">弄一个指针，指向表示上的约束的 TypeDef、TypeRef 或 TypeSpec 标记 `ptGenericParam` 。</span><span class="sxs-lookup"><span data-stu-id="e63d5-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e63d5-109">要求</span><span class="sxs-lookup"><span data-stu-id="e63d5-109">Requirements</span></span>  
 <span data-ttu-id="e63d5-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e63d5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e63d5-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="e63d5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e63d5-112">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="e63d5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e63d5-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e63d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63d5-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e63d5-114">See also</span></span>

- [<span data-ttu-id="e63d5-115">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="e63d5-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="e63d5-116">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="e63d5-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
