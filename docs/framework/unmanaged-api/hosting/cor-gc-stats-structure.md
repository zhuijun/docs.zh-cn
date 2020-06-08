---
title: COR_GC_STATS 结构
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501659"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="44d77-102">COR_GC_STATS 结构</span><span class="sxs-lookup"><span data-stu-id="44d77-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="44d77-103">提供有关公共语言运行时（CLR）的垃圾回收机制的统计信息。</span><span class="sxs-lookup"><span data-stu-id="44d77-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d77-104">语法</span><span class="sxs-lookup"><span data-stu-id="44d77-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="44d77-105">成员</span><span class="sxs-lookup"><span data-stu-id="44d77-105">Members</span></span>  
  
|<span data-ttu-id="44d77-106">成员</span><span class="sxs-lookup"><span data-stu-id="44d77-106">Member</span></span>|<span data-ttu-id="44d77-107">描述</span><span class="sxs-lookup"><span data-stu-id="44d77-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="44d77-108">指示应计算并返回的字段值。</span><span class="sxs-lookup"><span data-stu-id="44d77-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="44d77-109">指示外部请求强制执行的垃圾回收数。</span><span class="sxs-lookup"><span data-stu-id="44d77-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="44d77-110">指示为每个代执行的垃圾回收数。</span><span class="sxs-lookup"><span data-stu-id="44d77-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="44d77-111">所有堆中提交的总千字节数。</span><span class="sxs-lookup"><span data-stu-id="44d77-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="44d77-112">所有堆中保留的总千字节数。</span><span class="sxs-lookup"><span data-stu-id="44d77-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="44d77-113">代零堆的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="44d77-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="44d77-114">第一代堆的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="44d77-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="44d77-115">第二代堆的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="44d77-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="44d77-116">大型对象堆的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="44d77-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="44d77-117">从零代升级到第1代的对象的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="44d77-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="44d77-118">从第一代升级到第二代的对象的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="44d77-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44d77-119">注解</span><span class="sxs-lookup"><span data-stu-id="44d77-119">Remarks</span></span>  
 <span data-ttu-id="44d77-120">[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法要求将 `Flags` 结构的字段 `COR_GC_STATS` 设置为一个或多个[COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)枚举的值，以指定要设置的统计信息。</span><span class="sxs-lookup"><span data-stu-id="44d77-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="44d77-121">下表将此结构提供的统计信息映射到两个[COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)枚举值 `COR_GC_COUNTS` 和 `COR_GC_MEMORYUSAGE` 。</span><span class="sxs-lookup"><span data-stu-id="44d77-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="44d77-122">指定者 COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="44d77-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="44d77-123">指定者 COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="44d77-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="44d77-124">用法的示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="44d77-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="44d77-125">要求</span><span class="sxs-lookup"><span data-stu-id="44d77-125">Requirements</span></span>  
 <span data-ttu-id="44d77-126">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44d77-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d77-127">**标头：** GCHost .idl</span><span class="sxs-lookup"><span data-stu-id="44d77-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="44d77-128">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="44d77-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44d77-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d77-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d77-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44d77-130">See also</span></span>

- [<span data-ttu-id="44d77-131">承载结构</span><span class="sxs-lookup"><span data-stu-id="44d77-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="44d77-132">自动内存管理</span><span class="sxs-lookup"><span data-stu-id="44d77-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="44d77-133">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="44d77-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
