---
title: IMetaDataImport::GetMemberRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: 00693f1a87334620442e8865e76183b2dab68878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503609"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="b3884-102">IMetaDataImport::GetMemberRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="b3884-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="b3884-103">获取与指定标记引用的成员关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="b3884-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3884-104">语法</span><span class="sxs-lookup"><span data-stu-id="b3884-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,
   [out] mdToken           *ptk,
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3884-105">参数</span><span class="sxs-lookup"><span data-stu-id="b3884-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="b3884-106">中要为其返回关联的元数据的 MemberRef 标记。</span><span class="sxs-lookup"><span data-stu-id="b3884-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="b3884-107">弄TypeDef 或 TypeRef 或 TypeSpec 标记，它表示声明成员的类，或表示声明成员的 module 类的 ModuleRef 标记或表示成员的 MethodDef。</span><span class="sxs-lookup"><span data-stu-id="b3884-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="b3884-108">弄成员名称的字符串缓冲区。</span><span class="sxs-lookup"><span data-stu-id="b3884-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="b3884-109">中请求的大小（以宽字符为大小） `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="b3884-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="b3884-110">弄返回的宽字符大小 `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="b3884-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="b3884-111">弄指向成员的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="b3884-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="b3884-112">弄的大小（以字节为单位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="b3884-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3884-113">要求</span><span class="sxs-lookup"><span data-stu-id="b3884-113">Requirements</span></span>  
 <span data-ttu-id="b3884-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3884-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3884-115">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="b3884-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3884-116">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="b3884-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3884-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3884-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3884-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3884-118">See also</span></span>

- [<span data-ttu-id="b3884-119">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="b3884-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b3884-120">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="b3884-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
