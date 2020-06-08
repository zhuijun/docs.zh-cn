---
title: IMetaDataFilter 接口
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503778"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="b040b-102">IMetaDataFilter 接口</span><span class="sxs-lookup"><span data-stu-id="b040b-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="b040b-103">提供用于标记和筛选元数据标记以避免重复已进行的操作的方法。</span><span class="sxs-lookup"><span data-stu-id="b040b-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b040b-104">方法</span><span class="sxs-lookup"><span data-stu-id="b040b-104">Methods</span></span>  
  
|<span data-ttu-id="b040b-105">方法</span><span class="sxs-lookup"><span data-stu-id="b040b-105">Method</span></span>|<span data-ttu-id="b040b-106">说明</span><span class="sxs-lookup"><span data-stu-id="b040b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b040b-107">IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="b040b-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="b040b-108">获取一个值，该值指示是否已处理指定的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="b040b-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="b040b-109">MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="b040b-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="b040b-110">设置一个值，该值指示已处理指定的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="b040b-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="b040b-111">UnmarkAll 方法</span><span class="sxs-lookup"><span data-stu-id="b040b-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="b040b-112">从当前元数据范围内的所有标记中删除处理标记。</span><span class="sxs-lookup"><span data-stu-id="b040b-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b040b-113">要求</span><span class="sxs-lookup"><span data-stu-id="b040b-113">Requirements</span></span>  
 <span data-ttu-id="b040b-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b040b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b040b-115">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="b040b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b040b-116">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="b040b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b040b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b040b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b040b-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b040b-118">See also</span></span>

- [<span data-ttu-id="b040b-119">元数据接口</span><span class="sxs-lookup"><span data-stu-id="b040b-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
