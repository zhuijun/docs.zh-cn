---
title: IMetaDataImport::EnumEvents 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 53b1234a176cade5876d70da0cb4eadc18802c69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492299"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="9779d-102">IMetaDataImport::EnumEvents 方法</span><span class="sxs-lookup"><span data-stu-id="9779d-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="9779d-103">枚举指定的 TypeDef 标记的事件定义标记。</span><span class="sxs-lookup"><span data-stu-id="9779d-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9779d-104">语法</span><span class="sxs-lookup"><span data-stu-id="9779d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9779d-105">参数</span><span class="sxs-lookup"><span data-stu-id="9779d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9779d-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="9779d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="9779d-107">中要枚举其事件定义的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="9779d-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="9779d-108">弄返回的事件的数组。</span><span class="sxs-lookup"><span data-stu-id="9779d-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9779d-109">[in] `rEvents` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="9779d-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="9779d-110">弄中返回的实际事件数 `rEvents` 。</span><span class="sxs-lookup"><span data-stu-id="9779d-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9779d-111">返回值</span><span class="sxs-lookup"><span data-stu-id="9779d-111">Return Value</span></span>  
  
|<span data-ttu-id="9779d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9779d-112">HRESULT</span></span>|<span data-ttu-id="9779d-113">说明</span><span class="sxs-lookup"><span data-stu-id="9779d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9779d-114">`EnumEvents`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="9779d-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9779d-115">没有要枚举的事件。</span><span class="sxs-lookup"><span data-stu-id="9779d-115">There are no events to enumerate.</span></span> <span data-ttu-id="9779d-116">在这种情况下， `pcEvents` 为零。</span><span class="sxs-lookup"><span data-stu-id="9779d-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9779d-117">要求</span><span class="sxs-lookup"><span data-stu-id="9779d-117">Requirements</span></span>  
 <span data-ttu-id="9779d-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9779d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9779d-119">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="9779d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9779d-120">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="9779d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9779d-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9779d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9779d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9779d-122">See also</span></span>

- [<span data-ttu-id="9779d-123">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="9779d-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9779d-124">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="9779d-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
