---
title: IMetaDataImport::GetNativeCallConvFromSig 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: 44439eda62f85c32893b73f17bd057195cf6b2e1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503544"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="911fc-102">IMetaDataImport::GetNativeCallConvFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="911fc-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="911fc-103">获取指定的签名指针所表示的方法的本机调用约定。</span><span class="sxs-lookup"><span data-stu-id="911fc-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911fc-104">语法</span><span class="sxs-lookup"><span data-stu-id="911fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="911fc-105">参数</span><span class="sxs-lookup"><span data-stu-id="911fc-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="911fc-106">中指向要为其返回调用约定的方法的元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="911fc-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="911fc-107">中的大小（以字节为单位） `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="911fc-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="911fc-108">弄指向本机调用约定的指针。</span><span class="sxs-lookup"><span data-stu-id="911fc-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="911fc-109">要求</span><span class="sxs-lookup"><span data-stu-id="911fc-109">Requirements</span></span>  
 <span data-ttu-id="911fc-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="911fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="911fc-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="911fc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="911fc-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="911fc-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="911fc-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="911fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911fc-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="911fc-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="911fc-115">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="911fc-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="911fc-116">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="911fc-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
