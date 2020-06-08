---
title: ICorProfilerInfo7：： GetInMemorySymbolsLength 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 43d6bdeae5f522bd73b0bdf3a5c403ec69ee384c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495433"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="e9210-102">ICorProfilerInfo7：： GetInMemorySymbolsLength 方法</span><span class="sxs-lookup"><span data-stu-id="e9210-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="e9210-103">[仅在 .NET Framework 4.6.1 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="e9210-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="e9210-104">返回内存中符号流的长度。</span><span class="sxs-lookup"><span data-stu-id="e9210-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9210-105">语法</span><span class="sxs-lookup"><span data-stu-id="e9210-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9210-106">参数</span><span class="sxs-lookup"><span data-stu-id="e9210-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="e9210-107">中包含内存中流的模块的标识符。</span><span class="sxs-lookup"><span data-stu-id="e9210-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="e9210-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="e9210-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="e9210-109">弄一个指向 `DWORD` 值的指针，当该方法返回时，将包含流的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e9210-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9210-110">返回值</span><span class="sxs-lookup"><span data-stu-id="e9210-110">Return Value</span></span>  
 <span data-ttu-id="e9210-111">`S_OK`如果可以确定内存流的长度（即使它为零（0）），则方法将返回。</span><span class="sxs-lookup"><span data-stu-id="e9210-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="e9210-112">`CORPROF_E_MODULE_IS_DYNAMIC`如果该方法是使用创建的，则该方法返回 <xref:System.Reflection.Emit?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e9210-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9210-113">注解</span><span class="sxs-lookup"><span data-stu-id="e9210-113">Remarks</span></span>  
 <span data-ttu-id="e9210-114">如果模块有内存中符号，则流的长度将被置于中 `pCountSymbolBytes` 。</span><span class="sxs-lookup"><span data-stu-id="e9210-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="e9210-115">如果模块没有内存中符号，则为 `*pCountSymbolBytes = 0` 。</span><span class="sxs-lookup"><span data-stu-id="e9210-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9210-116">当前实现不支持反射。发出。</span><span class="sxs-lookup"><span data-stu-id="e9210-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="e9210-117">如果该模块是使用反射创建的，则该方法返回 `CORPROF_E_MODULE_IS_DYNAMIC` 。</span><span class="sxs-lookup"><span data-stu-id="e9210-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9210-118">要求</span><span class="sxs-lookup"><span data-stu-id="e9210-118">Requirements</span></span>  
 <span data-ttu-id="e9210-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9210-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9210-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9210-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9210-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9210-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9210-122">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9210-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9210-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9210-123">See also</span></span>

- [<span data-ttu-id="e9210-124">ICorProfilerInfo7 接口</span><span class="sxs-lookup"><span data-stu-id="e9210-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
