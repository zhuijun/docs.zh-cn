---
title: ICorProfilerInfo7：： ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: 6732457220d795bbf8ae54277ef9f5c07cf96359
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495354"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="3f54c-102">ICorProfilerInfo7：： ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="3f54c-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="3f54c-103">[仅在 .NET Framework 4.6.1 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="3f54c-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3f54c-104">从内存中的符号流中读取字节。</span><span class="sxs-lookup"><span data-stu-id="3f54c-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f54c-105">语法</span><span class="sxs-lookup"><span data-stu-id="3f54c-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f54c-106">参数</span><span class="sxs-lookup"><span data-stu-id="3f54c-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3f54c-107">中包含内存中流的模块的标识符。</span><span class="sxs-lookup"><span data-stu-id="3f54c-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="3f54c-108">中内存中流中的偏移量，从此处开始读取字节。</span><span class="sxs-lookup"><span data-stu-id="3f54c-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="3f54c-109">弄指向数据将复制到的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="3f54c-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="3f54c-110">缓冲区应有 `countSymbolBytes` 可用空间。</span><span class="sxs-lookup"><span data-stu-id="3f54c-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="3f54c-111">中要复制的字节数。</span><span class="sxs-lookup"><span data-stu-id="3f54c-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="3f54c-112">弄当该方法返回时，包含所读取的实际字节数。</span><span class="sxs-lookup"><span data-stu-id="3f54c-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f54c-113">返回值</span><span class="sxs-lookup"><span data-stu-id="3f54c-113">Return Value</span></span>  
 <span data-ttu-id="3f54c-114">`S_OK`如果读取的字节数为非零，则为。</span><span class="sxs-lookup"><span data-stu-id="3f54c-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="3f54c-115">`CORPROF_E_MODULE_IS_DYNAMIC`如果该模块是使用创建的，则为 <xref:System.Reflection.Emit> 。</span><span class="sxs-lookup"><span data-stu-id="3f54c-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f54c-116">注解</span><span class="sxs-lookup"><span data-stu-id="3f54c-116">Remarks</span></span>  
 <span data-ttu-id="3f54c-117">此 `ReadInMemorySymbols` 方法尝试 `countSymbolBytes` 从 `symbolsReadOffset` 内存中流内的偏移量开始读取数据。</span><span class="sxs-lookup"><span data-stu-id="3f54c-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="3f54c-118">将数据复制到 `pSymbolBytes` ，该数据应具有 `countSymbolBytes` 可用空间。</span><span class="sxs-lookup"><span data-stu-id="3f54c-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="3f54c-119">`pCountSymbolsBytesRead`包含读取的实际字节数， `countSymbolBytes` 如果已到达流的末尾，则可以小于。</span><span class="sxs-lookup"><span data-stu-id="3f54c-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f54c-120">当前实现不支持反射。发出。</span><span class="sxs-lookup"><span data-stu-id="3f54c-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="3f54c-121">如果该模块是使用反射创建的，则该方法返回 `CORPROF_E_MODULE_IS_DYNAMIC` 。</span><span class="sxs-lookup"><span data-stu-id="3f54c-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f54c-122">要求</span><span class="sxs-lookup"><span data-stu-id="3f54c-122">Requirements</span></span>  
 <span data-ttu-id="3f54c-123">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f54c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f54c-124">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f54c-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f54c-125">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f54c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f54c-126">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f54c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f54c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f54c-127">See also</span></span>

- [<span data-ttu-id="3f54c-128">ICorProfilerInfo7 接口</span><span class="sxs-lookup"><span data-stu-id="3f54c-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
