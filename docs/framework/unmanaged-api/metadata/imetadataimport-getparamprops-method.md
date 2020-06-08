---
title: IMetaDataImport::GetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491051"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="99a3f-102">IMetaDataImport::GetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="99a3f-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="99a3f-103">获取指定的 ParamDef 标记所引用的参数的元数据值。</span><span class="sxs-lookup"><span data-stu-id="99a3f-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a3f-104">语法</span><span class="sxs-lookup"><span data-stu-id="99a3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99a3f-105">参数</span><span class="sxs-lookup"><span data-stu-id="99a3f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="99a3f-106">中一个 ParamDef 标记，它表示要为其返回元数据的参数。</span><span class="sxs-lookup"><span data-stu-id="99a3f-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="99a3f-107">弄指向 MethodDef 标记的指针，该标记表示采用参数的方法。</span><span class="sxs-lookup"><span data-stu-id="99a3f-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="99a3f-108">弄参数在方法自变量列表中的序号位置。</span><span class="sxs-lookup"><span data-stu-id="99a3f-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="99a3f-109">弄用于保存参数名称的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="99a3f-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="99a3f-110">中请求的大小（以宽字符为大小） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="99a3f-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="99a3f-111">弄返回的宽字符大小 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="99a3f-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="99a3f-112">弄指向与参数关联的任何特性标志的指针。</span><span class="sxs-lookup"><span data-stu-id="99a3f-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="99a3f-113">这是一个值的位掩码 `CorParamAttr` 。</span><span class="sxs-lookup"><span data-stu-id="99a3f-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="99a3f-114">弄指向标志的指针，该标志指定参数为 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="99a3f-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="99a3f-115">弄指向参数返回的常量字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="99a3f-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="99a3f-116">弄以宽字符为大小的大小 `ppValue` ; 如果不包含字符串，则为零 `ppValue` 。</span><span class="sxs-lookup"><span data-stu-id="99a3f-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99a3f-117">注解</span><span class="sxs-lookup"><span data-stu-id="99a3f-117">Remarks</span></span>

<span data-ttu-id="99a3f-118">参数的序列值 `pulSequence` 从1开始。</span><span class="sxs-lookup"><span data-stu-id="99a3f-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="99a3f-119">返回值的序列号为0。</span><span class="sxs-lookup"><span data-stu-id="99a3f-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="99a3f-120">要求</span><span class="sxs-lookup"><span data-stu-id="99a3f-120">Requirements</span></span>  
 <span data-ttu-id="99a3f-121">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99a3f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99a3f-122">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="99a3f-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99a3f-123">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="99a3f-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99a3f-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99a3f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a3f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99a3f-125">See also</span></span>

- [<span data-ttu-id="99a3f-126">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="99a3f-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="99a3f-127">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="99a3f-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
