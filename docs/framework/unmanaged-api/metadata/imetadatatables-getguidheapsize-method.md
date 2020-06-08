---
title: IMetaDataTables::GetGuidHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: 71a75defa72e4fe3594b4d0ceff45273b3a35395
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490349"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="27bd9-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="27bd9-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="27bd9-103">获取 GUID 堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="27bd9-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27bd9-104">语法</span><span class="sxs-lookup"><span data-stu-id="27bd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27bd9-105">参数</span><span class="sxs-lookup"><span data-stu-id="27bd9-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="27bd9-106">弄一个指针，指向 GUID 堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="27bd9-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27bd9-107">要求</span><span class="sxs-lookup"><span data-stu-id="27bd9-107">Requirements</span></span>  
 <span data-ttu-id="27bd9-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27bd9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27bd9-109">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="27bd9-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27bd9-110">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="27bd9-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27bd9-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27bd9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bd9-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27bd9-112">See also</span></span>

- [<span data-ttu-id="27bd9-113">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="27bd9-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="27bd9-114">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="27bd9-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
