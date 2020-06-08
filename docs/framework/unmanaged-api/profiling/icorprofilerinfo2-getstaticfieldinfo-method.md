---
title: ICorProfilerInfo2::GetStaticFieldInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: e1dd6addd9053ffb6cf2ce23408673d8fca17cb5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496836"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="60acf-102">ICorProfilerInfo2::GetStaticFieldInfo 方法</span><span class="sxs-lookup"><span data-stu-id="60acf-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="60acf-103">获取一个值，该值指示应用于指定字段的静态类型。</span><span class="sxs-lookup"><span data-stu-id="60acf-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60acf-104">语法</span><span class="sxs-lookup"><span data-stu-id="60acf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60acf-105">参数</span><span class="sxs-lookup"><span data-stu-id="60acf-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="60acf-106">中在其中定义静态字段的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="60acf-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="60acf-107">中静态字段的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="60acf-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="60acf-108">弄一个指针，指向[COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md)枚举的值，该值指示指定字段是否为静态的，如果为，则为应用于该字段的静态类型。</span><span class="sxs-lookup"><span data-stu-id="60acf-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60acf-109">注解</span><span class="sxs-lookup"><span data-stu-id="60acf-109">Remarks</span></span>  
 <span data-ttu-id="60acf-110">此信息可用于确定要调用哪个函数以获取静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="60acf-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="60acf-111">探查器代码仍应检查静态字段的元数据，以确保它实际具有地址。</span><span class="sxs-lookup"><span data-stu-id="60acf-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="60acf-112">静态文本（即常量）仅存在于元数据中，并且没有地址。</span><span class="sxs-lookup"><span data-stu-id="60acf-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60acf-113">要求</span><span class="sxs-lookup"><span data-stu-id="60acf-113">Requirements</span></span>  
 <span data-ttu-id="60acf-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60acf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60acf-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60acf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60acf-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60acf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60acf-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60acf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60acf-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60acf-118">See also</span></span>

- [<span data-ttu-id="60acf-119">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="60acf-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="60acf-120">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="60acf-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
