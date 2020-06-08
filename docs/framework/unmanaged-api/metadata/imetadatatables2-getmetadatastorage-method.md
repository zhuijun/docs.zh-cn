---
title: IMetaDataTables2::GetMetaDataStorage 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: 55fcde6c47705e515eb2d20f25ac870e257b92c0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501087"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="a4da6-102">IMetaDataTables2::GetMetaDataStorage 方法</span><span class="sxs-lookup"><span data-stu-id="a4da6-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="a4da6-103">获取指定节中存储的元数据的大小和内容。</span><span class="sxs-lookup"><span data-stu-id="a4da6-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4da6-104">语法</span><span class="sxs-lookup"><span data-stu-id="a4da6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4da6-105">参数</span><span class="sxs-lookup"><span data-stu-id="a4da6-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="a4da6-106">[in，out]指向元数据部分的指针。</span><span class="sxs-lookup"><span data-stu-id="a4da6-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="a4da6-107">弄元数据流的大小。</span><span class="sxs-lookup"><span data-stu-id="a4da6-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4da6-108">要求</span><span class="sxs-lookup"><span data-stu-id="a4da6-108">Requirements</span></span>  
 <span data-ttu-id="a4da6-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4da6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4da6-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="a4da6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4da6-111">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="a4da6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4da6-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4da6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4da6-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4da6-113">See also</span></span>

- [<span data-ttu-id="a4da6-114">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="a4da6-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="a4da6-115">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="a4da6-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
