---
title: COR_PRF_CODE_INFO 结构
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 9dbe0219f5932a9d212edaf5181b96335c47db0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501009"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="47d45-102">COR_PRF_CODE_INFO 结构</span><span class="sxs-lookup"><span data-stu-id="47d45-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="47d45-103">表示存储在内存中的一个本机代码连续块。</span><span class="sxs-lookup"><span data-stu-id="47d45-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d45-104">语法</span><span class="sxs-lookup"><span data-stu-id="47d45-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="47d45-105">成员</span><span class="sxs-lookup"><span data-stu-id="47d45-105">Members</span></span>  
  
|<span data-ttu-id="47d45-106">成员</span><span class="sxs-lookup"><span data-stu-id="47d45-106">Member</span></span>|<span data-ttu-id="47d45-107">描述</span><span class="sxs-lookup"><span data-stu-id="47d45-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="47d45-108">连续代码块的起始地址。</span><span class="sxs-lookup"><span data-stu-id="47d45-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="47d45-109">块的大小。</span><span class="sxs-lookup"><span data-stu-id="47d45-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47d45-110">要求</span><span class="sxs-lookup"><span data-stu-id="47d45-110">Requirements</span></span>  
 <span data-ttu-id="47d45-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47d45-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47d45-112">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="47d45-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="47d45-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47d45-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47d45-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47d45-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d45-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47d45-115">See also</span></span>

- [<span data-ttu-id="47d45-116">分析结构</span><span class="sxs-lookup"><span data-stu-id="47d45-116">Profiling Structures</span></span>](profiling-structures.md)
