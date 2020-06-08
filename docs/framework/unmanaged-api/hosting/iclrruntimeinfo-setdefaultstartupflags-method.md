---
title: ICLRRuntimeInfo::SetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504012"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags 方法
设置启动标志和将用于启动运行时的主机配置文件。 此方法取代了 `startupFlags` [CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函数中的参数使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>参数  
 `dwStartupFlags`  
 中要设置的主机启动标志。 使用与[CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函数相同的标志。  
  
 `pwzHostConfigFile`  
 中要设置的主机配置文件的目录路径。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定的 HRESULT 以及指示方法失败的 HRESULT 错误。  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|该方法已成功完成。|  
  
## <a name="remarks"></a>注解  
 多线程主机应同步对此方法的调用。 否则，线程 A 可能会 `SetStartupFlags` 在线程 b 完成对的调用 `SetStartupFlags` 和线程 b 启动运行时之前调用方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** MetaHost  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRRuntimeInfo 接口](iclrruntimeinfo-interface.md)
- [承载接口](hosting-interfaces.md)
- [承载](index.md)
