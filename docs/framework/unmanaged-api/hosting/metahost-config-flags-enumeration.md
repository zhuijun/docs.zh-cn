---
title: METAHOST_CONFIG_FLAGS 枚举
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 6b37fcfc04e3ec880c67f102ec12d7f3e4b06a43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493157"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="facf2-102">METAHOST_CONFIG_FLAGS 枚举</span><span class="sxs-lookup"><span data-stu-id="facf2-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="facf2-103">描述在 `pdwConfigFlags` [ICLRMetaHostPolicy：： GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)方法的参数中返回的可能的标志，指示 `useLegacyV2RuntimeActivationPolicy` 配置文件的[ \<startup> 元素](../../configure-apps/file-schema/startup/startup-element.md)中的特性的状态和设置。</span><span class="sxs-lookup"><span data-stu-id="facf2-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facf2-104">语法</span><span class="sxs-lookup"><span data-stu-id="facf2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="facf2-105">成员</span><span class="sxs-lookup"><span data-stu-id="facf2-105">Members</span></span>  
  
|<span data-ttu-id="facf2-106">成员</span><span class="sxs-lookup"><span data-stu-id="facf2-106">Member</span></span>|<span data-ttu-id="facf2-107">描述</span><span class="sxs-lookup"><span data-stu-id="facf2-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="facf2-108">`useLegacyV2RuntimeActivationPolicy` [ \<startup> 元素](../../configure-apps/file-schema/startup/startup-element.md)中不存在该特性。</span><span class="sxs-lookup"><span data-stu-id="facf2-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="facf2-109">`useLegacyV2RuntimeActivationPolicy`特性存在并设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="facf2-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="facf2-110">`useLegacyV2RuntimeActivationPolicy`特性存在并设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="facf2-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="facf2-111">将此掩码应用于在中返回的值，以 `pdwConfigFlags` 获取与相关的值 `useLegacyV2RuntimeActivationPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="facf2-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="facf2-112">备注</span><span class="sxs-lookup"><span data-stu-id="facf2-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facf2-113">要求</span><span class="sxs-lookup"><span data-stu-id="facf2-113">Requirements</span></span>  
 <span data-ttu-id="facf2-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="facf2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facf2-115">**标头：** Metahost</span><span class="sxs-lookup"><span data-stu-id="facf2-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="facf2-116">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="facf2-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="facf2-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facf2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facf2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="facf2-118">See also</span></span>

- [<span data-ttu-id="facf2-119">承载枚举</span><span class="sxs-lookup"><span data-stu-id="facf2-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="facf2-120">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="facf2-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="facf2-121">\<startup> 元素</span><span class="sxs-lookup"><span data-stu-id="facf2-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
