---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE 结构
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 8b3785955ec138bbf898e84aa4deb5ed2a6e6b53
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500944"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="b6278-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 结构</span><span class="sxs-lookup"><span data-stu-id="b6278-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="b6278-103">表示内存中按从左向右的顺序连续存储的函数自变量块。</span><span class="sxs-lookup"><span data-stu-id="b6278-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6278-104">语法</span><span class="sxs-lookup"><span data-stu-id="b6278-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="b6278-105">成员</span><span class="sxs-lookup"><span data-stu-id="b6278-105">Members</span></span>  
  
|<span data-ttu-id="b6278-106">成员</span><span class="sxs-lookup"><span data-stu-id="b6278-106">Members</span></span>|<span data-ttu-id="b6278-107">说明</span><span class="sxs-lookup"><span data-stu-id="b6278-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="b6278-108">块的起始地址。</span><span class="sxs-lookup"><span data-stu-id="b6278-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="b6278-109">连续块的长度。</span><span class="sxs-lookup"><span data-stu-id="b6278-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6278-110">要求</span><span class="sxs-lookup"><span data-stu-id="b6278-110">Requirements</span></span>  
 <span data-ttu-id="b6278-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6278-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6278-112">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="b6278-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b6278-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6278-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6278-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6278-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6278-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6278-115">See also</span></span>

- [<span data-ttu-id="b6278-116">分析结构</span><span class="sxs-lookup"><span data-stu-id="b6278-116">Profiling Structures</span></span>](profiling-structures.md)
