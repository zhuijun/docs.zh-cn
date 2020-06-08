---
title: IMetaDataValidate 接口
ms.date: 03/30/2017
api_name:
- IMetaDataValidate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate
helpviewer_keywords:
- IMetaDataValidate interface [.NET Framework metadata]
ms.assetid: db98608a-e85c-4f50-9d7b-5f57a426ddb6
topic_type:
- apiref
ms.openlocfilehash: 2dbd4559bad54aee69f6980e8baf6441480f482c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489668"
---
# <a name="imetadatavalidate-interface"></a><span data-ttu-id="e1147-102">IMetaDataValidate 接口</span><span class="sxs-lookup"><span data-stu-id="e1147-102">IMetaDataValidate Interface</span></span>
<span data-ttu-id="e1147-103">提供验证元数据签名的方法。</span><span class="sxs-lookup"><span data-stu-id="e1147-103">Provides methods to validate metadata signatures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1147-104">方法</span><span class="sxs-lookup"><span data-stu-id="e1147-104">Methods</span></span>  
  
|<span data-ttu-id="e1147-105">方法</span><span class="sxs-lookup"><span data-stu-id="e1147-105">Method</span></span>|<span data-ttu-id="e1147-106">说明</span><span class="sxs-lookup"><span data-stu-id="e1147-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1147-107">ValidateMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="e1147-107">ValidateMetaData Method</span></span>](imetadatavalidate-validatemetadata-method.md)|<span data-ttu-id="e1147-108">验证在当前元数据范围内的对象的元数据签名。</span><span class="sxs-lookup"><span data-stu-id="e1147-108">Validates the metadata signatures of the objects in the current metadata scope.</span></span>|  
|[<span data-ttu-id="e1147-109">ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="e1147-109">ValidatorInit Method</span></span>](imetadatavalidate-validatorinit-method.md)|<span data-ttu-id="e1147-110">设置一个标志，该标志指定当前元数据范围内的模块类型，并注册验证错误的指定回调方法。</span><span class="sxs-lookup"><span data-stu-id="e1147-110">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1147-111">要求</span><span class="sxs-lookup"><span data-stu-id="e1147-111">Requirements</span></span>  
 <span data-ttu-id="e1147-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1147-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1147-113">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="e1147-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1147-114">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="e1147-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1147-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1147-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1147-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1147-116">See also</span></span>

- [<span data-ttu-id="e1147-117">元数据接口</span><span class="sxs-lookup"><span data-stu-id="e1147-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
