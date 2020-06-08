---
title: IMetaDataEmit2::SaveDelta 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: d3e25f271fc434785e25e7b226ad98f86b5f8dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492780"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="fcedf-102">IMetaDataEmit2::SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="fcedf-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="fcedf-103">将当前的 "编辑并继续" 会话中的更改保存到指定的文件。</span><span class="sxs-lookup"><span data-stu-id="fcedf-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcedf-104">语法</span><span class="sxs-lookup"><span data-stu-id="fcedf-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcedf-105">参数</span><span class="sxs-lookup"><span data-stu-id="fcedf-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="fcedf-106">中用于保存更改的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="fcedf-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="fcedf-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="fcedf-107">[in] Reserved.</span></span> <span data-ttu-id="fcedf-108">必须为零。</span><span class="sxs-lookup"><span data-stu-id="fcedf-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcedf-109">要求</span><span class="sxs-lookup"><span data-stu-id="fcedf-109">Requirements</span></span>  
 <span data-ttu-id="fcedf-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcedf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcedf-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="fcedf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcedf-112">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="fcedf-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcedf-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcedf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcedf-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcedf-114">See also</span></span>

- [<span data-ttu-id="fcedf-115">IMetaDataEmit2 接口</span><span class="sxs-lookup"><span data-stu-id="fcedf-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="fcedf-116">IMetaDataEmit 接口</span><span class="sxs-lookup"><span data-stu-id="fcedf-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
