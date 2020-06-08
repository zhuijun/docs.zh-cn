---
title: IMetaDataImport::GetRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 58ab9ee9381fce4d7af1910df6c8d3bb813bcf13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490886"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="03779-102">IMetaDataImport::GetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="03779-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="03779-103">获取指定标记所表示的方法或字段的相对虚拟地址（RVA）和实现标志。</span><span class="sxs-lookup"><span data-stu-id="03779-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03779-104">语法</span><span class="sxs-lookup"><span data-stu-id="03779-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03779-105">参数</span><span class="sxs-lookup"><span data-stu-id="03779-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="03779-106">中一个 MethodDef 或 FieldDef 元数据标记，它表示要为其返回 RVA 的代码对象。</span><span class="sxs-lookup"><span data-stu-id="03779-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="03779-107">如果标记为 FieldDef，则字段必须是全局变量。</span><span class="sxs-lookup"><span data-stu-id="03779-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="03779-108">弄指向由标记表示的代码对象的相对虚拟地址的指针。</span><span class="sxs-lookup"><span data-stu-id="03779-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="03779-109">弄一个指针，指向方法的实现标志。</span><span class="sxs-lookup"><span data-stu-id="03779-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="03779-110">此值是[CorMethodImpl](cormethodimpl-enumeration.md)枚举中的位掩码。</span><span class="sxs-lookup"><span data-stu-id="03779-110">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="03779-111">`pdwImplFlags`仅当为 MethodDef 标记时，的值才有效 `tk` 。</span><span class="sxs-lookup"><span data-stu-id="03779-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03779-112">要求</span><span class="sxs-lookup"><span data-stu-id="03779-112">Requirements</span></span>  
 <span data-ttu-id="03779-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03779-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03779-114">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="03779-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03779-115">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="03779-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03779-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03779-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03779-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03779-117">See also</span></span>

- [<span data-ttu-id="03779-118">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="03779-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="03779-119">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="03779-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
