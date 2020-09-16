---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 121ed0401628193f6e2fe632a124c08aad7bd1b4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551434"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="ed6cc-102">ICorProfilerInfo10：： SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="ed6cc-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="ed6cc-103">挂起运行时，而不执行 GC。</span><span class="sxs-lookup"><span data-stu-id="ed6cc-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed6cc-104">语法</span><span class="sxs-lookup"><span data-stu-id="ed6cc-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="ed6cc-105">要求</span><span class="sxs-lookup"><span data-stu-id="ed6cc-105">Requirements</span></span>

<span data-ttu-id="ed6cc-106">**平台：** 请参阅 [支持 .Net Core 的操作系统](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="ed6cc-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="ed6cc-107">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed6cc-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ed6cc-108">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed6cc-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ed6cc-109">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed6cc-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ed6cc-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed6cc-110">See also</span></span>

- [<span data-ttu-id="ed6cc-111">ICorProfilerInfo10 接口</span><span class="sxs-lookup"><span data-stu-id="ed6cc-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
