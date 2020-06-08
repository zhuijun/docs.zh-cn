---
title: ICorProfilerInfo::GetObjectSize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: 15c843fe138be55a3480f46e0ef8b37bcb445ad0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497967"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="244fd-102">ICorProfilerInfo::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="244fd-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="244fd-103">获取指定对象的大小。</span><span class="sxs-lookup"><span data-stu-id="244fd-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="244fd-104">语法</span><span class="sxs-lookup"><span data-stu-id="244fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="244fd-105">参数</span><span class="sxs-lookup"><span data-stu-id="244fd-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="244fd-106">中对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="244fd-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="244fd-107">弄一个指针，指向对象的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="244fd-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="244fd-108">注解</span><span class="sxs-lookup"><span data-stu-id="244fd-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="244fd-109">此方法已过时。</span><span class="sxs-lookup"><span data-stu-id="244fd-109">This method is obsolete.</span></span> <span data-ttu-id="244fd-110">它在64位平台上为大于4GB 的对象返回 COR_E_OVERFLOW。</span><span class="sxs-lookup"><span data-stu-id="244fd-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="244fd-111">改为使用[ICorProfilerInfo4：： GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="244fd-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="244fd-112">相同类型的不同对象通常具有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="244fd-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="244fd-113">但是，某些类型（例如数组或字符串）对于每个对象可能有不同的大小。</span><span class="sxs-lookup"><span data-stu-id="244fd-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="244fd-114">方法返回的大小 `GetObjectSize` 不包括对象在垃圾回收堆上时可能出现的任何对齐填充。</span><span class="sxs-lookup"><span data-stu-id="244fd-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="244fd-115">如果使用 `GetObjectSize` 方法从对象到垃圾回收堆上的对象前进，请根据需要手动添加对齐填充。</span><span class="sxs-lookup"><span data-stu-id="244fd-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="244fd-116">在32位 Windows 上，COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用4字节对齐，COR_PRF_GC_LARGE_OBJECT_HEAP 使用8字节对齐。</span><span class="sxs-lookup"><span data-stu-id="244fd-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="244fd-117">在64位 Windows 上，对齐始终为8个字节。</span><span class="sxs-lookup"><span data-stu-id="244fd-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="244fd-118">要求</span><span class="sxs-lookup"><span data-stu-id="244fd-118">Requirements</span></span>  
 <span data-ttu-id="244fd-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="244fd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="244fd-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="244fd-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="244fd-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="244fd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="244fd-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="244fd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244fd-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="244fd-123">See also</span></span>

- [<span data-ttu-id="244fd-124">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="244fd-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
