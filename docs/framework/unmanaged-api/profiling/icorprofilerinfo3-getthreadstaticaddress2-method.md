---
title: ICorProfilerInfo3::GetThreadStaticAddress2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: a27e7ca156ca138078215a65486ac4b965c6a93d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496329"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="10eb4-102">ICorProfilerInfo3::GetThreadStaticAddress2 方法</span><span class="sxs-lookup"><span data-stu-id="10eb4-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="10eb4-103">获取指定线程和应用程序域范围内的指定线程静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="10eb4-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10eb4-104">语法</span><span class="sxs-lookup"><span data-stu-id="10eb4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10eb4-105">参数</span><span class="sxs-lookup"><span data-stu-id="10eb4-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="10eb4-106">中包含请求的线程静态字段的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="10eb4-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="10eb4-107">中请求的线程静态字段的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="10eb4-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="10eb4-108">[in] 应用程序域的 ID。</span><span class="sxs-lookup"><span data-stu-id="10eb4-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="10eb4-109">中作为所请求的静态字段的作用域的线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="10eb4-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="10eb4-110">弄一个指针，指向指定线程内的静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="10eb4-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10eb4-111">注解</span><span class="sxs-lookup"><span data-stu-id="10eb4-111">Remarks</span></span>  
 <span data-ttu-id="10eb4-112">此 `GetThreadStaticAddress2` 方法可能会返回以下内容之一：</span><span class="sxs-lookup"><span data-stu-id="10eb4-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="10eb4-113">如果未在指定的上下文中为给定的静态字段分配地址，则 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="10eb4-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="10eb4-114">可能位于垃圾回收堆中的对象的地址。</span><span class="sxs-lookup"><span data-stu-id="10eb4-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="10eb4-115">这些地址可能会在垃圾回收后失效，因此，在垃圾回收后，探查器不应假定它们是有效的。</span><span class="sxs-lookup"><span data-stu-id="10eb4-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="10eb4-116">在类的类构造函数完成之前， `GetThreadStaticAddress2` 将为其所有静态字段返回 CORPROF_E_DATAINCOMPLETE，不过，某些静态字段可能已经初始化并为垃圾回收对象提供了根。</span><span class="sxs-lookup"><span data-stu-id="10eb4-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="10eb4-117">[ICorProfilerInfo2：： GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md)方法类似于 `GetThreadStaticAddress2` 方法，但不接受应用程序域参数。</span><span class="sxs-lookup"><span data-stu-id="10eb4-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10eb4-118">要求</span><span class="sxs-lookup"><span data-stu-id="10eb4-118">Requirements</span></span>  
 <span data-ttu-id="10eb4-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10eb4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10eb4-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10eb4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10eb4-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10eb4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10eb4-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10eb4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10eb4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10eb4-123">See also</span></span>

- [<span data-ttu-id="10eb4-124">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="10eb4-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="10eb4-125">分析接口</span><span class="sxs-lookup"><span data-stu-id="10eb4-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="10eb4-126">分析</span><span class="sxs-lookup"><span data-stu-id="10eb4-126">Profiling</span></span>](index.md)
