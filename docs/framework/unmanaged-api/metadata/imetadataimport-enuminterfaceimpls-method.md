---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492182"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="32a20-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="32a20-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="32a20-103">枚举由指定实现的所有接口 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="32a20-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="32a20-104">语法</span><span class="sxs-lookup"><span data-stu-id="32a20-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32a20-105">参数</span><span class="sxs-lookup"><span data-stu-id="32a20-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="32a20-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="32a20-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="32a20-107">中要枚举其 MethodDef 标记表示接口实现的 TypeDef 的标记。</span><span class="sxs-lookup"><span data-stu-id="32a20-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="32a20-108">弄用于存储 MethodDef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="32a20-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="32a20-109">中数组的最大长度 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="32a20-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="32a20-110">弄返回的标记的实际数量 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="32a20-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32a20-111">返回值</span><span class="sxs-lookup"><span data-stu-id="32a20-111">Return Value</span></span>  
  
|<span data-ttu-id="32a20-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32a20-112">HRESULT</span></span>|<span data-ttu-id="32a20-113">说明</span><span class="sxs-lookup"><span data-stu-id="32a20-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="32a20-114">`EnumInterfaceImpls`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="32a20-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="32a20-115">没有要枚举的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="32a20-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="32a20-116">在这种情况下， `pcImpls` 设置为零。</span><span class="sxs-lookup"><span data-stu-id="32a20-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="32a20-117">注解</span><span class="sxs-lookup"><span data-stu-id="32a20-117">Remarks</span></span>

<span data-ttu-id="32a20-118">枚举返回 `mdInterfaceImpl` 由指定的实现的每个接口的令牌集合 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="32a20-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="32a20-119">接口令牌按指定的顺序（通过 `DefineTypeDef` 或 `SetTypeDefProps` ）返回。</span><span class="sxs-lookup"><span data-stu-id="32a20-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="32a20-120">`mdInterfaceImpl`可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)查询返回的标记的属性。</span><span class="sxs-lookup"><span data-stu-id="32a20-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="32a20-121">要求</span><span class="sxs-lookup"><span data-stu-id="32a20-121">Requirements</span></span>  
 <span data-ttu-id="32a20-122">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32a20-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a20-123">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="32a20-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32a20-124">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="32a20-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32a20-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a20-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a20-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32a20-126">See also</span></span>

- [<span data-ttu-id="32a20-127">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="32a20-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="32a20-128">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="32a20-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
