---
title: ICorProfilerInfo3::GetStringLayout2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 51d5b2f2ee17cc177e3b0ddc7d2e0b82fd70063d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496368"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="c1143-102">ICorProfilerInfo3::GetStringLayout2 方法</span><span class="sxs-lookup"><span data-stu-id="c1143-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="c1143-103">获取有关字符串对象布局的信息。</span><span class="sxs-lookup"><span data-stu-id="c1143-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="c1143-104">此方法取代了[ICorProfilerInfo2：： GetStringLayout](icorprofilerinfo2-getstringlayout-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c1143-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1143-105">语法</span><span class="sxs-lookup"><span data-stu-id="c1143-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1143-106">参数</span><span class="sxs-lookup"><span data-stu-id="c1143-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="c1143-107">弄指向位置偏移量的指针，该位置相对于 `ObjectID` 指针存储字符串本身的长度。</span><span class="sxs-lookup"><span data-stu-id="c1143-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="c1143-108">长度存储为 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="c1143-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="c1143-109">弄指向缓冲区偏移量的指针，该指针相对于 `ObjectID` 存储宽字符字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="c1143-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1143-110">注解</span><span class="sxs-lookup"><span data-stu-id="c1143-110">Remarks</span></span>  
 <span data-ttu-id="c1143-111">字符串可以是，也可以不是以 null 结尾。</span><span class="sxs-lookup"><span data-stu-id="c1143-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1143-112">要求</span><span class="sxs-lookup"><span data-stu-id="c1143-112">Requirements</span></span>  
 <span data-ttu-id="c1143-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1143-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1143-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1143-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1143-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1143-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1143-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1143-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1143-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1143-117">See also</span></span>

- [<span data-ttu-id="c1143-118">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="c1143-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c1143-119">分析接口</span><span class="sxs-lookup"><span data-stu-id="c1143-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
