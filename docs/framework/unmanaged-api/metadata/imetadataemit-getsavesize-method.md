---
title: IMetaDataEmit::GetSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 0a283c837e23ab1aafd3545df1dfe8a267de0557
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501282"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="4da96-102">IMetaDataEmit::GetSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="4da96-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="4da96-103">获取当前范围内的程序集和它的元数据的预计二进制大小。</span><span class="sxs-lookup"><span data-stu-id="4da96-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da96-104">语法</span><span class="sxs-lookup"><span data-stu-id="4da96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4da96-105">参数</span><span class="sxs-lookup"><span data-stu-id="4da96-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="4da96-106">中[CorSaveSize](corsavesize-enumeration.md)枚举的一个值，该值指定是获取准确大小还是近似大小。</span><span class="sxs-lookup"><span data-stu-id="4da96-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="4da96-107">只有三个值有效： cssAccurate、cssQuick 和 cssDiscardTransientCAs：</span><span class="sxs-lookup"><span data-stu-id="4da96-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="4da96-108">cssAccurate 返回准确的保存大小，但需要更长的时间来计算。</span><span class="sxs-lookup"><span data-stu-id="4da96-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="4da96-109">cssQuick 返回大小，为安全起见，但计算时间较少。</span><span class="sxs-lookup"><span data-stu-id="4da96-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="4da96-110">cssDiscardTransientCAs 告知 `GetSaveSize` 它可以丢弃可放弃的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="4da96-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="4da96-111">弄一个指针，指向保存该文件所需的大小。</span><span class="sxs-lookup"><span data-stu-id="4da96-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4da96-112">注解</span><span class="sxs-lookup"><span data-stu-id="4da96-112">Remarks</span></span>  
 <span data-ttu-id="4da96-113">`GetSaveSize`计算在当前作用域中保存程序集及其所有元数据所需的空间（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="4da96-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="4da96-114">（对[IMetaDataEmit：： SaveToStream](imetadataemit-savetostream-method.md)方法的调用将发出此数目的字节。）</span><span class="sxs-lookup"><span data-stu-id="4da96-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="4da96-115">如果调用方实现[IMapToken](imaptoken-interface.md)接口（通过[IMetaDataEmit：： SetHandler](imetadataemit-sethandler-method.md)或[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)），将对 `GetSaveSize` 元数据执行两次传递以优化和压缩该接口。</span><span class="sxs-lookup"><span data-stu-id="4da96-115">If the caller implements the [IMapToken](imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="4da96-116">否则，不执行任何优化。</span><span class="sxs-lookup"><span data-stu-id="4da96-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="4da96-117">如果执行了优化，则第一个传递将只对元数据结构进行排序，以优化导入时间搜索的性能。</span><span class="sxs-lookup"><span data-stu-id="4da96-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="4da96-118">此步骤通常会导致四处移动记录，并产生副作用，由工具保留的标记将会失效。</span><span class="sxs-lookup"><span data-stu-id="4da96-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="4da96-119">但是，在第二次传递后，元数据不会将这些令牌更改通知给调用方。</span><span class="sxs-lookup"><span data-stu-id="4da96-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="4da96-120">在第二个阶段中，将执行各种优化，这些优化旨在减少元数据的总大小，例如， `mdTypeRef` `mdMemberRef` 在引用到当前元数据范围内声明的类型或成员时进行优化（早期绑定）和标记。</span><span class="sxs-lookup"><span data-stu-id="4da96-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="4da96-121">在此阶段中，会发生另一轮标记映射。</span><span class="sxs-lookup"><span data-stu-id="4da96-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="4da96-122">此次传递后，元数据引擎通过其接口通知调用方 `IMapToken` 所有已更改的令牌值。</span><span class="sxs-lookup"><span data-stu-id="4da96-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4da96-123">要求</span><span class="sxs-lookup"><span data-stu-id="4da96-123">Requirements</span></span>  
 <span data-ttu-id="4da96-124">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4da96-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4da96-125">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="4da96-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4da96-126">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="4da96-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4da96-127">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4da96-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da96-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4da96-128">See also</span></span>

- [<span data-ttu-id="4da96-129">IMetaDataEmit 接口</span><span class="sxs-lookup"><span data-stu-id="4da96-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4da96-130">IMetaDataEmit2 接口</span><span class="sxs-lookup"><span data-stu-id="4da96-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
