---
title: IMetaDataImport::GetNameFromToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6d62739148280c7333cf7cdb6002b59a145496e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503557"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="1fb3c-102">IMetaDataImport::GetNameFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="1fb3c-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="1fb3c-103">获取指定的元数据标记所引用的对象的 UTF-8 名称。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="1fb3c-104">此方法已过时。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb3c-105">语法</span><span class="sxs-lookup"><span data-stu-id="1fb3c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fb3c-106">参数</span><span class="sxs-lookup"><span data-stu-id="1fb3c-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1fb3c-107">中表示要为其返回名称的对象的标记。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="1fb3c-108">弄指向堆中 UTF-8 对象名称的指针。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fb3c-109">注解</span><span class="sxs-lookup"><span data-stu-id="1fb3c-109">Remarks</span></span>  
 <span data-ttu-id="1fb3c-110">`GetNameFromToken` 已过时。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="1fb3c-111">作为替代方法，可以调用方法来获取所需的特定类型的标记的属性，例如 `GetFieldProps` 为字段或方法提供 `GetMethodProps` 。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fb3c-112">要求</span><span class="sxs-lookup"><span data-stu-id="1fb3c-112">Requirements</span></span>  
 <span data-ttu-id="1fb3c-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1fb3c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb3c-114">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="1fb3c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1fb3c-115">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="1fb3c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1fb3c-116">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="1fb3c-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb3c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fb3c-117">See also</span></span>

- [<span data-ttu-id="1fb3c-118">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="1fb3c-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1fb3c-119">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="1fb3c-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
