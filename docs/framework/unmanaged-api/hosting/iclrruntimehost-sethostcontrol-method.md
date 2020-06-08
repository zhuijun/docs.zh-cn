---
title: ICLRRuntimeHost::SetHostControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 644b31ae8e8f0c51c08bcad57220a028406cfd3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504066"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl 方法
设置公共语言运行时（CLR）可用于获取宿主的[IHostControl 接口](ihostcontrol-interface.md)实现的接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>参数  
 `pHostControl`  
 中指向主机的[IHostControl 接口](ihostcontrol-interface.md)实现的接口指针。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|`SetHostControl`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。|  
|HOST_E_TIMEOUT|调用超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|已阻止的线程或纤程正在等待某个事件时，该事件被取消。|  
|E_FAIL|发生未知的灾难性故障。 如果方法返回 E_FAIL，则 CLR 在该进程内将不再可用。 对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。|  
|E_CLR_ALREADY_STARTED|CLR 已初始化。|  
  
## <a name="remarks"></a>注解  
 必须在 `SetHostControl` 初始化 CLR 之前调用，也就是说，在调用[Start 方法](iclrruntimehost-start-method.md)或使用任何[元数据接口](../metadata/metadata-interfaces.md)之前。 建议在 `SetHostControl` 调用[CorBindToCurrentRuntime 函数](corbindtocurrentruntime-function.md)或[CorBindToRuntimeEx 函数](corbindtoruntimeex-function.md)之后立即调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRRuntimeHost 接口](iclrruntimehost-interface.md)
- [IHostControl 接口](ihostcontrol-interface.md)
