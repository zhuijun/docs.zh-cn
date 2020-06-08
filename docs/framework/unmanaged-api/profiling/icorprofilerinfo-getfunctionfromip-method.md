---
title: ICorProfilerInfo::GetFunctionFromIP 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
ms.openlocfilehash: 339c5db1610a3cf087085ce19fc663436d9c4ec1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498305"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="d88a5-102">ICorProfilerInfo::GetFunctionFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="d88a5-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="d88a5-103">将托管代码指令指针映射到 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="d88a5-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88a5-104">语法</span><span class="sxs-lookup"><span data-stu-id="d88a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d88a5-105">参数</span><span class="sxs-lookup"><span data-stu-id="d88a5-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="d88a5-106">\[in] 托管代码中的指令指针。</span><span class="sxs-lookup"><span data-stu-id="d88a5-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="d88a5-107">\[out] 返回的函数 ID。</span><span class="sxs-lookup"><span data-stu-id="d88a5-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="d88a5-108">要求</span><span class="sxs-lookup"><span data-stu-id="d88a5-108">Requirements</span></span>  
 <span data-ttu-id="d88a5-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d88a5-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d88a5-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d88a5-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d88a5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d88a5-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d88a5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88a5-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d88a5-113">See also</span></span>

- [<span data-ttu-id="d88a5-114">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="d88a5-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
