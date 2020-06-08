---
title: ICorProfilerCallback::COMClassicVTableCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
ms.openlocfilehash: 6c9ec6af90cc47c3c01621563a9813789c25aa1d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500333"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="d1d46-102">ICorProfilerCallback::COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="d1d46-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="d1d46-103">通知探查器已创建指定 IID 和类的 COM 互操作 vtable。</span><span class="sxs-lookup"><span data-stu-id="d1d46-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d46-104">语法</span><span class="sxs-lookup"><span data-stu-id="d1d46-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d46-105">参数</span><span class="sxs-lookup"><span data-stu-id="d1d46-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="d1d46-106">\[in] 已为其创建 vtable 的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="d1d46-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="d1d46-107">\[in] 类实现的接口的 ID。</span><span class="sxs-lookup"><span data-stu-id="d1d46-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="d1d46-108">如果接口仅限内部接口，此值可能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="d1d46-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="d1d46-109">\[in] 指向 vtable 开头的指针。</span><span class="sxs-lookup"><span data-stu-id="d1d46-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="d1d46-110">\[in] vtable 中的槽数。</span><span class="sxs-lookup"><span data-stu-id="d1d46-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1d46-111">注解</span><span class="sxs-lookup"><span data-stu-id="d1d46-111">Remarks</span></span>  
 <span data-ttu-id="d1d46-112">探查器不应在此方法的实现中被阻止，因为堆栈可能不处于允许垃圾回收的状态，因此无法启用抢先垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="d1d46-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d1d46-113">如果探查器在此处阻止并且试图进行垃圾回收，则运行时将被阻止，直到此回调返回。</span><span class="sxs-lookup"><span data-stu-id="d1d46-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d1d46-114">探查器的此方法的实现不应调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="d1d46-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d46-115">要求</span><span class="sxs-lookup"><span data-stu-id="d1d46-115">Requirements</span></span>  
 <span data-ttu-id="d1d46-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d46-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d46-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1d46-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1d46-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1d46-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d46-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d46-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d46-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1d46-120">See also</span></span>

- [<span data-ttu-id="d1d46-121">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="d1d46-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d1d46-122">COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="d1d46-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
