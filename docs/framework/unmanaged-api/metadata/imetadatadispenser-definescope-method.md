---
title: IMetaDataDispenser::DefineScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 12a32b5d2f0647ea2d9b696d08d6644e30be0c65
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501347"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="603db-102">IMetaDataDispenser::DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="603db-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="603db-103">在内存中创建一个新区域，您可以在其中创建新的元数据。</span><span class="sxs-lookup"><span data-stu-id="603db-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603db-104">语法</span><span class="sxs-lookup"><span data-stu-id="603db-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="603db-105">参数</span><span class="sxs-lookup"><span data-stu-id="603db-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="603db-106">中要创建的元数据结构版本的 CLSID。</span><span class="sxs-lookup"><span data-stu-id="603db-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="603db-107">对于 .NET Framework 版本2.0，此值必须为 CLSID_CorMetaDataRuntime。</span><span class="sxs-lookup"><span data-stu-id="603db-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="603db-108">中指定选项的标志。</span><span class="sxs-lookup"><span data-stu-id="603db-108">[in] Flags that specify options.</span></span> <span data-ttu-id="603db-109">对于 .NET Framework 2.0，此值必须为零。</span><span class="sxs-lookup"><span data-stu-id="603db-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="603db-110">中要返回的所需元数据接口的 IID;调用方将使用接口创建新的元数据。</span><span class="sxs-lookup"><span data-stu-id="603db-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="603db-111">的值 `riid` 必须指定一个 "发出" 接口。</span><span class="sxs-lookup"><span data-stu-id="603db-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="603db-112">有效值为 IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit 或 IID_IMetaDataEmit2。</span><span class="sxs-lookup"><span data-stu-id="603db-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="603db-113">弄指向返回的接口的指针。</span><span class="sxs-lookup"><span data-stu-id="603db-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="603db-114">注解</span><span class="sxs-lookup"><span data-stu-id="603db-114">Remarks</span></span>  
 <span data-ttu-id="603db-115">`DefineScope`创建一组内存中的元数据表，为元数据生成唯一的 GUID （模块版本标识符或 MVID），并在模块表中为发出的编译单元创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="603db-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="603db-116">根据需要，可以使用[IMetaDataEmit：： SetModuleProps](imetadataemit-setmoduleprops-method.md)或[IMetaDataEmit：:D efinecustomattribute](imetadataemit-definecustomattribute-method.md)方法，将属性作为一个整体附加到元数据范围。</span><span class="sxs-lookup"><span data-stu-id="603db-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="603db-117">要求</span><span class="sxs-lookup"><span data-stu-id="603db-117">Requirements</span></span>  
 <span data-ttu-id="603db-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="603db-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="603db-119">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="603db-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="603db-120">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="603db-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="603db-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="603db-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603db-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="603db-122">See also</span></span>

- [<span data-ttu-id="603db-123">IMetaDataDispenser 接口</span><span class="sxs-lookup"><span data-stu-id="603db-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="603db-124">IMetaDataDispenserEx 接口</span><span class="sxs-lookup"><span data-stu-id="603db-124">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="603db-125">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="603db-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="603db-126">IMetaDataEmit 接口</span><span class="sxs-lookup"><span data-stu-id="603db-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="603db-127">IMetaDataEmit2 接口</span><span class="sxs-lookup"><span data-stu-id="603db-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
