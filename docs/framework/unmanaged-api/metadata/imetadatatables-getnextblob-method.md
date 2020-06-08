---
title: IMetaDataTables::GetNextBlob 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490375"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="1fc91-102">IMetaDataTables::GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="1fc91-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="1fc91-103">获取表中下一个二进制大型对象（BLOB）的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc91-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc91-104">语法</span><span class="sxs-lookup"><span data-stu-id="1fc91-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fc91-105">参数</span><span class="sxs-lookup"><span data-stu-id="1fc91-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="1fc91-106">中从 Blob 的列中返回的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc91-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="1fc91-107">弄指向下一个 BLOB 的索引的指针。</span><span class="sxs-lookup"><span data-stu-id="1fc91-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fc91-108">要求</span><span class="sxs-lookup"><span data-stu-id="1fc91-108">Requirements</span></span>  
 <span data-ttu-id="1fc91-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1fc91-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fc91-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="1fc91-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1fc91-111">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="1fc91-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1fc91-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fc91-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc91-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fc91-113">See also</span></span>

- [<span data-ttu-id="1fc91-114">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="1fc91-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1fc91-115">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="1fc91-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
