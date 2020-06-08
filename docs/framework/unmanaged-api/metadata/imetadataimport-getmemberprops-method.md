---
title: IMetaDataImport::GetMemberProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503635"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="29755-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="29755-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="29755-103">获取存储在指定的成员定义的元数据中的信息，包括 <xref:System.Type> 指定的元数据标记所引用的成员的名称、二进制签名和相对虚拟地址。</span><span class="sxs-lookup"><span data-stu-id="29755-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="29755-104">这是一个简单的帮助器方法：如果*mb*是 MethodDef，则调用**GetMethodProps** ;如果*mb*是 FieldDef，则调用**GetFieldProps** 。</span><span class="sxs-lookup"><span data-stu-id="29755-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="29755-105">有关详细信息，请参阅其他方法。</span><span class="sxs-lookup"><span data-stu-id="29755-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="29755-106">语法</span><span class="sxs-lookup"><span data-stu-id="29755-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29755-107">参数</span><span class="sxs-lookup"><span data-stu-id="29755-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="29755-108">中引用要为其获取关联元数据的成员的标记。</span><span class="sxs-lookup"><span data-stu-id="29755-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="29755-109">弄指向表示成员的类的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="29755-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="29755-110">弄成员的名称。</span><span class="sxs-lookup"><span data-stu-id="29755-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="29755-111">中缓冲区的大小（以宽字符为大小） `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="29755-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="29755-112">弄返回名称的大小（以宽字符为大小）。</span><span class="sxs-lookup"><span data-stu-id="29755-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="29755-113">弄应用于成员的任何标志值。</span><span class="sxs-lookup"><span data-stu-id="29755-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="29755-114">弄指向成员的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="29755-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="29755-115">弄的大小（以字节为单位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="29755-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="29755-116">弄指向成员的相对虚拟地址的指针。</span><span class="sxs-lookup"><span data-stu-id="29755-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="29755-117">弄与成员关联的任何方法实现标志。</span><span class="sxs-lookup"><span data-stu-id="29755-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="29755-118">弄标记的标志 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="29755-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="29755-119">它是 `ELEMENT_TYPE_*` 值之一。</span><span class="sxs-lookup"><span data-stu-id="29755-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="29755-120">弄此成员返回的常量字符串值。</span><span class="sxs-lookup"><span data-stu-id="29755-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="29755-121">弄的大小（以字符为大小 `ppValue` ）; 如果不保存字符串，则为零 `ppValue` 。</span><span class="sxs-lookup"><span data-stu-id="29755-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29755-122">要求</span><span class="sxs-lookup"><span data-stu-id="29755-122">Requirements</span></span>  
 <span data-ttu-id="29755-123">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29755-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29755-124">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="29755-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29755-125">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="29755-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29755-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29755-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29755-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29755-127">See also</span></span>

- [<span data-ttu-id="29755-128">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="29755-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="29755-129">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="29755-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
