---
title: dllMainReturnsFalse MDA
description: 了解 .NET 中的 dllMainReturnsFalse 托管调试助手。 如果 DLL 初始化失败，则会激活此 MDA。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416052"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="9a8ab-104">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="9a8ab-104">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="9a8ab-105">如果用户程序集的托管 `DllMain` 函数（因 DLL_PROCESS_ATTACH 原因而调用）返回 FALSE，则将激活 `dllMainReturnsFalse` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9a8ab-106">症状</span><span class="sxs-lookup"><span data-stu-id="9a8ab-106">Symptoms</span></span>  
 <span data-ttu-id="9a8ab-107">`DllMain` 函数返回 FALSE，表示其未正确执行。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="9a8ab-108">这会导致一些未确定的问题，因为 `DllMain` 函数通常包含重要的初始化代码。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9a8ab-109">原因</span><span class="sxs-lookup"><span data-stu-id="9a8ab-109">Cause</span></span>  
 <span data-ttu-id="9a8ab-110">因 DLL_PROCESS_ATTACH 原因调用 `DllMain` 函数，在上传时初始化 DLL。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="9a8ab-111">如果它返回 FALSE，则意味着该 DLL 初始化失败。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9a8ab-112">解决方法</span><span class="sxs-lookup"><span data-stu-id="9a8ab-112">Resolution</span></span>  
 <span data-ttu-id="9a8ab-113">分析失败的 DLL 的 `DllMain` 函数的代码，找出初始化失败的原因。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9a8ab-114">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="9a8ab-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="9a8ab-115">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9a8ab-116">它只报告有关 `DllMain` 的返回值的数据。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9a8ab-117">输出</span><span class="sxs-lookup"><span data-stu-id="9a8ab-117">Output</span></span>  
 <span data-ttu-id="9a8ab-118">一条指示 `DllMain` 函数（因 DLL_PROCESS_ATTACH 原因调用）返回 FALSE 的消息。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="9a8ab-119">请注意，此 MDA 仅在托管代码中实现 `DllMain` 时才激活。</span><span class="sxs-lookup"><span data-stu-id="9a8ab-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9a8ab-120">配置</span><span class="sxs-lookup"><span data-stu-id="9a8ab-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a8ab-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="9a8ab-121">See also</span></span>

- [<span data-ttu-id="9a8ab-122">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="9a8ab-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
