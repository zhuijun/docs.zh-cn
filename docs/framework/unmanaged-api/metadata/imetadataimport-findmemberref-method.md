---
title: IMetaDataImport::FindMemberRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491623"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="240f7-102">IMetaDataImport::FindMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="240f7-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="240f7-103">获取一个指针，该指针指向成员引用的 MemberRef 标记，该成员引用由指定的括起来并 <xref:System.Type> 具有指定的名称和元数据签名。</span><span class="sxs-lookup"><span data-stu-id="240f7-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="240f7-104">语法</span><span class="sxs-lookup"><span data-stu-id="240f7-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="240f7-105">参数</span><span class="sxs-lookup"><span data-stu-id="240f7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="240f7-106">中类或接口的 TypeRef 标记，其中包含要搜索的成员引用。</span><span class="sxs-lookup"><span data-stu-id="240f7-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="240f7-107">如果此值为 `mdTokenNil` ，则对全局变量或全局函数引用执行查找。</span><span class="sxs-lookup"><span data-stu-id="240f7-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="240f7-108">中要搜索的成员引用的名称。</span><span class="sxs-lookup"><span data-stu-id="240f7-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="240f7-109">中指向成员引用的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="240f7-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="240f7-110">中的大小（以字节为单位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="240f7-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="240f7-111">弄指向匹配的 MemberRef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="240f7-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="240f7-112">注解</span><span class="sxs-lookup"><span data-stu-id="240f7-112">Remarks</span></span>  
 <span data-ttu-id="240f7-113">使用成员的封闭类或接口（ `td` ）、其名称（ `szName` ）和（可选）的签名（）来指定成员 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="240f7-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="240f7-114">传递给的签名 `FindMemberRef` 必须已在当前范围内生成，因为签名将绑定到特定范围。</span><span class="sxs-lookup"><span data-stu-id="240f7-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="240f7-115">签名可以嵌入标识封闭类或值类型的标记。</span><span class="sxs-lookup"><span data-stu-id="240f7-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="240f7-116">该令牌是本地 TypeDef 表中的索引。</span><span class="sxs-lookup"><span data-stu-id="240f7-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="240f7-117">不能在当前范围的上下文之外生成运行时签名，并将该签名用作的输入 `FindMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="240f7-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="240f7-118">`FindMemberRef`仅查找直接在类或接口中定义的成员引用;它不会查找继承成员引用。</span><span class="sxs-lookup"><span data-stu-id="240f7-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="240f7-119">要求</span><span class="sxs-lookup"><span data-stu-id="240f7-119">Requirements</span></span>  
 <span data-ttu-id="240f7-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="240f7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="240f7-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="240f7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="240f7-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="240f7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="240f7-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="240f7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="240f7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="240f7-124">See also</span></span>

- [<span data-ttu-id="240f7-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="240f7-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="240f7-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="240f7-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
