---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO 结构
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 861b31e5621e9a7b40403d249c6a5c8c4ac25db8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501035"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="fee21-102">COR_PRF_ASSEMBLY_REFERENCE_INFO 结构</span><span class="sxs-lookup"><span data-stu-id="fee21-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="fee21-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="fee21-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fee21-104">向公共语言运行时提供有关在执行程序集引用闭包审核时应考虑的程序集引用的信息。</span><span class="sxs-lookup"><span data-stu-id="fee21-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee21-105">语法</span><span class="sxs-lookup"><span data-stu-id="fee21-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="fee21-106">成员</span><span class="sxs-lookup"><span data-stu-id="fee21-106">Members</span></span>  
  
|<span data-ttu-id="fee21-107">成员</span><span class="sxs-lookup"><span data-stu-id="fee21-107">Member</span></span>|<span data-ttu-id="fee21-108">描述</span><span class="sxs-lookup"><span data-stu-id="fee21-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="fee21-109">指向程序集的公钥或标记的指针。</span><span class="sxs-lookup"><span data-stu-id="fee21-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="fee21-110">公钥或标记中的字节数。</span><span class="sxs-lookup"><span data-stu-id="fee21-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="fee21-111">所引用的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="fee21-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="fee21-112">指向程序集的元数据的指针。</span><span class="sxs-lookup"><span data-stu-id="fee21-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="fee21-113">指向哈希二进制大对象 (BLOB) 的指针。</span><span class="sxs-lookup"><span data-stu-id="fee21-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="fee21-114">哈希 BLOB 中的字节数。</span><span class="sxs-lookup"><span data-stu-id="fee21-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="fee21-115">程序集的标志。</span><span class="sxs-lookup"><span data-stu-id="fee21-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee21-116">注解</span><span class="sxs-lookup"><span data-stu-id="fee21-116">Remarks</span></span>  
 <span data-ttu-id="fee21-117">当 `COR_PRF_EX_CLAUSE_INFO` 结构声明在执行程序集引用闭包审核时公共语言运行时应考虑的附加程序集引用时，该结构将由探查器进行填充。</span><span class="sxs-lookup"><span data-stu-id="fee21-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="fee21-118">如果探查器注册了[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回调方法，则运行时将传递要加载的程序集的路径和名称以及指向该方法的指向[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)接口对象的指针。</span><span class="sxs-lookup"><span data-stu-id="fee21-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="fee21-119">然后，探查器可以[ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) `COR_PRF_ASSEMBLY_REFERENCE_INFO` 为它计划从[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回调中指定的程序集引用的每个目标程序集调用 ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference 方法和一个对象。</span><span class="sxs-lookup"><span data-stu-id="fee21-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee21-120">要求</span><span class="sxs-lookup"><span data-stu-id="fee21-120">Requirements</span></span>  
 <span data-ttu-id="fee21-121">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fee21-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee21-122">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fee21-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fee21-123">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fee21-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee21-124">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee21-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee21-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fee21-125">See also</span></span>

- [<span data-ttu-id="fee21-126">分析结构</span><span class="sxs-lookup"><span data-stu-id="fee21-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="fee21-127">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="fee21-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="fee21-128">AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="fee21-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
