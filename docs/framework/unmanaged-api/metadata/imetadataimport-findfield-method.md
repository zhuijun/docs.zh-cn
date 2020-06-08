---
title: IMetaDataImport::FindField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503661"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="ae66a-102">IMetaDataImport::FindField 方法</span><span class="sxs-lookup"><span data-stu-id="ae66a-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="ae66a-103">获取一个指针，该指针指向由指定的括起来 <xref:System.Type> 且具有指定名称和元数据签名的字段的 FieldDef 标记。</span><span class="sxs-lookup"><span data-stu-id="ae66a-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae66a-104">语法</span><span class="sxs-lookup"><span data-stu-id="ae66a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae66a-105">参数</span><span class="sxs-lookup"><span data-stu-id="ae66a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ae66a-106">中包含要搜索的字段的类或接口的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="ae66a-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="ae66a-107">如果此值为 `mdTokenNil` ，则对全局变量执行查找。</span><span class="sxs-lookup"><span data-stu-id="ae66a-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="ae66a-108">中要搜索的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="ae66a-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ae66a-109">中指向字段的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="ae66a-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ae66a-110">中的大小（以字节为单位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="ae66a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="ae66a-111">弄指向匹配的 FieldDef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="ae66a-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae66a-112">注解</span><span class="sxs-lookup"><span data-stu-id="ae66a-112">Remarks</span></span>  
 <span data-ttu-id="ae66a-113">您可以使用其封闭类或接口（ `td` ）、其名称（ `szName` ）和（可选）的签名（）来指定字段 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="ae66a-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="ae66a-114">传递给的签名 `FindField` 必须已在当前范围内生成，因为签名将绑定到特定范围。</span><span class="sxs-lookup"><span data-stu-id="ae66a-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="ae66a-115">签名可以嵌入标识封闭类或值类型的标记。</span><span class="sxs-lookup"><span data-stu-id="ae66a-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="ae66a-116">（标记是本地 TypeDef 表中的索引）。</span><span class="sxs-lookup"><span data-stu-id="ae66a-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="ae66a-117">不能在当前范围的上下文之外生成运行时签名，并将该签名用作的输入 `FindField` 。</span><span class="sxs-lookup"><span data-stu-id="ae66a-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="ae66a-118">`FindField`仅查找直接在类或接口中定义的字段;它不会找到继承的字段。</span><span class="sxs-lookup"><span data-stu-id="ae66a-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae66a-119">要求</span><span class="sxs-lookup"><span data-stu-id="ae66a-119">Requirements</span></span>  
 <span data-ttu-id="ae66a-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae66a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae66a-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="ae66a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae66a-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="ae66a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae66a-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae66a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae66a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae66a-124">See also</span></span>

- [<span data-ttu-id="ae66a-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="ae66a-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ae66a-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="ae66a-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
