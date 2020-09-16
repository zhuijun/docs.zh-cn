---
title: ILCodeKind 枚举
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: b9d27c3e3cd42039aeefcb517ecc81eadeb5c183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557419"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="8c14c-102">ILCodeKind 枚举</span><span class="sxs-lookup"><span data-stu-id="8c14c-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="8c14c-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="8c14c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8c14c-104">提供用于指定调试器是否能够访问在探查器 ReJIT 检测中添加的局部变量或代码的值。</span><span class="sxs-lookup"><span data-stu-id="8c14c-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c14c-105">语法</span><span class="sxs-lookup"><span data-stu-id="8c14c-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="8c14c-106">成员</span><span class="sxs-lookup"><span data-stu-id="8c14c-106">Members</span></span>  
  
|<span data-ttu-id="8c14c-107">成员名称</span><span class="sxs-lookup"><span data-stu-id="8c14c-107">Member name</span></span>|<span data-ttu-id="8c14c-108">说明</span><span class="sxs-lookup"><span data-stu-id="8c14c-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="8c14c-109">调试器无法访问 ReJIT 检测的信息。</span><span class="sxs-lookup"><span data-stu-id="8c14c-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="8c14c-110">调试器可以访问 ReJIT 检测的信息。</span><span class="sxs-lookup"><span data-stu-id="8c14c-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c14c-111">备注</span><span class="sxs-lookup"><span data-stu-id="8c14c-111">Remarks</span></span>  
 <span data-ttu-id="8c14c-112">枚举的成员 `ILCodeKind` 可以传递给 [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) 和 [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) 方法，以确定调试器是否可以访问在探查器 ReJIT 检测中添加的变量，以及如何访问 [GetCodeEx](icordebugilframe4-getcodeex-method.md) 方法，以确定调试器是否可以访问检测的 IL。</span><span class="sxs-lookup"><span data-stu-id="8c14c-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c14c-113">要求</span><span class="sxs-lookup"><span data-stu-id="8c14c-113">Requirements</span></span>  
 <span data-ttu-id="8c14c-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c14c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c14c-115">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c14c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c14c-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c14c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c14c-117">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c14c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c14c-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="8c14c-118">See also</span></span>

- [<span data-ttu-id="8c14c-119">调试枚举</span><span class="sxs-lookup"><span data-stu-id="8c14c-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="8c14c-120">ICorDebugILFrame4 接口</span><span class="sxs-lookup"><span data-stu-id="8c14c-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="8c14c-121">ReJIT：操作方法指南</span><span class="sxs-lookup"><span data-stu-id="8c14c-121">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
