---
title: IMetaDataImport::EnumUnresolvedMethods 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: c991c0af845bc6825db6b3bf258fe0809d5db804
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503687"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="0103d-102">IMetaDataImport::EnumUnresolvedMethods 方法</span><span class="sxs-lookup"><span data-stu-id="0103d-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="0103d-103">枚举表示当前元数据范围内未解析的方法的 MemberDef 标记。</span><span class="sxs-lookup"><span data-stu-id="0103d-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0103d-104">语法</span><span class="sxs-lookup"><span data-stu-id="0103d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0103d-105">参数</span><span class="sxs-lookup"><span data-stu-id="0103d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0103d-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="0103d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0103d-107">第一次调用此方法时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="0103d-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="0103d-108">弄用于存储 MemberDef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="0103d-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0103d-109">[in] `rMethods` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="0103d-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0103d-110">弄中返回的 MemberDef 令牌数 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="0103d-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0103d-111">返回值</span><span class="sxs-lookup"><span data-stu-id="0103d-111">Return Value</span></span>  
  
|<span data-ttu-id="0103d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0103d-112">HRESULT</span></span>|<span data-ttu-id="0103d-113">说明</span><span class="sxs-lookup"><span data-stu-id="0103d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0103d-114">`EnumUnresolvedMethods`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="0103d-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0103d-115">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="0103d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0103d-116">在这种情况下， `pcTokens` 为零。</span><span class="sxs-lookup"><span data-stu-id="0103d-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0103d-117">注解</span><span class="sxs-lookup"><span data-stu-id="0103d-117">Remarks</span></span>  
 <span data-ttu-id="0103d-118">未解析的方法是已声明但未实现的方法。</span><span class="sxs-lookup"><span data-stu-id="0103d-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="0103d-119">如果方法已标记 `miForwardRef` 并且 `mdPinvokeImpl` 或 `miRuntime` 设置为零，则枚举中将包含方法。</span><span class="sxs-lookup"><span data-stu-id="0103d-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="0103d-120">换句话说，未解析的方法是标记 `miForwardRef` 但未在非托管代码中实现的方法，该方法在非托管代码中实现（通过 PInvoke 实现），或由运行时本身内部实现</span><span class="sxs-lookup"><span data-stu-id="0103d-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="0103d-121">枚举排除在模块范围（全局）或接口或抽象类中定义的所有方法。</span><span class="sxs-lookup"><span data-stu-id="0103d-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0103d-122">要求</span><span class="sxs-lookup"><span data-stu-id="0103d-122">Requirements</span></span>  
 <span data-ttu-id="0103d-123">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0103d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0103d-124">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="0103d-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0103d-125">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="0103d-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0103d-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0103d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0103d-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0103d-127">See also</span></span>

- [<span data-ttu-id="0103d-128">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="0103d-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0103d-129">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="0103d-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
