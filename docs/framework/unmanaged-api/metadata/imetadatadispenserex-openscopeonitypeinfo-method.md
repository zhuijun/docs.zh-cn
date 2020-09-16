---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
ms.openlocfilehash: 8e119093800ea0a0119ba25ba38cf2eaf9afe96b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540833"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="8cc01-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8cc01-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="8cc01-103">未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="8cc01-103">This method is not implemented.</span></span> <span data-ttu-id="8cc01-104">如果调用，它将返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="8cc01-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc01-105">语法</span><span class="sxs-lookup"><span data-stu-id="8cc01-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cc01-106">参数</span><span class="sxs-lookup"><span data-stu-id="8cc01-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="8cc01-107">中指向 [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) 接口的指针，该接口提供要打开范围的类型信息。</span><span class="sxs-lookup"><span data-stu-id="8cc01-107">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="8cc01-108">中打开模式标志。</span><span class="sxs-lookup"><span data-stu-id="8cc01-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="8cc01-109">中所需的接口。</span><span class="sxs-lookup"><span data-stu-id="8cc01-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="8cc01-110">弄指向返回接口的指针的指针。</span><span class="sxs-lookup"><span data-stu-id="8cc01-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc01-111">要求</span><span class="sxs-lookup"><span data-stu-id="8cc01-111">Requirements</span></span>  
 <span data-ttu-id="8cc01-112">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cc01-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc01-113">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="8cc01-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8cc01-114">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="8cc01-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8cc01-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc01-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc01-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="8cc01-116">See also</span></span>

- [<span data-ttu-id="8cc01-117">IMetaDataDispenserEx 接口</span><span class="sxs-lookup"><span data-stu-id="8cc01-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="8cc01-118">IMetaDataDispenser 接口</span><span class="sxs-lookup"><span data-stu-id="8cc01-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
