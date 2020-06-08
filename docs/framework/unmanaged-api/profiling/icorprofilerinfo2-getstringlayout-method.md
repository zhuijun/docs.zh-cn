---
title: ICorProfilerInfo2::GetStringLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 257cf24fa476c75d6ec949e17a5b83fc015b8d43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496773"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="058fc-102">ICorProfilerInfo2::GetStringLayout 方法</span><span class="sxs-lookup"><span data-stu-id="058fc-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="058fc-103">获取有关字符串对象布局的信息。</span><span class="sxs-lookup"><span data-stu-id="058fc-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="058fc-104">此方法在 .NET Framework 4 中已弃用，并且被[ICorProfilerInfo3：： GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md)方法取代。</span><span class="sxs-lookup"><span data-stu-id="058fc-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="058fc-105">语法</span><span class="sxs-lookup"><span data-stu-id="058fc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="058fc-106">参数</span><span class="sxs-lookup"><span data-stu-id="058fc-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="058fc-107">弄一个指针， `ObjectID` 它指向存储字符串长度的相对于指针的位置偏移量。</span><span class="sxs-lookup"><span data-stu-id="058fc-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="058fc-108">长度存储为 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="058fc-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="058fc-109">此参数返回字符串本身的长度，而不是缓冲区的长度。</span><span class="sxs-lookup"><span data-stu-id="058fc-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="058fc-110">缓冲区的长度不再可用。</span><span class="sxs-lookup"><span data-stu-id="058fc-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="058fc-111">弄指向位置偏移量的指针，该位置相对于 `ObjectID` 指针存储字符串本身的长度。</span><span class="sxs-lookup"><span data-stu-id="058fc-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="058fc-112">长度存储为 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="058fc-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="058fc-113">弄一个指针， `ObjectID` 它指向存储宽字符字符串的缓冲区相对于指针的偏移量。</span><span class="sxs-lookup"><span data-stu-id="058fc-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="058fc-114">注解</span><span class="sxs-lookup"><span data-stu-id="058fc-114">Remarks</span></span>  
 <span data-ttu-id="058fc-115">`GetStringLayout`方法获取 `ObjectID` 在其中存储下列位置的相对于指针的偏移量：</span><span class="sxs-lookup"><span data-stu-id="058fc-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="058fc-116">字符串缓冲区的长度。</span><span class="sxs-lookup"><span data-stu-id="058fc-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="058fc-117">字符串本身的长度。</span><span class="sxs-lookup"><span data-stu-id="058fc-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="058fc-118">包含宽字符实际字符串的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="058fc-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="058fc-119">字符串可以以 null 结尾。</span><span class="sxs-lookup"><span data-stu-id="058fc-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="058fc-120">要求</span><span class="sxs-lookup"><span data-stu-id="058fc-120">Requirements</span></span>  
 <span data-ttu-id="058fc-121">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="058fc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="058fc-122">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="058fc-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="058fc-123">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="058fc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="058fc-124">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="058fc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="058fc-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="058fc-125">See also</span></span>

- [<span data-ttu-id="058fc-126">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="058fc-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="058fc-127">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="058fc-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
