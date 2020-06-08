---
title: ICorProfilerCallback::Shutdown 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: f6873de1a864489d144a671b1a9e1349eaf77d15
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503171"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown 方法
通知探查器应用程序正在关闭。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>备注  
 调用方法后，探查器代码无法安全调用[ICorProfilerInfo](icorprofilerinfo-interface.md)接口的方法 `Shutdown` 。 对方法的任何调用都会 `ICorProfilerInfo` 导致在方法返回后出现未定义的行为 `Shutdown` 。 某些不可变事件可能仍会在关闭后发生;此事件发生时，探查器应小心立即返回。  
  
 `Shutdown`仅当要分析的托管应用程序作为托管代码启动时（即，处理堆栈上的初始帧是托管的），将调用方法。 如果应用程序启动为非托管代码，但后来跳转到托管代码，从而创建公共语言运行时（CLR）的实例，则 `Shutdown` 不会调用。 对于这些情况，探查器应在其库中包含一个 `DllMain` 例程，该例程使用 DLL_PROCESS_DETACH 值来释放所有资源并对其数据执行清理处理，如将跟踪刷新到磁盘等。  
  
 通常，探查器必须处理意外关闭。 例如，进程可能由 Win32 `TerminateProcess` 方法（在 winbase.h 中声明）暂停。 在其他情况下，CLR 将暂停某些托管线程（后台线程），而无需为它们传递有序的析构消息。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorProfilerCallback 接口](icorprofilercallback-interface.md)
- [Initialize 方法](icorprofilercallback-initialize-method.md)
