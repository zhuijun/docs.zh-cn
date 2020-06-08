---
title: EClrFailure 枚举
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504389"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure 枚举
描述主机可对其设置策略操作的失败集。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|尝试在非关键的代码区域中分配资源（如线程、内存块或锁定）时出错了。|  
|`FAIL_CriticalResource`|尝试在关键的代码区域中分配资源（如线程、内存块或锁定）时出现错误。|  
|`FAIL_FatalRuntime`|公共语言运行时（CLR）无法再运行进程中的托管代码。 之后，对任何宿主函数的调用都会返回 HOST_E_CLRNOTAVAILABLE 的 HRESULT 值。|  
|`FAIL_OrphanedLock`|在从对象返回时，线程无法释放锁 <xref:System.AppDomain> 。 宿主无法将此失败设置为导致线程中止。|  
|`FAIL_StackOverflow`|发生堆栈溢出。|  
|`FAIL_AccessViolation`|尝试读取或写入受保护的内存。 在 .NET Framework 4 中不受支持。|  
|`FAIL_CodeContract`|发生代码协定失败。 请参阅[代码协定](../../debug-trace-profile/code-contracts.md)。|  
  
## <a name="remarks"></a>注解  
 请参阅[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)方法，以获取[EPolicyAction](epolicyaction-enumeration.md)值的列表，主机可以使用这些值来指定失败情况的策略操作。 有关代码的关键和非关键区域的详细信息，请参阅[EClrOperation](eclroperation-enumeration.md)。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Mscoree.dll  
  
 **库：** Mscoree.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRPolicyManager 接口](iclrpolicymanager-interface.md)
- [SetActionOnFailure 方法](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager 接口](ihostpolicymanager-interface.md)
- [承载枚举](hosting-enumerations.md)
