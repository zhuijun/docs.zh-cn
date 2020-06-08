---
title: IMetaDataTables::GetBlobHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
ms.openlocfilehash: 68e29e932e477f286db00b0c989a3346bd13c9bc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501217"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="127e3-102">IMetaDataTables::GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="127e3-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="127e3-103">获取二进制大型对象（BLOB）堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="127e3-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="127e3-104">语法</span><span class="sxs-lookup"><span data-stu-id="127e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="127e3-105">参数</span><span class="sxs-lookup"><span data-stu-id="127e3-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="127e3-106">弄一个指针，指向 BLOB 堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="127e3-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="127e3-107">要求</span><span class="sxs-lookup"><span data-stu-id="127e3-107">Requirements</span></span>  
 <span data-ttu-id="127e3-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="127e3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="127e3-109">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="127e3-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="127e3-110">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="127e3-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="127e3-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="127e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127e3-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="127e3-112">See also</span></span>

- [<span data-ttu-id="127e3-113">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="127e3-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="127e3-114">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="127e3-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
