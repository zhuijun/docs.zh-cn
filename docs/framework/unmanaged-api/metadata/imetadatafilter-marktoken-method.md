---
title: IMetaDataFilter::MarkToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 28a5f79f6fa8d25fd254c4093b0f76e0308edbad
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492520"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="55e66-102">IMetaDataFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="55e66-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="55e66-103">设置一个值，该值指示已处理指定的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="55e66-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e66-104">语法</span><span class="sxs-lookup"><span data-stu-id="55e66-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55e66-105">参数</span><span class="sxs-lookup"><span data-stu-id="55e66-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="55e66-106">中标记为已处理的标记。</span><span class="sxs-lookup"><span data-stu-id="55e66-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55e66-107">要求</span><span class="sxs-lookup"><span data-stu-id="55e66-107">Requirements</span></span>  
 <span data-ttu-id="55e66-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55e66-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55e66-109">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="55e66-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55e66-110">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="55e66-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55e66-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55e66-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e66-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55e66-112">See also</span></span>

- [<span data-ttu-id="55e66-113">IMetaDataFilter 接口</span><span class="sxs-lookup"><span data-stu-id="55e66-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
