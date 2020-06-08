---
title: ICorProfilerInfo2::GetContextStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: 7550caaa7cb4d7ed77dc36ecf0ce0e0cbc541db7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497057"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="9fd72-102">ICorProfilerInfo2::GetContextStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="9fd72-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="9fd72-103">获取指定上下文的范围内的指定上下文静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="9fd72-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd72-104">语法</span><span class="sxs-lookup"><span data-stu-id="9fd72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fd72-105">参数</span><span class="sxs-lookup"><span data-stu-id="9fd72-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9fd72-106">中包含请求的上下文静态字段的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="9fd72-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="9fd72-107">中请求的上下文静态字段的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="9fd72-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="9fd72-108">中作为所请求的上下文静态字段的作用域的上下文的 ID。</span><span class="sxs-lookup"><span data-stu-id="9fd72-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="9fd72-109">弄指向指定上下文内的静态字段的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="9fd72-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fd72-110">注解</span><span class="sxs-lookup"><span data-stu-id="9fd72-110">Remarks</span></span>  
 <span data-ttu-id="9fd72-111">此 `GetContextStaticAddress` 方法可能会返回以下内容之一：</span><span class="sxs-lookup"><span data-stu-id="9fd72-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="9fd72-112">如果未在指定的上下文中为给定的静态字段分配地址，则 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9fd72-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="9fd72-113">可能位于垃圾回收堆中的对象的地址。</span><span class="sxs-lookup"><span data-stu-id="9fd72-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="9fd72-114">这些地址可能会在垃圾回收后失效，因此，在垃圾回收后，探查器不应假定它们是有效的。</span><span class="sxs-lookup"><span data-stu-id="9fd72-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="9fd72-115">在类的类构造函数完成之前， `GetContextStaticAddress` 将为其所有静态字段返回 CORPROF_E_DATAINCOMPLETE，不过，某些静态字段可能已经初始化并为垃圾回收对象提供了根。</span><span class="sxs-lookup"><span data-stu-id="9fd72-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fd72-116">要求</span><span class="sxs-lookup"><span data-stu-id="9fd72-116">Requirements</span></span>  
 <span data-ttu-id="9fd72-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9fd72-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fd72-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9fd72-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9fd72-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fd72-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fd72-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fd72-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd72-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fd72-121">See also</span></span>

- [<span data-ttu-id="9fd72-122">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="9fd72-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="9fd72-123">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="9fd72-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
