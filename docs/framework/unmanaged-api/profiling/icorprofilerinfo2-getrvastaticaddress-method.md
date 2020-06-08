---
title: ICorProfilerInfo2::GetRVAStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: 525fa2efa39909390d874fb97d9f11e647340ea9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496940"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="2ca6f-102">ICorProfilerInfo2::GetRVAStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="2ca6f-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="2ca6f-103">获取指定的相对虚拟地址（RVA）静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca6f-104">语法</span><span class="sxs-lookup"><span data-stu-id="2ca6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ca6f-105">参数</span><span class="sxs-lookup"><span data-stu-id="2ca6f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2ca6f-106">中包含请求的 RVA 静态字段的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="2ca6f-107">中请求的 RVA 静态字段的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="2ca6f-108">弄指向 RVA 静态字段的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ca6f-109">注解</span><span class="sxs-lookup"><span data-stu-id="2ca6f-109">Remarks</span></span>  
 <span data-ttu-id="2ca6f-110">此 `GetRVAStaticAddress` 方法可能会返回以下内容之一：</span><span class="sxs-lookup"><span data-stu-id="2ca6f-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="2ca6f-111">如果未在指定的上下文中为给定的静态字段分配地址，则 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="2ca6f-112">可能位于垃圾回收堆中的对象的地址。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="2ca6f-113">这些地址可能会在垃圾回收后失效，因此，在垃圾回收后，探查器不应假定它们是有效的。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="2ca6f-114">在类的类构造函数完成之前， `GetRVAStaticAddress` 将为其所有静态字段返回 CORPROF_E_DATAINCOMPLETE，不过，某些静态字段可能已经初始化并且可能是对垃圾回收对象的根。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ca6f-115">要求</span><span class="sxs-lookup"><span data-stu-id="2ca6f-115">Requirements</span></span>  
 <span data-ttu-id="2ca6f-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca6f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca6f-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ca6f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ca6f-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ca6f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ca6f-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca6f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca6f-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ca6f-120">See also</span></span>

- [<span data-ttu-id="2ca6f-121">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="2ca6f-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2ca6f-122">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="2ca6f-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
