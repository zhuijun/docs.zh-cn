---
title: IMetaDataFilter::IsTokenMarked 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: eb0ebab0f4e05d81730d5beb2b5345e319e8e274
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492533"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="62824-102">IMetaDataFilter::IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="62824-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="62824-103">获取一个值，该值指示指定的元数据标记是否已标记为已处理。</span><span class="sxs-lookup"><span data-stu-id="62824-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62824-104">语法</span><span class="sxs-lookup"><span data-stu-id="62824-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62824-105">参数</span><span class="sxs-lookup"><span data-stu-id="62824-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="62824-106">中要检查处理标记的标记。</span><span class="sxs-lookup"><span data-stu-id="62824-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="62824-107">弄如果已处理，则该值为 `true` `tk` ; 否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="62824-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62824-108">要求</span><span class="sxs-lookup"><span data-stu-id="62824-108">Requirements</span></span>  
 <span data-ttu-id="62824-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62824-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62824-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="62824-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62824-111">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="62824-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62824-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62824-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62824-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62824-113">See also</span></span>

- [<span data-ttu-id="62824-114">IMetaDataFilter 接口</span><span class="sxs-lookup"><span data-stu-id="62824-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
