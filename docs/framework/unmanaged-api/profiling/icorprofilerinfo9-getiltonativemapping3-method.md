---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 14391a0fe046b44aedca1da2bc42c7d962e1a5e7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541273"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="cdbd8-102">ICorProfilerInfo9：： GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="cdbd8-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="cdbd8-103">给定本机代码起始地址，返回此实时编译版本的代码的本机到 IL 映射信息。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="cdbd8-104">语法</span><span class="sxs-lookup"><span data-stu-id="cdbd8-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="cdbd8-105">参数</span><span class="sxs-lookup"><span data-stu-id="cdbd8-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="cdbd8-106">\[in] 指向本机函数开头的指针。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="cdbd8-107">\[in] 数组的最大大小 `map` 。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="cdbd8-108">\[out] 可用 COR_DEBUG_IL_TO_NATIVE_MAP 结构的总数。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="cdbd8-109">\[out] [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) 结构的数组，其中每个结构都指定了偏移量。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="cdbd8-110">`GetILToNativeMapping3` 方法返回后，`map` 将包含部分或全部 `COR_DEBUG_IL_TO_NATIVE_MAP` 结构。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdbd8-111">备注</span><span class="sxs-lookup"><span data-stu-id="cdbd8-111">Remarks</span></span>

<span data-ttu-id="cdbd8-112">当启用分层编译时，一个方法可能有多个本机代码体。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="cdbd8-113">[ICorProfilerInfo9：： GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) 将返回所有本机代码正文的开始地址。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdbd8-114">要求</span><span class="sxs-lookup"><span data-stu-id="cdbd8-114">Requirements</span></span>

<span data-ttu-id="cdbd8-115">**平台：** 请参阅 [支持 .Net Core 的操作系统](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="cdbd8-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="cdbd8-116">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdbd8-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cdbd8-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdbd8-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cdbd8-118">**.NET Framework 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbd8-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cdbd8-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdbd8-119">See also</span></span>

- [<span data-ttu-id="cdbd8-120">ICorProfilerInfo9 接口</span><span class="sxs-lookup"><span data-stu-id="cdbd8-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
