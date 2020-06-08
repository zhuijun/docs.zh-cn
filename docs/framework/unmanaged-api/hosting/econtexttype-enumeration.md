---
title: EContextType 枚举
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493380"
---
# <a name="econtexttype-enumeration"></a>EContextType 枚举
描述当前正在执行的线程的安全上下文。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`eCurrentContext`|指示公共语言运行时（CLR）在调用[IHostSecurityManager：： SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md)方法的调用中调用[IHostSecurityManager：： GETSECURITYCONTEXT](ihostsecuritymanager-getsecuritycontext-method.md)方法或 CLR 请求的上下文时当前线程上的上下文。|  
|`eRestrictedContext`|指示宿主具有更低权限的上下文，如垃圾回收器或类或模块构造函数。|  
  
## <a name="remarks"></a>注解  
 `EContextType`在对和方法的调用中，CLR 将值之一作为参数值 `IHostSecurityManager::GetSecurityContext` 提供 `IHostSecurityManager::SetSecurityContext` 。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** Mscoree.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [IHostSecurityContext 接口](ihostsecuritycontext-interface.md)
- [IHostSecurityManager 接口](ihostsecuritymanager-interface.md)
- [承载枚举](hosting-enumerations.md)
