---
title: ICorProfilerInfo::GetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502998"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="2fb29-102">ICorProfilerInfo::GetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="2fb29-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="2fb29-103">获取一个指针，该指针指向 Microsoft 中间语言（MSIL）代码中的方法的正文（从其标头开始）。</span><span class="sxs-lookup"><span data-stu-id="2fb29-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb29-104">语法</span><span class="sxs-lookup"><span data-stu-id="2fb29-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fb29-105">参数</span><span class="sxs-lookup"><span data-stu-id="2fb29-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2fb29-106">中函数所在模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="2fb29-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="2fb29-107">中方法的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="2fb29-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="2fb29-108">弄指向方法的标头的指针。</span><span class="sxs-lookup"><span data-stu-id="2fb29-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="2fb29-109">弄一个整数，指定方法的大小。</span><span class="sxs-lookup"><span data-stu-id="2fb29-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb29-110">注解</span><span class="sxs-lookup"><span data-stu-id="2fb29-110">Remarks</span></span>  
 <span data-ttu-id="2fb29-111">方法的作用域由其所在的模块确定。</span><span class="sxs-lookup"><span data-stu-id="2fb29-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="2fb29-112">由于 `GetILFunctionBody` 方法旨在在公共语言运行时（CLR）加载 MSIL 代码之前为其提供访问权限，因此它使用方法的元数据标记来查找所需的实例。</span><span class="sxs-lookup"><span data-stu-id="2fb29-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="2fb29-113">`GetILFunctionBody`如果 `methodId` 指向不包含任何 MSIL 代码的方法（如抽象方法或平台调用（PInvoke）方法），则可以返回 CORPROF_E_FUNCTION_NOT_IL HRESULT。</span><span class="sxs-lookup"><span data-stu-id="2fb29-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb29-114">要求</span><span class="sxs-lookup"><span data-stu-id="2fb29-114">Requirements</span></span>  
 <span data-ttu-id="2fb29-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2fb29-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb29-116">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2fb29-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2fb29-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fb29-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fb29-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb29-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb29-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fb29-119">See also</span></span>

- [<span data-ttu-id="2fb29-120">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="2fb29-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
