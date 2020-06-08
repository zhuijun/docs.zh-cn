---
title: IMetaDataImport2::EnumMethodSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490713"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="bd76f-102">IMetaDataImport2::EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="bd76f-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="bd76f-103">获取与指定的 MethodDef 或 MemberRef 标记相关联的 MethodSpec 标记数组的枚举器。</span><span class="sxs-lookup"><span data-stu-id="bd76f-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd76f-104">语法</span><span class="sxs-lookup"><span data-stu-id="bd76f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="bd76f-105">参数</span><span class="sxs-lookup"><span data-stu-id="bd76f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bd76f-106">[in，out]指向的枚举器的指针 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="bd76f-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="bd76f-107">中MemberRef 或 MethodDef 标记，表示要枚举其 MethodSpec 标记的方法。</span><span class="sxs-lookup"><span data-stu-id="bd76f-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="bd76f-108">如果的值 `tk` 为0（零），则将枚举范围内的所有 MethodSpec 标记。</span><span class="sxs-lookup"><span data-stu-id="bd76f-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="bd76f-109">弄要枚举的 MethodSpec 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="bd76f-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bd76f-110">中要放入的请求的最大数量 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="bd76f-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="bd76f-111">弄放入的标记数 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="bd76f-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd76f-112">返回值</span><span class="sxs-lookup"><span data-stu-id="bd76f-112">Return Value</span></span>  
  
|<span data-ttu-id="bd76f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd76f-113">HRESULT</span></span>|<span data-ttu-id="bd76f-114">说明</span><span class="sxs-lookup"><span data-stu-id="bd76f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bd76f-115">`EnumMethodSpecs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="bd76f-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bd76f-116">`phEnum`没有成员元素。</span><span class="sxs-lookup"><span data-stu-id="bd76f-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="bd76f-117">在这种情况下， `pcMethodSpecs` 设置为0（零）。</span><span class="sxs-lookup"><span data-stu-id="bd76f-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd76f-118">要求</span><span class="sxs-lookup"><span data-stu-id="bd76f-118">Requirements</span></span>  
 <span data-ttu-id="bd76f-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd76f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd76f-120">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="bd76f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd76f-121">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="bd76f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd76f-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd76f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd76f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd76f-123">See also</span></span>

- [<span data-ttu-id="bd76f-124">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="bd76f-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="bd76f-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="bd76f-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
