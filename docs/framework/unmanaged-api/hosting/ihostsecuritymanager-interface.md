---
title: IHostSecurityManager 接口
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 237fe23493460df77a79ba3aed9f0a809cd8aa23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501464"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager 接口
提供允许访问和控制当前正在执行的线程的安全上下文的方法。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[GetSecurityContext 方法](ihostsecuritymanager-getsecuritycontext-method.md)|从主机获取请求的[IHostSecurityContext](ihostsecuritycontext-interface.md) 。|  
|[ImpersonateLoggedOnUser 方法](ihostsecuritymanager-impersonateloggedonuser-method.md)|请求使用当前用户标识的凭据执行代码。|  
|[OpenThreadToken 方法](ihostsecuritymanager-openthreadtoken-method.md)|打开与当前线程关联的自由访问标记。|  
|[RevertToSelf 方法](ihostsecuritymanager-reverttoself-method.md)|终止当前用户标识的模拟并返回原始线程标记。|  
|[SetSecurityContext 方法](ihostsecuritymanager-setsecuritycontext-method.md)|设置当前正在执行的线程的安全上下文。|  
|[SetThreadToken 方法](ihostsecuritymanager-setthreadtoken-method.md)|设置当前正在执行的线程的句柄。|  
  
## <a name="remarks"></a>注解  
 宿主可以通过公共语言运行时（CLR）和用户代码控制对线程标记的所有代码访问。 它还可以确保在异步操作或代码点之间跨受限制的代码访问传递完整的安全上下文信息。 `IHostSecurityContext`封装此安全上下文信息，这对于 CLR 是不透明的。  
  
 CLR 在内部处理托管线程上下文。 它在以下情况下查询特定于进程的 `IHostSecurityManager` ：  
  
- 终结器线程上的终结器执行期间。  
  
- 在类和模块构造函数执行期间。  
  
- 在工作线程上的异步点，调用[IHostThreadPoolManager：： QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)方法。  
  
- 用于 i/o 完成端口的服务。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [IHostSecurityContext 接口](ihostsecuritycontext-interface.md)
- [承载接口](hosting-interfaces.md)
