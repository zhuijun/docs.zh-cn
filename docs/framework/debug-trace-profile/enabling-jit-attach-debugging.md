---
title: 启用 JIT 附加调试
description: 启用实时（JIT）附加调试，在遇到错误时将调试器附加到进程。 它可以由某些方法或函数触发。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416039"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="fae6d-104">启用 JIT 附加调试</span><span class="sxs-lookup"><span data-stu-id="fae6d-104">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="fae6d-105">JIT 附加调试是用于描述如何在发生错误时将调试器附加到进程的词组，它也可以由特定的方法或函数触发。</span><span class="sxs-lookup"><span data-stu-id="fae6d-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="fae6d-106">JIT 附加调试用于以下错误情况：</span><span class="sxs-lookup"><span data-stu-id="fae6d-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="fae6d-107">未经处理的异常（在本机代码和托管代码中）。</span><span class="sxs-lookup"><span data-stu-id="fae6d-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="fae6d-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> 方法或 [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) 函数（Windows 7 系列）。</span><span class="sxs-lookup"><span data-stu-id="fae6d-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="fae6d-109">运行时灾难性错误。</span><span class="sxs-lookup"><span data-stu-id="fae6d-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="fae6d-110">也可通过调用以下方法和函数来触发 JIT 附加调试：</span><span class="sxs-lookup"><span data-stu-id="fae6d-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="fae6d-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="fae6d-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="fae6d-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="fae6d-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="fae6d-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 函数 (Win32)。</span><span class="sxs-lookup"><span data-stu-id="fae6d-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="fae6d-114">在 .NET Framework 4 之前，.NET Framework 提供了单独的注册表项来控制本机调试器和托管调试器的行为。</span><span class="sxs-lookup"><span data-stu-id="fae6d-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="fae6d-115">从 .NET Framework 4 开始，将控件合并到一个注册表项下： HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug。</span><span class="sxs-lookup"><span data-stu-id="fae6d-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="fae6d-116">用户可为该注册表项设置值来确定是否调用调试器，如果调用，则确定是否使用需用户交互的对话框来调用。</span><span class="sxs-lookup"><span data-stu-id="fae6d-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="fae6d-117">有关设置此注册表项的信息，请参阅[配置自动调试](/windows/win32/debug/configuring-automatic-debugging)。</span><span class="sxs-lookup"><span data-stu-id="fae6d-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae6d-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="fae6d-118">See also</span></span>

- [<span data-ttu-id="fae6d-119">调试、跟踪和分析</span><span class="sxs-lookup"><span data-stu-id="fae6d-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="fae6d-120">令映像更易于调试</span><span class="sxs-lookup"><span data-stu-id="fae6d-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
