---
title: IMetaDataError::OnError 方法
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: d2252f58af1a319d953fb320a99fad1cfec3dca0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492689"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="466ba-102">IMetaDataError::OnError 方法</span><span class="sxs-lookup"><span data-stu-id="466ba-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="466ba-103">提供在元数据合并期间发生的错误的通知。</span><span class="sxs-lookup"><span data-stu-id="466ba-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="466ba-104">语法</span><span class="sxs-lookup"><span data-stu-id="466ba-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="466ba-105">参数</span><span class="sxs-lookup"><span data-stu-id="466ba-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="466ba-106">中返回到调用方法的 HRESULT 错误值。</span><span class="sxs-lookup"><span data-stu-id="466ba-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="466ba-107">中发生错误时正在合并的代码对象的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="466ba-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="466ba-108">要求</span><span class="sxs-lookup"><span data-stu-id="466ba-108">Requirements</span></span>  
 <span data-ttu-id="466ba-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="466ba-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="466ba-110">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="466ba-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="466ba-111">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="466ba-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="466ba-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="466ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="466ba-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="466ba-113">See also</span></span>

- [<span data-ttu-id="466ba-114">IMetaDataError 接口</span><span class="sxs-lookup"><span data-stu-id="466ba-114">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
