---
title: IMetaDataImport::GetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491038"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="f3979-102">IMetaDataImport::GetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="f3979-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="f3979-103">获取由指定标记表示的属性的元数据。</span><span class="sxs-lookup"><span data-stu-id="f3979-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3979-104">语法</span><span class="sxs-lookup"><span data-stu-id="f3979-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3979-105">参数</span><span class="sxs-lookup"><span data-stu-id="f3979-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="f3979-106">中一个标记，它表示要为其返回元数据的属性。</span><span class="sxs-lookup"><span data-stu-id="f3979-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f3979-107">弄一个指针，指向表示实现属性的类型的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="f3979-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="f3979-108">弄用于保存属性名称的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f3979-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="f3979-109">中的大小（以宽字符为大小） `szProperty` 。</span><span class="sxs-lookup"><span data-stu-id="f3979-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="f3979-110">弄返回的宽字符数 `szProperty` 。</span><span class="sxs-lookup"><span data-stu-id="f3979-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="f3979-111">弄指向应用于属性的任何属性标志的指针。</span><span class="sxs-lookup"><span data-stu-id="f3979-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="f3979-112">此值是[CorPropertyAttr](corpropertyattr-enumeration.md)枚举中的位掩码。</span><span class="sxs-lookup"><span data-stu-id="f3979-112">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="f3979-113">弄指向属性的元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="f3979-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="f3979-114">弄返回的字节数 `ppvSig` 。</span><span class="sxs-lookup"><span data-stu-id="f3979-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="f3979-115">弄一个标志，该标志指定作为属性的默认值的常量的类型。</span><span class="sxs-lookup"><span data-stu-id="f3979-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="f3979-116">此值来自 CorElementType 枚举。</span><span class="sxs-lookup"><span data-stu-id="f3979-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="f3979-117">弄指向存储此属性的默认值的字节的指针。</span><span class="sxs-lookup"><span data-stu-id="f3979-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="f3979-118">弄如果 ELEMENT_TYPE_STRING，则为的宽字符大小 `ppDefaultValue` `pdwCPlusTypeFlag` ; 否则，此值是不相关的。</span><span class="sxs-lookup"><span data-stu-id="f3979-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="f3979-119">在这种情况下，的长度 `ppDefaultValue` 是从指定的类型推断出来的 `pdwCPlusTypeFlag` 。</span><span class="sxs-lookup"><span data-stu-id="f3979-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="f3979-120">弄一个指针，它指向表示属性的 set 访问器方法的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="f3979-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="f3979-121">弄一个指针，它指向表示属性的 get 访问器方法的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="f3979-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="f3979-122">弄MethodDef 标记的数组，表示与属性关联的其他方法。</span><span class="sxs-lookup"><span data-stu-id="f3979-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f3979-123">[in] `rmdOtherMethod` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="f3979-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="f3979-124">如果未提供足够大的数组来容纳所有方法，则会跳过这些方法，而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="f3979-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="f3979-125">弄中返回的 MethodDef 标记的数目 `rmdOtherMethod` 。</span><span class="sxs-lookup"><span data-stu-id="f3979-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3979-126">要求</span><span class="sxs-lookup"><span data-stu-id="f3979-126">Requirements</span></span>  
 <span data-ttu-id="f3979-127">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3979-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3979-128">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="f3979-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3979-129">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="f3979-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3979-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3979-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3979-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3979-131">See also</span></span>

- [<span data-ttu-id="f3979-132">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="f3979-132">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f3979-133">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="f3979-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
