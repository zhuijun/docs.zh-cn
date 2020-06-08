---
title: IMetaDataImport2::GetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 7e97b2d4ad1fec4675d1484959b115a4d4b87e90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490609"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="3b1a9-102">IMetaDataImport2::GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="3b1a9-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="3b1a9-103">获取与指定标记表示的泛型参数关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1a9-104">语法</span><span class="sxs-lookup"><span data-stu-id="3b1a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b1a9-105">参数</span><span class="sxs-lookup"><span data-stu-id="3b1a9-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="3b1a9-106">中表示要为其返回元数据的泛型参数的标记。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="3b1a9-107">弄`Type`参数在父构造函数或方法中的序号位置。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="3b1a9-108">弄用于描述泛型参数的的[CorGenericParamAttr](corgenericparamattr-enumeration.md)枚举的值 `Type` 。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-108">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="3b1a9-109">弄一个 TypeDef 或 MethodDef 标记，它表示参数的所有者。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="3b1a9-110">弄保留以供将来进行扩展。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="3b1a9-111">弄泛型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3b1a9-112">中缓冲区的大小 `wzName` 。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3b1a9-113">弄以宽字符返回的名称的大小。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b1a9-114">要求</span><span class="sxs-lookup"><span data-stu-id="3b1a9-114">Requirements</span></span>  
 <span data-ttu-id="3b1a9-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1a9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b1a9-116">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="3b1a9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b1a9-117">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="3b1a9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b1a9-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b1a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1a9-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b1a9-119">See also</span></span>

- [<span data-ttu-id="3b1a9-120">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="3b1a9-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="3b1a9-121">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="3b1a9-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
