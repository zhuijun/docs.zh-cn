---
title: IMetaDataImport::FindTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 545fe1e1d9e641d2225ad92c11453558dc4b97d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491493"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="69720-102">IMetaDataImport::FindTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="69720-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="69720-103">获取一个指针，该指针指向 <xref:System.Type> 指定范围内且具有指定名称的引用的 TypeRef 标记。</span><span class="sxs-lookup"><span data-stu-id="69720-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69720-104">语法</span><span class="sxs-lookup"><span data-stu-id="69720-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69720-105">参数</span><span class="sxs-lookup"><span data-stu-id="69720-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="69720-106">中一个 ModuleRef、AssemblyRef 或 TypeRef 标记，分别指定定义了类型引用的模块、程序集或类型。</span><span class="sxs-lookup"><span data-stu-id="69720-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="69720-107">中要搜索的类型引用的名称。</span><span class="sxs-lookup"><span data-stu-id="69720-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="69720-108">弄指向匹配的 TypeRef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="69720-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69720-109">要求</span><span class="sxs-lookup"><span data-stu-id="69720-109">Requirements</span></span>  
 <span data-ttu-id="69720-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69720-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69720-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="69720-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69720-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="69720-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="69720-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69720-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69720-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69720-114">See also</span></span>

- [<span data-ttu-id="69720-115">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="69720-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="69720-116">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="69720-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
