---
title: IMetaDataImport::GetClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 36c0ffef2d984604be4ae19899e8f3f912cee123
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491467"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="d8dc4-102">IMetaDataImport::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="d8dc4-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="d8dc4-103">获取指定的 TypeDef 标记所引用类的布局信息。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8dc4-104">语法</span><span class="sxs-lookup"><span data-stu-id="d8dc4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8dc4-105">参数</span><span class="sxs-lookup"><span data-stu-id="d8dc4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d8dc4-106">中具有要返回的布局的类的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="d8dc4-107">弄值1、2、4、8或16，表示类的 pack 大小。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="d8dc4-108">弄[COR_FIELD_OFFSET](cor-field-offset-structure.md)值的数组。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-108">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d8dc4-109">[in] `rFieldOffset` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="d8dc4-110">弄中返回的元素的数目 `rFieldOffset` 。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="d8dc4-111">弄所表示的类的大小（以字节为单位） `td` 。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8dc4-112">要求</span><span class="sxs-lookup"><span data-stu-id="d8dc4-112">Requirements</span></span>  
 <span data-ttu-id="d8dc4-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8dc4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8dc4-114">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="d8dc4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8dc4-115">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="d8dc4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8dc4-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8dc4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8dc4-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8dc4-117">See also</span></span>

- [<span data-ttu-id="d8dc4-118">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="d8dc4-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d8dc4-119">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="d8dc4-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
