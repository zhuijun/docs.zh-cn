---
title: IMetaDataTables::GetNextGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 645a9913d0de6f93e59df3dd8ba7267ddb13b41b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490232"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="81208-102">IMetaDataTables::GetNextGuid 方法</span><span class="sxs-lookup"><span data-stu-id="81208-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="81208-103">获取当前表列中的下一个 GUID 值的索引。</span><span class="sxs-lookup"><span data-stu-id="81208-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81208-104">语法</span><span class="sxs-lookup"><span data-stu-id="81208-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81208-105">参数</span><span class="sxs-lookup"><span data-stu-id="81208-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="81208-106">中来自 GUID 表列的索引值。</span><span class="sxs-lookup"><span data-stu-id="81208-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="81208-107">弄指向下一个 GUID 值的索引的指针。</span><span class="sxs-lookup"><span data-stu-id="81208-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81208-108">注解</span><span class="sxs-lookup"><span data-stu-id="81208-108">Remarks</span></span>  

  <span data-ttu-id="81208-109">不建议使用此方法，因为它不返回一致的结果。</span><span class="sxs-lookup"><span data-stu-id="81208-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="81208-110">有关 GUID 表的信息，请参阅公共语言基础结构（CLI）文档，尤其是 "第二部分：元数据定义和语义"。</span><span class="sxs-lookup"><span data-stu-id="81208-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="81208-111">文档在线提供;请参阅[ECMA c # 和公共语言基础结构标准](../../../standard/components.md#applicable-standards)和[标准 ECMA-335-公共语言基础结构（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="81208-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81208-112">要求</span><span class="sxs-lookup"><span data-stu-id="81208-112">Requirements</span></span>  
 <span data-ttu-id="81208-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81208-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81208-114">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="81208-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81208-115">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="81208-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81208-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81208-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81208-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81208-117">See also</span></span>

- [<span data-ttu-id="81208-118">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="81208-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="81208-119">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="81208-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
