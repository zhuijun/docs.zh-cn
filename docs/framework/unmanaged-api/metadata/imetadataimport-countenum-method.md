---
title: IMetaDataImport::CountEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492377"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="0b122-102">IMetaDataImport::CountEnum 方法</span><span class="sxs-lookup"><span data-stu-id="0b122-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="0b122-103">获取由指定枚举器检索的枚举中的元素数目。</span><span class="sxs-lookup"><span data-stu-id="0b122-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b122-104">语法</span><span class="sxs-lookup"><span data-stu-id="0b122-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b122-105">参数</span><span class="sxs-lookup"><span data-stu-id="0b122-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0b122-106">中枚举器的句柄。</span><span class="sxs-lookup"><span data-stu-id="0b122-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="0b122-107">弄枚举的元素的数目。</span><span class="sxs-lookup"><span data-stu-id="0b122-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b122-108">注解</span><span class="sxs-lookup"><span data-stu-id="0b122-108">Remarks</span></span>  
 <span data-ttu-id="0b122-109">由指定的句柄 `hEnum` 是从以前的 `Enum` *名称*调用获取的（例如， [IMetaDataImport：： EnumTypeDefs](imetadataimport-enumtypedefs-method.md)）。</span><span class="sxs-lookup"><span data-stu-id="0b122-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b122-110">要求</span><span class="sxs-lookup"><span data-stu-id="0b122-110">Requirements</span></span>  
 <span data-ttu-id="0b122-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b122-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b122-112">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="0b122-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b122-113">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="0b122-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b122-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b122-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b122-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b122-115">See also</span></span>

- [<span data-ttu-id="0b122-116">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="0b122-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0b122-117">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="0b122-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
