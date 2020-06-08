---
title: IMetaDataImport::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: 5de62db4180a6a9160193053fe42e39cebc34d0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492469"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="b3c49-102">IMetaDataImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="b3c49-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="b3c49-103">关闭由指定句柄标识的枚举器。</span><span class="sxs-lookup"><span data-stu-id="b3c49-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c49-104">语法</span><span class="sxs-lookup"><span data-stu-id="b3c49-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3c49-105">参数</span><span class="sxs-lookup"><span data-stu-id="b3c49-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b3c49-106">中要关闭的枚举器的句柄。</span><span class="sxs-lookup"><span data-stu-id="b3c49-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3c49-107">注解</span><span class="sxs-lookup"><span data-stu-id="b3c49-107">Remarks</span></span>  
 <span data-ttu-id="b3c49-108">由指定的句柄 `hEnum` 是从以前的 `Enum` *名称*调用获取的（例如， [IMetaDataImport：： EnumTypeDefs](imetadataimport-enumtypedefs-method.md)）。</span><span class="sxs-lookup"><span data-stu-id="b3c49-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c49-109">要求</span><span class="sxs-lookup"><span data-stu-id="b3c49-109">Requirements</span></span>  
 <span data-ttu-id="b3c49-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3c49-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c49-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="b3c49-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3c49-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="b3c49-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3c49-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c49-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3c49-114">See also</span></span>

- [<span data-ttu-id="b3c49-115">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="b3c49-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b3c49-116">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="b3c49-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
