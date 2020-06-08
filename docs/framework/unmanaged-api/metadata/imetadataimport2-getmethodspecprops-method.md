---
title: IMetaDataImport2::GetMethodSpecProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 079d9245526ff7914d1cbd6a91f0f2d96a690af5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490440"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="d6928-102">IMetaDataImport2::GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="d6928-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="d6928-103">获取指定的 MethodSpec 标记所引用的方法的元数据签名。</span><span class="sxs-lookup"><span data-stu-id="d6928-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6928-104">语法</span><span class="sxs-lookup"><span data-stu-id="d6928-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d6928-105">参数</span><span class="sxs-lookup"><span data-stu-id="d6928-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="d6928-106">中一个 MethodSpec 标记，表示方法的实例化。</span><span class="sxs-lookup"><span data-stu-id="d6928-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="d6928-107">弄一个指针，指向表示方法定义的 MethodDef 或 MethodRef 标记。</span><span class="sxs-lookup"><span data-stu-id="d6928-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d6928-108">弄指向方法的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="d6928-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d6928-109">弄的大小（以字节为单位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d6928-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6928-110">要求</span><span class="sxs-lookup"><span data-stu-id="d6928-110">Requirements</span></span>  
 <span data-ttu-id="d6928-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6928-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6928-112">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="d6928-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6928-113">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="d6928-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6928-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6928-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6928-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6928-115">See also</span></span>

- [<span data-ttu-id="d6928-116">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="d6928-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="d6928-117">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="d6928-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
