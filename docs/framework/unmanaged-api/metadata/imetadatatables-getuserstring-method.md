---
title: IMetaDataTables::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501139"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="e61d2-102">IMetaDataTables::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="e61d2-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="e61d2-103">获取当前范围内字符串列中指定索引处的硬编码字符串。</span><span class="sxs-lookup"><span data-stu-id="e61d2-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="e61d2-104">语法</span><span class="sxs-lookup"><span data-stu-id="e61d2-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="e61d2-105">参数</span><span class="sxs-lookup"><span data-stu-id="e61d2-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="e61d2-106">中要从中检索硬编码字符串的索引值。</span><span class="sxs-lookup"><span data-stu-id="e61d2-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="e61d2-107">弄指向的大小的指针 `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="e61d2-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="e61d2-108">弄指向返回的字符串的指针的指针。</span><span class="sxs-lookup"><span data-stu-id="e61d2-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="e61d2-109">要求</span><span class="sxs-lookup"><span data-stu-id="e61d2-109">Requirements</span></span>

<span data-ttu-id="e61d2-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e61d2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e61d2-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="e61d2-111">**Header:** Cor.h</span></span>

<span data-ttu-id="e61d2-112">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="e61d2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="e61d2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e61d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e61d2-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e61d2-114">See also</span></span>

- [<span data-ttu-id="e61d2-115">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="e61d2-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="e61d2-116">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="e61d2-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
