---
title: ICorProfilerInfo::GetCodeInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: eb6efc738b270f8f76d7130a12af4927fb6220ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498357"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="10234-102">ICorProfilerInfo::GetCodeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="10234-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="10234-103">获取与指定函数 ID 关联的本机代码的范围。</span><span class="sxs-lookup"><span data-stu-id="10234-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="10234-104">此方法已过时。</span><span class="sxs-lookup"><span data-stu-id="10234-104">This method is obsolete.</span></span> <span data-ttu-id="10234-105">改为使用[ICorProfilerInfo2：： GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="10234-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10234-106">语法</span><span class="sxs-lookup"><span data-stu-id="10234-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10234-107">参数</span><span class="sxs-lookup"><span data-stu-id="10234-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="10234-108">[in] 与本机代码关联的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="10234-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="10234-109">[out] 指向组成该函数本机代码的字节数组的指针。</span><span class="sxs-lookup"><span data-stu-id="10234-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="10234-110">[out] 指向以字节为单位指定本机代码大小的整数的指针。</span><span class="sxs-lookup"><span data-stu-id="10234-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10234-111">注解</span><span class="sxs-lookup"><span data-stu-id="10234-111">Remarks</span></span>  
 <span data-ttu-id="10234-112">为了优化性能，.NET Framework 2.0 版中的运行时将函数的预编译本机代码拆分为多个部分。</span><span class="sxs-lookup"><span data-stu-id="10234-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="10234-113">因此，`GetCodeInfo` 方法在.NET Framework 2.0 中已过时，因为它无法处理函数的本机代码的范围。</span><span class="sxs-lookup"><span data-stu-id="10234-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="10234-114">探查器应切换为使用更常规的 `ICorProfilerInfo2::GetCodeInfo2` 方法。</span><span class="sxs-lookup"><span data-stu-id="10234-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="10234-115">此函数使用调用方分配的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="10234-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10234-116">要求</span><span class="sxs-lookup"><span data-stu-id="10234-116">Requirements</span></span>  
 <span data-ttu-id="10234-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10234-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10234-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10234-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10234-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10234-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10234-120">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="10234-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10234-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10234-121">See also</span></span>

- [<span data-ttu-id="10234-122">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="10234-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="10234-123">分析接口</span><span class="sxs-lookup"><span data-stu-id="10234-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="10234-124">分析</span><span class="sxs-lookup"><span data-stu-id="10234-124">Profiling</span></span>](index.md)
