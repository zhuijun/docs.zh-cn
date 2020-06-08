---
title: IMetaDataTables::GetGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 6f273cb03ad00957afb2bd78fe538a940fae236a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501230"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="41733-102">IMetaDataTables::GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="41733-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="41733-103">获取指定索引处的行的 GUID。</span><span class="sxs-lookup"><span data-stu-id="41733-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41733-104">语法</span><span class="sxs-lookup"><span data-stu-id="41733-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41733-105">参数</span><span class="sxs-lookup"><span data-stu-id="41733-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="41733-106">中要从中获取 GUID 的行的索引。</span><span class="sxs-lookup"><span data-stu-id="41733-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="41733-107">弄指向 GUID 的指针的指针。</span><span class="sxs-lookup"><span data-stu-id="41733-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41733-108">注解</span><span class="sxs-lookup"><span data-stu-id="41733-108">Remarks</span></span>  

  <span data-ttu-id="41733-109">不建议使用此方法，因为它不返回一致的结果。</span><span class="sxs-lookup"><span data-stu-id="41733-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="41733-110">有关 GUID 表的信息，请参阅公共语言基础结构（CLI）文档，尤其是 "第二部分：元数据定义和语义"。</span><span class="sxs-lookup"><span data-stu-id="41733-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="41733-111">文档在线提供;请参阅[ECMA c # 和公共语言基础结构标准](../../../standard/components.md#applicable-standards)和[标准 ECMA-335-公共语言基础结构（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="41733-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41733-112">要求</span><span class="sxs-lookup"><span data-stu-id="41733-112">Requirements</span></span>  
 <span data-ttu-id="41733-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41733-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41733-114">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="41733-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41733-115">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="41733-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41733-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41733-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41733-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41733-117">See also</span></span>

- [<span data-ttu-id="41733-118">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="41733-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="41733-119">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="41733-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
