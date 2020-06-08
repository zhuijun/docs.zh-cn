---
title: ICLRMetaHost::GetRuntime 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: d482e25c7bf0f028e2478c8e7b7863bc54d7aeb9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504186"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime 方法
获取与特定版本的公共语言运行时（CLR）相对应的[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)接口。 此方法取代了与[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)标志一起使用的[CorBindToRuntimeEx](corbindtoruntimeex-function.md)函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>参数  
 `pwzVersion`  
 中存储在元数据中的 .NET Framework 编译版本，格式为 "v*A*"。*B.*[。*X*] "。 *A*、 *B*和*X*是与主版本、次版本和生成号对应的十进制数字。  
  
> [!NOTE]
> 此参数必须匹配 .NET Framework 版本的目录名称，因为它显示在 C:\Windows\Microsoft.NET\Framework 或 C:\Windows\Microsoft.NET\Framework64。  
  
 示例值为 "v1.0.3705"、"v 1.1.4322"、"v 2.0.50727" 和 "v4.0"。*X*"，其中*X*依赖于安装的生成号。 "V" 前缀是必需的。  
  
 `riid`  
 中所需接口的标识符。 目前，此参数的唯一有效值是 IID_ICLRRuntimeInfo。  
  
 `ppRuntime`  
 弄指向[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)接口的指针，该接口对应于所请求的运行时。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|说明|  
|-------------|-----------------|  
|S_OK|该方法已成功完成。|  
|E_POINTER|`pwzVersion` 或 `ppRuntime` 为 null。|  
  
## <a name="remarks"></a>注解  
 此方法与旧接口（如[ICorRuntimeHost](icorruntimehost-interface.md)接口）和旧功能（如已弃用的函数）一致地进行交互 `CorBindTo*` （请参阅 .NET FRAMEWORK 2.0 托管 API 中[弃用的 CLR 承载函数](deprecated-clr-hosting-functions.md)）。 也就是说，用旧版 API 加载的运行时对新 API 可见，而与新 API 一起加载的运行时对旧 API 可见。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** MetaHost  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRMetaHost 接口](iclrmetahost-interface.md)
- [弃用的 CLR 承载接口和 Coclass](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR 承载接口](clr-hosting-interfaces.md)
- [弃用的 CLR 承载函数](deprecated-clr-hosting-functions.md)
- [承载](index.md)
