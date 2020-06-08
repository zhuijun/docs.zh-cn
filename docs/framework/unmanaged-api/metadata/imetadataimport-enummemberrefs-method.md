---
title: IMetaDataImport::EnumMemberRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: 68cdefe7ab362b26bbf060fa46766068eb0d7094
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503752"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="3a658-102">IMetaDataImport::EnumMemberRefs 方法</span><span class="sxs-lookup"><span data-stu-id="3a658-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="3a658-103">枚举表示指定类型成员的 MemberRef 标记。</span><span class="sxs-lookup"><span data-stu-id="3a658-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a658-104">语法</span><span class="sxs-lookup"><span data-stu-id="3a658-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a658-105">参数</span><span class="sxs-lookup"><span data-stu-id="3a658-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3a658-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="3a658-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="3a658-107">中要枚举其成员的类型的 TypeDef、TypeRef、MethodDef 或 ModuleRef 标记。</span><span class="sxs-lookup"><span data-stu-id="3a658-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="3a658-108">弄用于存储 MemberRef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="3a658-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3a658-109">[in] `rMemberRefs` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="3a658-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3a658-110">弄中返回的 MemberRef 标记的实际数量 `rMemberRefs` 。</span><span class="sxs-lookup"><span data-stu-id="3a658-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a658-111">返回值</span><span class="sxs-lookup"><span data-stu-id="3a658-111">Return Value</span></span>  
  
|<span data-ttu-id="3a658-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a658-112">HRESULT</span></span>|<span data-ttu-id="3a658-113">说明</span><span class="sxs-lookup"><span data-stu-id="3a658-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3a658-114">`EnumMemberRefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="3a658-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3a658-115">没有要枚举的 MemberRef 标记。</span><span class="sxs-lookup"><span data-stu-id="3a658-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="3a658-116">在这种情况下， `pcTokens` 将为零。</span><span class="sxs-lookup"><span data-stu-id="3a658-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a658-117">要求</span><span class="sxs-lookup"><span data-stu-id="3a658-117">Requirements</span></span>  
 <span data-ttu-id="3a658-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a658-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a658-119">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="3a658-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a658-120">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="3a658-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a658-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a658-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a658-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a658-122">See also</span></span>

- [<span data-ttu-id="3a658-123">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="3a658-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3a658-124">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="3a658-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
