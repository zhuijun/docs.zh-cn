---
title: ICorProfilerInfo4::EnumThreads 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d42c86a458661d3559f99235a6d5b208c82d1963
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502803"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="27bb7-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="27bb7-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="27bb7-103">返回一个枚举器，该枚举器提供按顺序循环访问所分析进程中所有托管线程的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="27bb7-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27bb7-104">语法</span><span class="sxs-lookup"><span data-stu-id="27bb7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27bb7-105">参数</span><span class="sxs-lookup"><span data-stu-id="27bb7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="27bb7-106">弄指向[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)接口的指针。</span><span class="sxs-lookup"><span data-stu-id="27bb7-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27bb7-107">备注</span><span class="sxs-lookup"><span data-stu-id="27bb7-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27bb7-108">要求</span><span class="sxs-lookup"><span data-stu-id="27bb7-108">Requirements</span></span>  
 <span data-ttu-id="27bb7-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27bb7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27bb7-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27bb7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27bb7-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27bb7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27bb7-112">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27bb7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bb7-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27bb7-113">See also</span></span>

- [<span data-ttu-id="27bb7-114">ICorProfilerThreadEnum 接口</span><span class="sxs-lookup"><span data-stu-id="27bb7-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="27bb7-115">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="27bb7-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="27bb7-116">分析接口</span><span class="sxs-lookup"><span data-stu-id="27bb7-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="27bb7-117">分析</span><span class="sxs-lookup"><span data-stu-id="27bb7-117">Profiling</span></span>](index.md)
