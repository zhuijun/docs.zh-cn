---
title: IMetaDataImport::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: 358ca84f32e1b233116605bf5486cc9a01b42e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503493"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="897e8-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="897e8-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="897e8-103">获取指定元数据标记所表示的文字字符串。</span><span class="sxs-lookup"><span data-stu-id="897e8-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="897e8-104">语法</span><span class="sxs-lookup"><span data-stu-id="897e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="897e8-105">参数</span><span class="sxs-lookup"><span data-stu-id="897e8-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="897e8-106">中要为其返回关联字符串的字符串标记。</span><span class="sxs-lookup"><span data-stu-id="897e8-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="897e8-107">弄请求的字符串的副本。</span><span class="sxs-lookup"><span data-stu-id="897e8-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="897e8-108">中请求的的最大大小（以宽字符为大小） `szString` 。</span><span class="sxs-lookup"><span data-stu-id="897e8-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="897e8-109">弄返回的的大小（以宽字符为大小） `szString` 。</span><span class="sxs-lookup"><span data-stu-id="897e8-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="897e8-110">要求</span><span class="sxs-lookup"><span data-stu-id="897e8-110">Requirements</span></span>  
 <span data-ttu-id="897e8-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="897e8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="897e8-112">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="897e8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="897e8-113">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="897e8-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="897e8-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="897e8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897e8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="897e8-115">See also</span></span>

- [<span data-ttu-id="897e8-116">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="897e8-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="897e8-117">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="897e8-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
