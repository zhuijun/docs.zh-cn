---
title: IMetaDataImport::GetNestedClassProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503531"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="906ea-102">IMetaDataImport::GetNestedClassProps 方法</span><span class="sxs-lookup"><span data-stu-id="906ea-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="906ea-103">获取指定嵌套类型的父级的 TypeDef 标记 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="906ea-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906ea-104">语法</span><span class="sxs-lookup"><span data-stu-id="906ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="906ea-105">参数</span><span class="sxs-lookup"><span data-stu-id="906ea-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="906ea-106">中一个 TypeDef 标记，它表示 <xref:System.Type> 要为其返回父类标记的。</span><span class="sxs-lookup"><span data-stu-id="906ea-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="906ea-107">弄一个指针，指向 <xref:System.Type> 嵌套在中的的 TypeDef 标记 `tdNestedClass` 。</span><span class="sxs-lookup"><span data-stu-id="906ea-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906ea-108">要求</span><span class="sxs-lookup"><span data-stu-id="906ea-108">Requirements</span></span>  
 <span data-ttu-id="906ea-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="906ea-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="906ea-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="906ea-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="906ea-111">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="906ea-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="906ea-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="906ea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906ea-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="906ea-113">See also</span></span>

- [<span data-ttu-id="906ea-114">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="906ea-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="906ea-115">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="906ea-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
