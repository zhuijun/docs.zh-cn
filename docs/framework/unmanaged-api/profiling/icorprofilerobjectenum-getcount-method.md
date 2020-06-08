---
title: ICorProfilerObjectEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: 4c867a9e263f022fc6f8d90a883562e2560ad1b2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494652"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="badb6-102">ICorProfilerObjectEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="badb6-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="badb6-103">获取集合中冻结对象的总数。</span><span class="sxs-lookup"><span data-stu-id="badb6-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="badb6-104">语法</span><span class="sxs-lookup"><span data-stu-id="badb6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="badb6-105">参数</span><span class="sxs-lookup"><span data-stu-id="badb6-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="badb6-106">弄一个指针，它指向集合中的冻结对象的数目。</span><span class="sxs-lookup"><span data-stu-id="badb6-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="badb6-107">此方法在 .NET Framework 版本 3.5 Service Pack 1 （SP1）和更高版本中将始终返回零。</span><span class="sxs-lookup"><span data-stu-id="badb6-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="badb6-108">要求</span><span class="sxs-lookup"><span data-stu-id="badb6-108">Requirements</span></span>  
 <span data-ttu-id="badb6-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="badb6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="badb6-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="badb6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="badb6-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="badb6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="badb6-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="badb6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="badb6-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="badb6-113">See also</span></span>

- [<span data-ttu-id="badb6-114">ICorProfilerObjectEnum 接口</span><span class="sxs-lookup"><span data-stu-id="badb6-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
