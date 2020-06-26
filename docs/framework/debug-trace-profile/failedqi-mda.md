---
title: failedQI MDA
description: 查看 .NET 中的 failedQI 托管调试助手（MDA），当或来自运行时可调用包装（RCW）的 COM 调用失败时，这可能会被激活。
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415935"
---
# <a name="failedqi-mda"></a>failedQI MDA
当运行时代表运行时可调用包装器 (RCW) 在 COM 接口指针上调用 `QueryInterface` 且 `QueryInterface` 调用失败时，将激活 `failedQI` 托管调试助手 (MDA)。  
  
## <a name="symptoms"></a>症状  
 对 RCW 的强制转换失败，或从 RCW 调用 COM 意外失败。  
  
## <a name="cause"></a>原因  
  
- 从错误的上下文进行调用。  
  
- 注册的代理将无法进行 `QueryInterface` 调用，因为尝试在错误的上下文中进行调用。  
  
- OLE 拥有的代理返回失败 HRESULT。  
  
## <a name="resolution"></a>解决方法  
 请参阅 MSDN 文档的 COM 规则部分。  
  
## <a name="effect-on-the-runtime"></a>对运行时的影响  
 如果 `QueryInterface` 调用失败，将切换上下文并再次尝试调用`QueryInterface`，以确定是否因上下文错误而引起。  
  
## <a name="output"></a>输出  
 接口的托管名称、接口的 GUID 和失败的 HRESULT。  
  
## <a name="configuration"></a>配置  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用托管调试助手诊断错误](diagnosing-errors-with-managed-debugging-assistants.md)
- [互操作封送处理](../interop/interop-marshaling.md)
