---
title: COR_PRF_CLAUSE_TYPE 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: a308017dc80dd973cbf108ba9df824193775f5ff
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501048"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="a6a27-102">COR_PRF_CLAUSE_TYPE 枚举</span><span class="sxs-lookup"><span data-stu-id="a6a27-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="a6a27-103">指示代码刚进入或离开的异常子句的类型。</span><span class="sxs-lookup"><span data-stu-id="a6a27-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a27-104">语法</span><span class="sxs-lookup"><span data-stu-id="a6a27-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a6a27-105">成员</span><span class="sxs-lookup"><span data-stu-id="a6a27-105">Members</span></span>  
  
|<span data-ttu-id="a6a27-106">成员</span><span class="sxs-lookup"><span data-stu-id="a6a27-106">Member</span></span>|<span data-ttu-id="a6a27-107">描述</span><span class="sxs-lookup"><span data-stu-id="a6a27-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="a6a27-108">异常子句无效。</span><span class="sxs-lookup"><span data-stu-id="a6a27-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="a6a27-109">Exception 子句是一个筛选器表达式。</span><span class="sxs-lookup"><span data-stu-id="a6a27-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="a6a27-110">Exception 子句为 `catch` 语句。</span><span class="sxs-lookup"><span data-stu-id="a6a27-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="a6a27-111">Exception 子句为 `finally` 语句。</span><span class="sxs-lookup"><span data-stu-id="a6a27-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6a27-112">要求</span><span class="sxs-lookup"><span data-stu-id="a6a27-112">Requirements</span></span>  
 <span data-ttu-id="a6a27-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a27-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a27-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6a27-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6a27-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6a27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6a27-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a27-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6a27-117">See also</span></span>

- [<span data-ttu-id="a6a27-118">分析枚举</span><span class="sxs-lookup"><span data-stu-id="a6a27-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
