---
title: IMetaDataEmit2::DefineMethodSpec 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503810"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="797a9-102">IMetaDataEmit2::DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="797a9-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="797a9-103">创建方法的泛型实例，并获取定义的标记。</span><span class="sxs-lookup"><span data-stu-id="797a9-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="797a9-104">语法</span><span class="sxs-lookup"><span data-stu-id="797a9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="797a9-105">参数</span><span class="sxs-lookup"><span data-stu-id="797a9-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="797a9-106">中创建泛型实例的方法的标记。</span><span class="sxs-lookup"><span data-stu-id="797a9-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="797a9-107">令牌的类型必须为 `mdMethodDef` 或 `mdMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="797a9-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="797a9-108">中指向方法的二进制 COM + 签名的指针。</span><span class="sxs-lookup"><span data-stu-id="797a9-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="797a9-109">中的大小（以字节为单位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="797a9-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="797a9-110">弄方法的元数据签名定义的标记。</span><span class="sxs-lookup"><span data-stu-id="797a9-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="797a9-111">要求</span><span class="sxs-lookup"><span data-stu-id="797a9-111">Requirements</span></span>  
 <span data-ttu-id="797a9-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="797a9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="797a9-113">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="797a9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="797a9-114">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="797a9-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="797a9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="797a9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="797a9-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="797a9-116">See also</span></span>

- [<span data-ttu-id="797a9-117">IMetaDataEmit2 接口</span><span class="sxs-lookup"><span data-stu-id="797a9-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="797a9-118">IMetaDataEmit 接口</span><span class="sxs-lookup"><span data-stu-id="797a9-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
