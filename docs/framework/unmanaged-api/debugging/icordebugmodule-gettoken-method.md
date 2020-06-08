---
title: ICorDebugModule::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: 1cf4d82200709971201da60d06d0cb929641a104
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501880"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="e3728-102">ICorDebugModule::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="e3728-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="e3728-103">获取此模块的表项的标记。</span><span class="sxs-lookup"><span data-stu-id="e3728-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3728-104">语法</span><span class="sxs-lookup"><span data-stu-id="e3728-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3728-105">参数</span><span class="sxs-lookup"><span data-stu-id="e3728-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="e3728-106">弄指向 `mdModule` 引用模块元数据的标记的指针。</span><span class="sxs-lookup"><span data-stu-id="e3728-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3728-107">注解</span><span class="sxs-lookup"><span data-stu-id="e3728-107">Remarks</span></span>  
 <span data-ttu-id="e3728-108">该令牌可以传递到[IMetaDataImport](../metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../metadata/imetadataimport2-interface.md)和[IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md)元数据导入接口。</span><span class="sxs-lookup"><span data-stu-id="e3728-108">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3728-109">要求</span><span class="sxs-lookup"><span data-stu-id="e3728-109">Requirements</span></span>  
 <span data-ttu-id="e3728-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3728-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3728-111">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3728-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3728-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3728-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3728-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3728-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3728-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3728-114">See also</span></span>

- [<span data-ttu-id="e3728-115">元数据</span><span class="sxs-lookup"><span data-stu-id="e3728-115">Metadata</span></span>](../metadata/index.md)
