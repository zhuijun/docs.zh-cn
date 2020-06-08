---
title: IMetaDataImport::IsGlobal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
ms.openlocfilehash: d477976952d2c1875a620d1397fd43e5c5e2836f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503466"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="2dd47-102">IMetaDataImport::IsGlobal 方法</span><span class="sxs-lookup"><span data-stu-id="2dd47-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="2dd47-103">获取一个值，该值指示由指定的元数据标记表示的字段、方法或类型是否具有全局范围。</span><span class="sxs-lookup"><span data-stu-id="2dd47-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dd47-104">语法</span><span class="sxs-lookup"><span data-stu-id="2dd47-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dd47-105">参数</span><span class="sxs-lookup"><span data-stu-id="2dd47-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="2dd47-106">中表示类型、字段或方法的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="2dd47-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="2dd47-107">[out] 如果对象具有全局范围，则为 1;否则为0（零）。</span><span class="sxs-lookup"><span data-stu-id="2dd47-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dd47-108">要求</span><span class="sxs-lookup"><span data-stu-id="2dd47-108">Requirements</span></span>  
 <span data-ttu-id="2dd47-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd47-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dd47-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="2dd47-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2dd47-111">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="2dd47-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2dd47-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dd47-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd47-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dd47-113">See also</span></span>

- [<span data-ttu-id="2dd47-114">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="2dd47-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2dd47-115">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="2dd47-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
