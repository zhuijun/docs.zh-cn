---
title: COR_PRF_MODULE_FLAGS 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
ms.openlocfilehash: 12e7faa8d9fee7698de9d9734f522d818f225c84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500814"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS 枚举
指定模块的属性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|模块是从磁盘加载的。|  
|COR_PRF_MODULE_NGEN|模块是由本机映像生成器（Ngen.exe）生成的。|  
|COR_PRF_MODULE_DYNAMIC|模块是通过命名空间中的方法创建的 <xref:System.Reflection.Emit?displayProperty=nameWithType> 。|  
|COR_PRF_MODULE_COLLECTIBLE|模块的生存期由垃圾回收器管理。|  
|COR_PRF_MODULE_RESOURCE|该模块不包含元数据，并严格用作资源。 此位的托管等效项是 <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> 方法。|  
|COR_PRF_MODULE_FLAT_LAYOUT|模块在内存中的布局是平面的，而不是映射的。 如果模块设置了此位，则当解释标头中的相对虚拟地址（Rva）时，直接从可移植可执行（PE）文件头读取信息的探查器将必须小心。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|在此模块的程序集的元数据中设置 Windows 运行时内容类型标志。 这适用于所有 Windows 元数据（winmd）模块。|  
  
## <a name="remarks"></a>注解  
 COR_PRF_MODULE_FLAGS 中的位将返回到探查器的 `pdwModuleFlags` [ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法的 output 参数中。 可能有两个或更多标志的一些组合，但并非所有组合都可行。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [分析枚举](profiling-enumerations.md)
