---
title: IMetaDataImport::ResetEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: bc7f1740d666211b63cd93e6f1c0e6955f61ec5d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503453"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="27bcf-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="27bcf-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="27bcf-103">将指定的枚举器重置到指定位置。</span><span class="sxs-lookup"><span data-stu-id="27bcf-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27bcf-104">语法</span><span class="sxs-lookup"><span data-stu-id="27bcf-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27bcf-105">参数</span><span class="sxs-lookup"><span data-stu-id="27bcf-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="27bcf-106">中要重置的枚举数。</span><span class="sxs-lookup"><span data-stu-id="27bcf-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="27bcf-107">中要放置枚举器的新位置。</span><span class="sxs-lookup"><span data-stu-id="27bcf-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27bcf-108">要求</span><span class="sxs-lookup"><span data-stu-id="27bcf-108">Requirements</span></span>  
 <span data-ttu-id="27bcf-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27bcf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27bcf-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="27bcf-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27bcf-111">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="27bcf-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27bcf-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27bcf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bcf-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27bcf-113">See also</span></span>

- [<span data-ttu-id="27bcf-114">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="27bcf-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="27bcf-115">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="27bcf-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
