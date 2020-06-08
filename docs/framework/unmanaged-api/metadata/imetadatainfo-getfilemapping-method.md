---
title: IMetaDataInfo::GetFileMapping 方法
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 5ef5d9ae3da4dff13a461162f0ba3466d3d8192c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501256"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="10dde-102">IMetaDataInfo::GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="10dde-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="10dde-103">获取映射文件的内存区域和映射类型。</span><span class="sxs-lookup"><span data-stu-id="10dde-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10dde-104">语法</span><span class="sxs-lookup"><span data-stu-id="10dde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10dde-105">参数</span><span class="sxs-lookup"><span data-stu-id="10dde-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="10dde-106">弄指向映射文件的开头的指针。</span><span class="sxs-lookup"><span data-stu-id="10dde-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="10dde-107">弄映射区域的大小。</span><span class="sxs-lookup"><span data-stu-id="10dde-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="10dde-108">如果 `pdwMappingType` 为 `fmFlat` ，则这是文件的大小。</span><span class="sxs-lookup"><span data-stu-id="10dde-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="10dde-109">弄指示映射类型的[CorFileMapping](corfilemapping-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="10dde-109">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="10dde-110">公共语言运行时（CLR）的当前实现始终返回 `fmFlat` 。</span><span class="sxs-lookup"><span data-stu-id="10dde-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="10dde-111">保留其他值以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="10dde-111">Other values are reserved for future use.</span></span> <span data-ttu-id="10dde-112">但是，应始终验证返回的值，因为在将来的版本或服务版本中可能会启用其他值。</span><span class="sxs-lookup"><span data-stu-id="10dde-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10dde-113">返回值</span><span class="sxs-lookup"><span data-stu-id="10dde-113">Return Value</span></span>  
  
|<span data-ttu-id="10dde-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10dde-114">HRESULT</span></span>|<span data-ttu-id="10dde-115">说明</span><span class="sxs-lookup"><span data-stu-id="10dde-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="10dde-116">所有输出都已填充。</span><span class="sxs-lookup"><span data-stu-id="10dde-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="10dde-117">将 NULL 作为参数值传递。</span><span class="sxs-lookup"><span data-stu-id="10dde-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="10dde-118">CLR 实现无法提供有关内存区域的信息。</span><span class="sxs-lookup"><span data-stu-id="10dde-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="10dde-119">这可能是由以下原因引起的：</span><span class="sxs-lookup"><span data-stu-id="10dde-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="10dde-120">-元数据范围已用 `ofWrite` 或标记打开 `ofCopyMemory` 。</span><span class="sxs-lookup"><span data-stu-id="10dde-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="10dde-121">-元数据范围在未带标志的情况下打开 `ofReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="10dde-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="10dde-122">- [IMetaDataDispenser：： OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md)方法仅用于打开文件的元数据部分。</span><span class="sxs-lookup"><span data-stu-id="10dde-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="10dde-123">-此文件不是可移植的可执行（PE）文件。</span><span class="sxs-lookup"><span data-stu-id="10dde-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="10dde-124">**注意：** 这些条件依赖于 CLR 实现，并且可能会在 CLR 的未来版本中减弱。</span><span class="sxs-lookup"><span data-stu-id="10dde-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10dde-125">注解</span><span class="sxs-lookup"><span data-stu-id="10dde-125">Remarks</span></span>  
 <span data-ttu-id="10dde-126">`ppvData`仅当基础元数据范围打开时，指向的内存才有效。</span><span class="sxs-lookup"><span data-stu-id="10dde-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="10dde-127">为了使此方法正常工作，当你通过调用[IMetaDataDispenser：： OpenScope](imetadatadispenser-openscope-method.md)方法将磁盘上的文件的元数据映射到内存中时，你必须指定 `ofReadOnly` 标志，并且不得指定 `ofWrite` 或 `ofCopyMemory` 标志。</span><span class="sxs-lookup"><span data-stu-id="10dde-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="10dde-128">每个作用域的文件映射类型选择特定于 CLR 的给定实现。</span><span class="sxs-lookup"><span data-stu-id="10dde-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="10dde-129">它不能由用户设置。</span><span class="sxs-lookup"><span data-stu-id="10dde-129">It cannot be set by the user.</span></span> <span data-ttu-id="10dde-130">CLR 的当前实现始终返回 `fmFlat` `pdwMappingType` ，但这可能会在将来版本的 clr 或未来版本的特定版本中发生更改。</span><span class="sxs-lookup"><span data-stu-id="10dde-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="10dde-131">应始终在中检查返回的值 `pdwMappingType` ，因为不同的类型将具有不同的布局和偏移量。</span><span class="sxs-lookup"><span data-stu-id="10dde-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="10dde-132">不支持为这三个参数中的任何一个传递 NULL。</span><span class="sxs-lookup"><span data-stu-id="10dde-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="10dde-133">方法返回 `E_INVALIDARG` ，但不填充任何输出。</span><span class="sxs-lookup"><span data-stu-id="10dde-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="10dde-134">忽略映射类型或区域大小可能会导致程序终止异常。</span><span class="sxs-lookup"><span data-stu-id="10dde-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10dde-135">要求</span><span class="sxs-lookup"><span data-stu-id="10dde-135">Requirements</span></span>  
 <span data-ttu-id="10dde-136">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10dde-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10dde-137">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="10dde-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10dde-138">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="10dde-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10dde-139">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10dde-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10dde-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10dde-140">See also</span></span>

- [<span data-ttu-id="10dde-141">IMetaDataInfo 接口</span><span class="sxs-lookup"><span data-stu-id="10dde-141">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="10dde-142">CorFileMapping 枚举</span><span class="sxs-lookup"><span data-stu-id="10dde-142">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
