---
title: ICorProfilerInfo3::EnumModules 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 85adf2dbdbb8c02192a9017bc4f664274a08ee24
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496576"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="9287d-102">ICorProfilerInfo3::EnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="9287d-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="9287d-103">返回一个枚举器，此枚举器提供方法以按顺序循环访问加载到应用程序的托管模块集合。</span><span class="sxs-lookup"><span data-stu-id="9287d-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9287d-104">语法</span><span class="sxs-lookup"><span data-stu-id="9287d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9287d-105">参数</span><span class="sxs-lookup"><span data-stu-id="9287d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9287d-106">弄指向[ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md)接口的指针。</span><span class="sxs-lookup"><span data-stu-id="9287d-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9287d-107">备注</span><span class="sxs-lookup"><span data-stu-id="9287d-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9287d-108">要求</span><span class="sxs-lookup"><span data-stu-id="9287d-108">Requirements</span></span>  
 <span data-ttu-id="9287d-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9287d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9287d-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9287d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9287d-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9287d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9287d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9287d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9287d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9287d-113">See also</span></span>

- [<span data-ttu-id="9287d-114">ICorProfilerFunctionEnum 接口</span><span class="sxs-lookup"><span data-stu-id="9287d-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="9287d-115">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="9287d-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9287d-116">分析接口</span><span class="sxs-lookup"><span data-stu-id="9287d-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9287d-117">分析</span><span class="sxs-lookup"><span data-stu-id="9287d-117">Profiling</span></span>](index.md)
