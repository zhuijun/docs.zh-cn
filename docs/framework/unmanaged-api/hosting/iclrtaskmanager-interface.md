---
title: ICLRTaskManager 接口
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: f918d4e7b95922734d70ed832581e6c494c70b05
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501633"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager 接口
提供允许主机显式请求公共语言运行时（CLR）创建新任务、获取当前正在执行的任务以及设置任务的地理语言和区域性的方法。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[CreateTask 方法](iclrtaskmanager-createtask-method.md)|显式请求 CLR 创建新的[ICLRTask](iclrtask-interface.md)实例。|  
|[GetCurrentTask 方法](iclrtaskmanager-getcurrenttask-method.md)|获取 `ICLRTask` 表示当前正在执行的任务的实例。|  
|[GetCurrentTaskType 方法](iclrtaskmanager-getcurrenttasktype-method.md)|获取当前正在执行的任务的类型。|  
|[SetLocale 方法](iclrtaskmanager-setlocale-method.md)|通知 CLR 宿主已经修改了当前正在执行的任务的区域设置标识符。|  
|[SetUILocale 方法](iclrtaskmanager-setuilocale-method.md)|通知公共语言运行时宿主已经修改了当前正在执行的任务的用户界面区域设置标识符。|  
  
## <a name="remarks"></a>注解  
 宿主环境中运行的每个任务在主机端（ [IHostTask](ihosttask-interface.md)的实例）和 CLR 端（ [ICLRTask](iclrtask-interface.md)的一个实例）上都具有表示形式。 宿主或 CLR 可以启动任务创建，但宿主端表示形式必须与相应的 CLR 端表示形式相关联，以确保主机与 CLR 之间的有关任务的通信成功。 必须先创建并实例化两个对象，然后托管代码才能在操作系统线程上执行。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRTask 接口](iclrtask-interface.md)
- [IHostTask 接口](ihosttask-interface.md)
- [IHostTaskManager 接口](ihosttaskmanager-interface.md)
- [承载接口](hosting-interfaces.md)
