---
title: IMetaDataImport::GetModuleFromScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503576"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="ca716-102">IMetaDataImport::GetModuleFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="ca716-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="ca716-103">获取当前元数据范围内引用的模块的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="ca716-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca716-104">语法</span><span class="sxs-lookup"><span data-stu-id="ca716-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca716-105">参数</span><span class="sxs-lookup"><span data-stu-id="ca716-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="ca716-106">弄一个指针，指向表示当前元数据范围内引用的模块的标记。</span><span class="sxs-lookup"><span data-stu-id="ca716-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca716-107">要求</span><span class="sxs-lookup"><span data-stu-id="ca716-107">Requirements</span></span>  
 <span data-ttu-id="ca716-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca716-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca716-109">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="ca716-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca716-110">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="ca716-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca716-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca716-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca716-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca716-112">See also</span></span>

- [<span data-ttu-id="ca716-113">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="ca716-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ca716-114">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="ca716-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
