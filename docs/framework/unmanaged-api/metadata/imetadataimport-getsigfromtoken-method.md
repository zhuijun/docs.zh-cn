---
title: IMetaDataImport::GetSigFromToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
ms.openlocfilehash: d795f90c458b7fcf1a191b2763ac5f5bb55fb438
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490882"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="df0ba-102">IMetaDataImport::GetSigFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="df0ba-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="df0ba-103">获取与指定标记关联的二进制元数据签名。</span><span class="sxs-lookup"><span data-stu-id="df0ba-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df0ba-104">语法</span><span class="sxs-lookup"><span data-stu-id="df0ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df0ba-105">参数</span><span class="sxs-lookup"><span data-stu-id="df0ba-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="df0ba-106">中要为其返回二进制元数据签名的标记。</span><span class="sxs-lookup"><span data-stu-id="df0ba-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="df0ba-107">弄指向返回的元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="df0ba-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="df0ba-108">弄二进制元数据签名的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="df0ba-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df0ba-109">要求</span><span class="sxs-lookup"><span data-stu-id="df0ba-109">Requirements</span></span>  
 <span data-ttu-id="df0ba-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df0ba-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df0ba-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="df0ba-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df0ba-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="df0ba-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df0ba-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df0ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df0ba-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df0ba-114">See also</span></span>

- [<span data-ttu-id="df0ba-115">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="df0ba-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="df0ba-116">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="df0ba-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
