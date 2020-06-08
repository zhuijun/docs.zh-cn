---
title: ICorProfilerInfo::GetModuleMetaData 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502946"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="8bf8b-102">ICorProfilerInfo::GetModuleMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="8bf8b-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="8bf8b-103">获取映射到指定模块的元数据接口实例。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf8b-104">语法</span><span class="sxs-lookup"><span data-stu-id="8bf8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf8b-105">参数</span><span class="sxs-lookup"><span data-stu-id="8bf8b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8bf8b-106">中接口实例将映射到的模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="8bf8b-107">中[CorOpenFlags](../metadata/coropenflags-enumeration.md)枚举的一个值，该值指定用于打开清单文件的模式。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="8bf8b-108">只有 `ofRead` 、 `ofWrite` 和 `ofNoTransform` 位有效。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="8bf8b-109">中将检索其实例的元数据接口的引用 ID （GUID）。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="8bf8b-110">有关接口列表，请参阅[元数据接口](../metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="8bf8b-111">弄指向元数据接口实例的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bf8b-112">注解</span><span class="sxs-lookup"><span data-stu-id="8bf8b-112">Remarks</span></span>  
 <span data-ttu-id="8bf8b-113">你可能要求在读/写模式下打开元数据，但这会导致程序的元数据执行速度变慢，因为对元数据所做的更改不会因为它们来自编译器而进行优化。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="8bf8b-114">某些模块（例如资源模块）没有元数据。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="8bf8b-115">在这些情况下， `GetModuleMetaData` 将返回的 HRESULT 值 S_FALSE，并在 \* 中返回 null `ppOut` 。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf8b-116">要求</span><span class="sxs-lookup"><span data-stu-id="8bf8b-116">Requirements</span></span>  
 <span data-ttu-id="8bf8b-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8bf8b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf8b-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bf8b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bf8b-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bf8b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bf8b-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf8b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf8b-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bf8b-121">See also</span></span>

- [<span data-ttu-id="8bf8b-122">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="8bf8b-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
