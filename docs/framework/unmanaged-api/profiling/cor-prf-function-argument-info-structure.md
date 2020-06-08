---
title: COR_PRF_FUNCTION_ARGUMENT_INFO 结构
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
ms.openlocfilehash: 9fca75ae59b95a226b51768b3e1bfb220d9926f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500957"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="0eaf5-102">COR_PRF_FUNCTION_ARGUMENT_INFO 结构</span><span class="sxs-lookup"><span data-stu-id="0eaf5-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="0eaf5-103">按从左向右的顺序表示函数的参数。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eaf5-104">语法</span><span class="sxs-lookup"><span data-stu-id="0eaf5-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0eaf5-105">成员</span><span class="sxs-lookup"><span data-stu-id="0eaf5-105">Members</span></span>  
  
|<span data-ttu-id="0eaf5-106">成员</span><span class="sxs-lookup"><span data-stu-id="0eaf5-106">Member</span></span>|<span data-ttu-id="0eaf5-107">描述</span><span class="sxs-lookup"><span data-stu-id="0eaf5-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="0eaf5-108">参数块的数目。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-108">The number of blocks of arguments.</span></span> <span data-ttu-id="0eaf5-109">也就是说，此值是数组中[COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)的结构数 `ranges` 。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="0eaf5-110">所有参数的总大小。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-110">The total size of all arguments.</span></span> <span data-ttu-id="0eaf5-111">换言之，此值是自变量长度之和。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="0eaf5-112">结构的数组 `COR_PRF_FUNCTION_ARGUMENT_RANGE` ，其中每个结构都表示一个函数参数块。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eaf5-113">注解</span><span class="sxs-lookup"><span data-stu-id="0eaf5-113">Remarks</span></span>  
 <span data-ttu-id="0eaf5-114">函数可以包含多个参数。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-114">A function may have many arguments.</span></span> <span data-ttu-id="0eaf5-115">这些参数可能不会连续存储在内存中。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="0eaf5-116">在一个位置，您可能有一个包含三个自变量的块、另一个位置中的两个参数块，以及在不同位置中的一个自变量的最后一个块。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="0eaf5-117">这些参数全部用于相同的函数;它们只是存储在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="0eaf5-118">`COR_PRF_FUNCTION_ARGUMENT_INFO`结构表示一个函数的所有自变量。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="0eaf5-119">它使用数组引用函数参数的所有块。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="0eaf5-120">因此，对于单个函数，你有一个 `COR_PRF_FUNCTION_ARGUMENT_INFO` 结构，它引用多个 `COR_PRF_FUNCTION_ARGUMENT_RANGE` 结构，其中每个结构都指向一个或多个函数自变量。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="0eaf5-121">存储在寄存器中的参数会溢出到内存中以生成结构。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eaf5-122">要求</span><span class="sxs-lookup"><span data-stu-id="0eaf5-122">Requirements</span></span>  
 <span data-ttu-id="0eaf5-123">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0eaf5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eaf5-124">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="0eaf5-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0eaf5-125">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0eaf5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0eaf5-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eaf5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eaf5-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0eaf5-127">See also</span></span>

- [<span data-ttu-id="0eaf5-128">分析结构</span><span class="sxs-lookup"><span data-stu-id="0eaf5-128">Profiling Structures</span></span>](profiling-structures.md)
