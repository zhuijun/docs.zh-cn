---
title: ICLRPolicyManager::SetActionOnFailure 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504103"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure 方法
指定发生指定的故障时公共语言运行时（CLR）应执行的策略操作。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>参数  
 `failure`  
 中[EClrFailure](eclrfailure-enumeration.md)值之一，指示要采取措施的故障类型。  
  
 `action`  
 中[EPolicyAction](epolicyaction-enumeration.md)值之一，指示发生失败时要执行的操作。 有关支持的值的列表，请参阅 "备注" 部分。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。|  
|HOST_E_TIMEOUT|调用超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|已阻止的线程或纤程正在等待某个事件时，该事件被取消。|  
|E_FAIL|发生未知的灾难性故障。 方法返回 E_FAIL 后，CLR 在该进程内将不再可用。 对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|无法为指定的操作设置策略操作，或者为该操作指定了无效的策略操作。|  
  
## <a name="remarks"></a>注解  
 默认情况下，CLR 在无法分配内存等资源时引发异常。 `SetActionOnFailure`允许主机通过指定在失败时要执行的策略操作来重写此行为。 下表显示了支持的[EClrFailure](eclrfailure-enumeration.md)和[EPolicyAction](epolicyaction-enumeration.md)值的组合。 （ [EClrFailure](eclrfailure-enumeration.md)值中省略了 FAIL_ 前缀。）  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||空值||  
|eThrowException|X|X||||空值||  
|`eAbortThread`|X|X||||空值|X|  
|`eRudeAbortThread`|X|X||||空值|X|  
|`eUnloadAppDomain`|X|X||X||空值|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|空值|X|  
|`eExitProcess`|X|X||X|X|空值|X|  
|eFastExitProcess|X|X||X|X|空值||  
|`eRudeExitProcess`|X|X|X|X|X|空值||  
|`eDisableRuntime`|X|X|X|X|X|空值||  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [EClrFailure 枚举](eclrfailure-enumeration.md)
- [EPolicyAction 枚举](epolicyaction-enumeration.md)
- [ICLRControl 接口](iclrcontrol-interface.md)
- [ICLRPolicyManager 接口](iclrpolicymanager-interface.md)
