---
title: IMetaDataImport::FindMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503648"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="46ed6-102">IMetaDataImport::FindMethod 方法</span><span class="sxs-lookup"><span data-stu-id="46ed6-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="46ed6-103">获取一个指针，该指针指向由指定的 <xref:System.Type> 和具有指定名称和元数据签名的方法的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="46ed6-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46ed6-104">语法</span><span class="sxs-lookup"><span data-stu-id="46ed6-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46ed6-105">参数</span><span class="sxs-lookup"><span data-stu-id="46ed6-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="46ed6-106">中`mdTypeDef`包含要搜索的成员的类型（类或接口）的标记。</span><span class="sxs-lookup"><span data-stu-id="46ed6-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="46ed6-107">如果此值为 `mdTokenNil` ，则对全局函数执行查找。</span><span class="sxs-lookup"><span data-stu-id="46ed6-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="46ed6-108">中要搜索的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="46ed6-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="46ed6-109">中指向方法的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="46ed6-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="46ed6-110">中的大小（以字节为单位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="46ed6-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="46ed6-111">弄指向匹配 MethodDef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="46ed6-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46ed6-112">注解</span><span class="sxs-lookup"><span data-stu-id="46ed6-112">Remarks</span></span>  
 <span data-ttu-id="46ed6-113">使用方法的封闭类或接口（ `td` ）、其名称（ `szName` ）和（可选）的签名（）来指定方法 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="46ed6-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="46ed6-114">类或接口中可能有多个具有相同名称的方法。</span><span class="sxs-lookup"><span data-stu-id="46ed6-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="46ed6-115">在这种情况下，传递该方法的签名以查找唯一匹配项。</span><span class="sxs-lookup"><span data-stu-id="46ed6-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="46ed6-116">传递给的签名 `FindMethod` 必须已在当前范围内生成，因为签名将绑定到特定范围。</span><span class="sxs-lookup"><span data-stu-id="46ed6-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="46ed6-117">签名可以嵌入标识封闭类或值类型的标记。</span><span class="sxs-lookup"><span data-stu-id="46ed6-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="46ed6-118">该令牌是本地 TypeDef 表中的索引。</span><span class="sxs-lookup"><span data-stu-id="46ed6-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="46ed6-119">不能在当前范围的上下文之外生成运行时签名，并将该签名用作输入以输入到 `FindMethod` 。</span><span class="sxs-lookup"><span data-stu-id="46ed6-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="46ed6-120">`FindMethod`仅查找直接在类或接口中定义的方法;它找不到继承的方法。</span><span class="sxs-lookup"><span data-stu-id="46ed6-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46ed6-121">要求</span><span class="sxs-lookup"><span data-stu-id="46ed6-121">Requirements</span></span>  
 <span data-ttu-id="46ed6-122">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46ed6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46ed6-123">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="46ed6-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46ed6-124">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="46ed6-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46ed6-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46ed6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ed6-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46ed6-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="46ed6-127">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="46ed6-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="46ed6-128">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="46ed6-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
