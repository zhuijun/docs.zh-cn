---
title: IMetaDataImport::GetEventProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491298"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="c0049-102">IMetaDataImport::GetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="c0049-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="c0049-103">获取指定事件标记所表示的事件的元数据信息，包括声明类型、委托的添加和移除方法以及任何标志和其他关联的数据。</span><span class="sxs-lookup"><span data-stu-id="c0049-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0049-104">语法</span><span class="sxs-lookup"><span data-stu-id="c0049-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0049-105">参数</span><span class="sxs-lookup"><span data-stu-id="c0049-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="c0049-106">中表示要获取其元数据的事件的事件元数据标记。</span><span class="sxs-lookup"><span data-stu-id="c0049-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c0049-107">弄一个指针，指向表示声明事件的类的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="c0049-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="c0049-108">弄引用的事件的名称 `ev` 。</span><span class="sxs-lookup"><span data-stu-id="c0049-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="c0049-109">中请求的长度（以宽字符为范围） `szEvent` 。</span><span class="sxs-lookup"><span data-stu-id="c0049-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="c0049-110">弄返回的宽字符的长度 `szEvent` 。</span><span class="sxs-lookup"><span data-stu-id="c0049-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="c0049-111">弄指向表示事件类型的 TypeRef 或 TypeDef 元数据标记的指针 <xref:System.Delegate> 。</span><span class="sxs-lookup"><span data-stu-id="c0049-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="c0049-112">弄指向表示添加事件处理程序的方法的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="c0049-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="c0049-113">弄指向表示删除事件处理程序的方法的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="c0049-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="c0049-114">弄指向表示引发事件的方法的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="c0049-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="c0049-115">弄指向与事件关联的其他方法的标记指针的数组。</span><span class="sxs-lookup"><span data-stu-id="c0049-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c0049-116">[in] `rmdOtherMethod` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="c0049-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="c0049-117">弄返回的令牌数 `rmdOtherMethod` 。</span><span class="sxs-lookup"><span data-stu-id="c0049-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0049-118">要求</span><span class="sxs-lookup"><span data-stu-id="c0049-118">Requirements</span></span>  
 <span data-ttu-id="c0049-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0049-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0049-120">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="c0049-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0049-121">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="c0049-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0049-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0049-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0049-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0049-123">See also</span></span>

- [<span data-ttu-id="c0049-124">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="c0049-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c0049-125">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="c0049-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
