---
title: ICorProfilerCallback::AssemblyLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500437"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished 方法
通知探查器程序集已完成加载。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>参数

- `assemblyId`

  \[in] 标识已加载的程序集。

- `hrStatus`

  \[in] 一个 HRESULT，指示程序集是否已成功加载。

## <a name="remarks"></a>注解  
 在 `assemblyId` 调用方法之前，的值对信息请求无效 `AssemblyLoadFinished` 。  
  
 在回调后，加载程序集的某些部分可能会继续 `AssemblyLoadFinished` 。 中的 HRESULT 失败 `hrStatus` 表示失败。 但是，中的成功 HRESULT `hrStatus` 仅指示加载程序集的第一部分已成功完成。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorProfilerCallback 接口](icorprofilercallback-interface.md)
