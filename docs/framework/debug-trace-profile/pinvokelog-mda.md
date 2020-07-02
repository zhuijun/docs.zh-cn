---
title: pInvokeLog MDA
description: 了解 pInvokeLog 托管调试助手（MDA），该助手为在 .NET 中执行过程中使用的每个唯一平台调用签名激活。
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803685"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="e3198-103">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="e3198-103">pInvokeLog MDA</span></span>
<span data-ttu-id="e3198-104">`pInvokeLog` 托管调试助手 (MDA) 会为执行期间使用的每个唯一平台调用签名而激活。</span><span class="sxs-lookup"><span data-stu-id="e3198-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e3198-105">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="e3198-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="e3198-106">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="e3198-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e3198-107">Output</span><span class="sxs-lookup"><span data-stu-id="e3198-107">Output</span></span>  
 <span data-ttu-id="e3198-108">指示执行期间使用的平台调用签名的消息。</span><span class="sxs-lookup"><span data-stu-id="e3198-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e3198-109">Configuration</span><span class="sxs-lookup"><span data-stu-id="e3198-109">Configuration</span></span>  
 <span data-ttu-id="e3198-110">每个匹配元素筛选平台调用将进行调用的 .dll 文件。</span><span class="sxs-lookup"><span data-stu-id="e3198-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3198-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="e3198-111">See also</span></span>

- [<span data-ttu-id="e3198-112">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="e3198-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e3198-113">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="e3198-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
