---
title: ICorProfilerFunctionControl::SetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: a6b24fd59a183a4a59b117663772417d55cc67db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503130"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="53f03-102">ICorProfilerFunctionControl::SetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="53f03-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="53f03-103">替换方法的公共中间语言 (CIL) 主体。</span><span class="sxs-lookup"><span data-stu-id="53f03-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f03-104">语法</span><span class="sxs-lookup"><span data-stu-id="53f03-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53f03-105">参数</span><span class="sxs-lookup"><span data-stu-id="53f03-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="53f03-106">[in] 新 CIL 的总体大小，包括标头和主体之后的任何结构。</span><span class="sxs-lookup"><span data-stu-id="53f03-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="53f03-107">[in] 一个指向新 CIL 的标头的指针。</span><span class="sxs-lookup"><span data-stu-id="53f03-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53f03-108">返回值</span><span class="sxs-lookup"><span data-stu-id="53f03-108">Return Value</span></span>  
 <span data-ttu-id="53f03-109">此方法会返回以下特定的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="53f03-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="53f03-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53f03-110">HRESULT</span></span>|<span data-ttu-id="53f03-111">说明</span><span class="sxs-lookup"><span data-stu-id="53f03-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53f03-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="53f03-112">S_OK</span></span>|<span data-ttu-id="53f03-113">替换成功。</span><span class="sxs-lookup"><span data-stu-id="53f03-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53f03-114">注解</span><span class="sxs-lookup"><span data-stu-id="53f03-114">Remarks</span></span>  
 <span data-ttu-id="53f03-115">与[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法不同， `SetILFunctionBody` 方法管理新 CIL 主体所需的内存。</span><span class="sxs-lookup"><span data-stu-id="53f03-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="53f03-116">这意味着，无需通过使用[IMethodMalloc](imethodmalloc-interface.md)接口来分配探查器提供的 CIL 主体，也不必在特定范围内进行分配。</span><span class="sxs-lookup"><span data-stu-id="53f03-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="53f03-117">它可在任何堆上进行分配。</span><span class="sxs-lookup"><span data-stu-id="53f03-117">It can be allocated on any heap.</span></span> <span data-ttu-id="53f03-118">探查器可以在返回后释放用于其 CIL 体的内存 `SetILFunctionBody` 。</span><span class="sxs-lookup"><span data-stu-id="53f03-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53f03-119">要求</span><span class="sxs-lookup"><span data-stu-id="53f03-119">Requirements</span></span>  
 <span data-ttu-id="53f03-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53f03-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53f03-121">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53f03-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53f03-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53f03-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53f03-123">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53f03-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f03-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53f03-124">See also</span></span>

- [<span data-ttu-id="53f03-125">ICorProfilerFunctionControl 接口</span><span class="sxs-lookup"><span data-stu-id="53f03-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
