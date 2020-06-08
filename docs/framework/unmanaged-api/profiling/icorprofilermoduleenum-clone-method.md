---
title: ICorProfilerModuleEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: ccbb051ac30fb25199ce12c16fff74bb0b9944fa
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495081"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="16d8a-102">ICorProfilerModuleEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="16d8a-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="16d8a-103">获取一个接口指针，该指针指向此[ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md)接口的副本。</span><span class="sxs-lookup"><span data-stu-id="16d8a-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16d8a-104">语法</span><span class="sxs-lookup"><span data-stu-id="16d8a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16d8a-105">参数</span><span class="sxs-lookup"><span data-stu-id="16d8a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="16d8a-106">弄指向接口指针的指针，该指针指向此[ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md)接口的副本。</span><span class="sxs-lookup"><span data-stu-id="16d8a-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="16d8a-107">枚举器的副本与此枚举器分别维护自己的枚举状态。</span><span class="sxs-lookup"><span data-stu-id="16d8a-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="16d8a-108">但是，副本的初始光标位置与此枚举器的当前游标位置相同。</span><span class="sxs-lookup"><span data-stu-id="16d8a-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d8a-109">要求</span><span class="sxs-lookup"><span data-stu-id="16d8a-109">Requirements</span></span>  
 <span data-ttu-id="16d8a-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16d8a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d8a-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16d8a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16d8a-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16d8a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16d8a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d8a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d8a-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16d8a-114">See also</span></span>

- [<span data-ttu-id="16d8a-115">ICorProfilerModuleEnum 接口</span><span class="sxs-lookup"><span data-stu-id="16d8a-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="16d8a-116">分析接口</span><span class="sxs-lookup"><span data-stu-id="16d8a-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
