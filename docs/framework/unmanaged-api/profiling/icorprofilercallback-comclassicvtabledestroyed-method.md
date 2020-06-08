---
title: ICorProfilerCallback::COMClassicVTableDestroyed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: 708981155589d491a3b1819adb611a28072dd1bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500309"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="1e5d9-102">ICorProfilerCallback::COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="1e5d9-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="1e5d9-103">通知探查器正在销毁 COM 互操作 vtable。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e5d9-104">此回调很可能永远不会发生，因为 vtables 的销毁操作非常接近关闭。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5d9-105">语法</span><span class="sxs-lookup"><span data-stu-id="1e5d9-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e5d9-106">参数</span><span class="sxs-lookup"><span data-stu-id="1e5d9-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="1e5d9-107">\[in] 为其创建了此 vtable 的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="1e5d9-108">\[in] 类实现的接口的 ID。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="1e5d9-109">如果接口仅限内部接口，此值可能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="1e5d9-110">\[in] 指向 vtable 开头的指针。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e5d9-111">注解</span><span class="sxs-lookup"><span data-stu-id="1e5d9-111">Remarks</span></span>  
 <span data-ttu-id="1e5d9-112">探查器不应在此方法的实现中被阻止，因为堆栈可能不处于允许垃圾回收的状态，因此无法启用抢先垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1e5d9-113">如果探查器在此处阻止并且试图进行垃圾回收，则运行时将被阻止，直到此回调返回。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1e5d9-114">探查器的此方法的实现不应调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e5d9-115">要求</span><span class="sxs-lookup"><span data-stu-id="1e5d9-115">Requirements</span></span>  
 <span data-ttu-id="1e5d9-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e5d9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e5d9-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e5d9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e5d9-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e5d9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e5d9-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e5d9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5d9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e5d9-120">See also</span></span>

- [<span data-ttu-id="1e5d9-121">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="1e5d9-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1e5d9-122">COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="1e5d9-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
