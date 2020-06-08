---
title: IMetaDataImport::IsValidToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 9190d021b801be951d214406dde7e6d76da15608
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503432"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="9fb13-102">IMetaDataImport::IsValidToken 方法</span><span class="sxs-lookup"><span data-stu-id="9fb13-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="9fb13-103">获取指示指定的标记是否包含对代码对象的有效引用的值。</span><span class="sxs-lookup"><span data-stu-id="9fb13-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb13-104">语法</span><span class="sxs-lookup"><span data-stu-id="9fb13-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fb13-105">参数</span><span class="sxs-lookup"><span data-stu-id="9fb13-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9fb13-106">中要检查其引用有效性的标记。</span><span class="sxs-lookup"><span data-stu-id="9fb13-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fb13-107">返回值</span><span class="sxs-lookup"><span data-stu-id="9fb13-107">Return Value</span></span>  
 <span data-ttu-id="9fb13-108">`true`如果 `tk` 是当前范围内的有效元数据标记，则为。</span><span class="sxs-lookup"><span data-stu-id="9fb13-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="9fb13-109">否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="9fb13-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb13-110">要求</span><span class="sxs-lookup"><span data-stu-id="9fb13-110">Requirements</span></span>  
 <span data-ttu-id="9fb13-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9fb13-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb13-112">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="9fb13-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fb13-113">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="9fb13-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fb13-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb13-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fb13-115">See also</span></span>

- [<span data-ttu-id="9fb13-116">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="9fb13-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9fb13-117">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="9fb13-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
