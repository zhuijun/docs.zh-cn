---
title: IHostPolicyManager 接口
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: d6b34403a45cc40863d79b59396041e496989045
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503921"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager 接口
提供一些方法，这些方法可通知宿主公共语言运行时（CLR）在中止、超时或失败时所执行的操作。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[OnDefaultAction 方法](ihostpolicymanager-ondefaultaction-method.md)|向宿主通知 CLR 将使用对[ICLRPolicyManager：： SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md)的调用指定的默认操作来响应线程中止或 <xref:System.AppDomain> 卸载。|  
|[OnFailure 方法](ihostpolicymanager-onfailure-method.md)|向宿主通知 CLR 即将获取调用[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)所指定的操作，以响应资源分配或回收失败。|  
|[OnTimeout 方法](ihostpolicymanager-ontimeout-method.md)|向宿主通知 CLR 即将使用对[ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)的调用指定的操作来响应超时。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [EClrFailure 枚举](eclrfailure-enumeration.md)
- [EClrOperation 枚举](eclroperation-enumeration.md)
- [EPolicyAction 枚举](epolicyaction-enumeration.md)
- [ICLRPolicyManager 接口](iclrpolicymanager-interface.md)
- [承载接口](hosting-interfaces.md)
