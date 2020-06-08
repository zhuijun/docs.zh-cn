---
title: IHostAssemblyManager 接口
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 4e32a36a4cf751bf7c5a2c918fde0122f21b7878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501582"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager 接口
提供一些方法，这些方法允许主机指定应由公共语言运行时（CLR）或主机加载的程序集集。  
  
## <a name="methods"></a>方法  
  
|方法|说明|  
|------------|-----------------|  
|[GetAssemblyStore 方法](ihostassemblymanager-getassemblystore-method.md)|获取一个接口指针，该指针指向表示宿主加载的程序集列表的[IHostAssemblyStore](ihostassemblystore-interface.md) 。|  
|[GetNonHostStoreAssemblies 方法](ihostassemblymanager-getnonhoststoreassemblies-method.md)|获取一个指向[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)的接口指针，该指针表示宿主预期 CLR 加载的程序集的列表。|  
  
## <a name="remarks"></a>注解  
 宿主无需实现 `IHostAssemblyManager` 或 `IHostAssemblyStore` 。 如果主机实现了 `IHostAssemblyManager` ，则它还必须实现 `IHostAssemblyStore` 。  
  
 运行时 `IHostAssemblyManager` 通过在使用 IID_IHostAssemblyManager 的初始化时调用[IHostControl：： GetHostManager](ihostcontrol-gethostmanager-method.md)来查询 `IID` 。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRAssemblyReferenceList 接口](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore 接口](ihostassemblystore-interface.md)
- [IHostControl 接口](ihostcontrol-interface.md)
- [承载接口](hosting-interfaces.md)
