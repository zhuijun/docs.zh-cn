---
title: bindingFailure MDA
description: 阅读有关 bindingFailure 托管调试助手（MDA）的信息，当程序集未能加载到 .NET 中时，将激活该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415623"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="c0738-103">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="c0738-103">bindingFailure MDA</span></span>

<span data-ttu-id="c0738-104">当程序集加载失败时，将激活 `bindingFailure` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="c0738-104">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="c0738-105">症状</span><span class="sxs-lookup"><span data-stu-id="c0738-105">Symptoms</span></span>

<span data-ttu-id="c0738-106">代码已尝试使用静态引用或一种加载程序方法（<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 或 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>）加载程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-106">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0738-107">程序集未加载，且引发 <xref:System.IO.FileNotFoundException> 或 <xref:System.IO.FileLoadException> 异常。</span><span class="sxs-lookup"><span data-stu-id="c0738-107">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="c0738-108">原因</span><span class="sxs-lookup"><span data-stu-id="c0738-108">Cause</span></span>

<span data-ttu-id="c0738-109">当运行时无法加载程序集时，会发生绑定失败。</span><span class="sxs-lookup"><span data-stu-id="c0738-109">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="c0738-110">绑定失败的原因可能是下列情况之一：</span><span class="sxs-lookup"><span data-stu-id="c0738-110">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="c0738-111">公共语言运行时 (CLR) 找不到请求的程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-111">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="c0738-112">导致此问题的原因有很多，如未安装程序集或未正确配置应用程序而无法查找程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-112">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="c0738-113">常见的问题方案是将类型传递给另一个应用程序域，这需要 CLR 加载在其他应用程序域包含该类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-113">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="c0738-114">如果其他应用程序域与原始应用程序域配置不同，那么运行时则不可能加载程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-114">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="c0738-115">例如，两个应用程序域可能具有不同的 <xref:System.AppDomain.BaseDirectory%2A> 属性值。</span><span class="sxs-lookup"><span data-stu-id="c0738-115">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="c0738-116">请求的程序集已损坏或不是程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-116">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="c0738-117">尝试加载程序集的代码没有正确的代码访问安全性权限来加载程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-117">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="c0738-118">用户凭据不提供读取文件所需的权限。</span><span class="sxs-lookup"><span data-stu-id="c0738-118">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="c0738-119">解决方法</span><span class="sxs-lookup"><span data-stu-id="c0738-119">Resolution</span></span>

<span data-ttu-id="c0738-120">第一步是确定 CLR 为何无法绑定到请求的程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-120">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="c0738-121">运行时找不到或无法加载请求的程序集的原因有很多，如“原因”部分中列出的情形。</span><span class="sxs-lookup"><span data-stu-id="c0738-121">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="c0738-122">建议采用以下操作来排除绑定失败的原因：</span><span class="sxs-lookup"><span data-stu-id="c0738-122">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="c0738-123">使用 `bindingFailure` MDA 提供的数据来确定原因：</span><span class="sxs-lookup"><span data-stu-id="c0738-123">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="c0738-124">运行 [Fuslogvw.exe（程序集绑定日志查看器）](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)以读取程序集绑定器生成的错误日志。</span><span class="sxs-lookup"><span data-stu-id="c0738-124">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="c0738-125">确定程序集是否位于请求的位置。</span><span class="sxs-lookup"><span data-stu-id="c0738-125">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="c0738-126">在使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 和 <xref:System.Reflection.Assembly.LoadFile%2A> 方法的情况下，可轻松确定请求的位置。</span><span class="sxs-lookup"><span data-stu-id="c0738-126">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="c0738-127">如果使用 <xref:System.Reflection.Assembly.Load%2A> 方法（利用程序集标识绑定），必须在应用程序域的 <xref:System.AppDomain.BaseDirectory%2A> 属性探测路径和全局程序集缓存中，查找与该标识匹配的程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-127">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="c0738-128">根据上述所确定事项解决失败原因。</span><span class="sxs-lookup"><span data-stu-id="c0738-128">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="c0738-129">可能的解决方案选项如下：</span><span class="sxs-lookup"><span data-stu-id="c0738-129">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="c0738-130">在全局程序集缓存中安装请求的程序集，并调用 </span><span class="sxs-lookup"><span data-stu-id="c0738-130">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="c0738-131"><xref:System.Reflection.Assembly.Load%2A> 方法以按标识加载程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-131"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="c0738-132">将请求的程序集复制到应用程序目录中，并调用 <xref:System.Reflection.Assembly.Load%2A> 方法以按标识加载程序集。</span><span class="sxs-lookup"><span data-stu-id="c0738-132">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="c0738-133">通过更改 <xref:System.AppDomain.BaseDirectory%2A> 属性或添加专用探测路径，重新配置发生绑定失败的应用程序域，以使其包含程序集路径。</span><span class="sxs-lookup"><span data-stu-id="c0738-133">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="c0738-134">更改文件的访问控制列表，以让登录用户读取此文件。</span><span class="sxs-lookup"><span data-stu-id="c0738-134">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="c0738-135">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="c0738-135">Effect on the Runtime</span></span>

<span data-ttu-id="c0738-136">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="c0738-136">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c0738-137">它只报告与绑定失败有关的数据。</span><span class="sxs-lookup"><span data-stu-id="c0738-137">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="c0738-138">输出</span><span class="sxs-lookup"><span data-stu-id="c0738-138">Output</span></span>

<span data-ttu-id="c0738-139">MDA 会报告加载失败的程序集，包括请求的路径和/或显示名称、绑定上下文、请求加载的应用程序域，以及失败的原因。</span><span class="sxs-lookup"><span data-stu-id="c0738-139">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="c0738-140">显示名称或请求的路径可能为空（如果该数据对 CLR 不可用）。</span><span class="sxs-lookup"><span data-stu-id="c0738-140">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="c0738-141">如果失败的调用是对 <xref:System.Reflection.Assembly.Load%2A> 方法的调用，则运行时有可能无法确定程序集的显示名称。</span><span class="sxs-lookup"><span data-stu-id="c0738-141">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="c0738-142">配置</span><span class="sxs-lookup"><span data-stu-id="c0738-142">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="c0738-143">示例</span><span class="sxs-lookup"><span data-stu-id="c0738-143">Example</span></span>

<span data-ttu-id="c0738-144">以下代码示例展示了一种可激活该 MDA 的情况：</span><span class="sxs-lookup"><span data-stu-id="c0738-144">The following code example demonstrates a situation that can activate this MDA:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="c0738-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="c0738-145">See also</span></span>

- [<span data-ttu-id="c0738-146">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="c0738-146">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
