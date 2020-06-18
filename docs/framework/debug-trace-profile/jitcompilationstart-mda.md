---
title: jitCompilationStart MDA
description: 使用 jitCompilationStart 托管调试助手（MDA），该助手已开始报告实时（JIT）编译器何时开始编译 .NET 函数。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: bf2d09f433f0b8e4056fecd1f4e82bf3b91dd2bc
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904125"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="e7a65-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="e7a65-103">jitCompilationStart MDA</span></span>
<span data-ttu-id="e7a65-104">激活 `jitCompilationStart` 托管调试助手 (MDA) 以报告实时 (MDA) 编译器何时开始编译函数。</span><span class="sxs-lookup"><span data-stu-id="e7a65-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e7a65-105">症状</span><span class="sxs-lookup"><span data-stu-id="e7a65-105">Symptoms</span></span>  
 <span data-ttu-id="e7a65-106">由于 mscorjit.dll 加载到此进程中，对于已采用本机映像格式的程序，工作集大小增加。</span><span class="sxs-lookup"><span data-stu-id="e7a65-106">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e7a65-107">原因</span><span class="sxs-lookup"><span data-stu-id="e7a65-107">Cause</span></span>  
 <span data-ttu-id="e7a65-108">并非程序依靠的所有程序集均已生成为本机格式，或已生成为本机格式的程序集未正确注册。</span><span class="sxs-lookup"><span data-stu-id="e7a65-108">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e7a65-109">解决方法</span><span class="sxs-lookup"><span data-stu-id="e7a65-109">Resolution</span></span>  
 <span data-ttu-id="e7a65-110">通过启用此 MDA，可确定哪一个函数正在进行 JIT 编译。</span><span class="sxs-lookup"><span data-stu-id="e7a65-110">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="e7a65-111">确定包含此函数的程序集是否生成为本机格式并且正确注册。</span><span class="sxs-lookup"><span data-stu-id="e7a65-111">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e7a65-112">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="e7a65-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="e7a65-113">此 MDA 在方法进行 JIT 编译前记录消息，因此启用此 MDA 会对性能产生重大影响。</span><span class="sxs-lookup"><span data-stu-id="e7a65-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="e7a65-114">请注意，如果方法是内联的，此 MDA 不会生成单独的消息。</span><span class="sxs-lookup"><span data-stu-id="e7a65-114">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e7a65-115">输出</span><span class="sxs-lookup"><span data-stu-id="e7a65-115">Output</span></span>  
 <span data-ttu-id="e7a65-116">下面的代码示例显示了示例输出。</span><span class="sxs-lookup"><span data-stu-id="e7a65-116">The following code sample shows sample output.</span></span> <span data-ttu-id="e7a65-117">在此情况下，输出显示在程序集测试中，类“ns2.CO”上的方法“m”是 JIT 编译。</span><span class="sxs-lookup"><span data-stu-id="e7a65-117">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="e7a65-118">配置</span><span class="sxs-lookup"><span data-stu-id="e7a65-118">Configuration</span></span>  
 <span data-ttu-id="e7a65-119">以下配置文件显示多种筛选器，可筛选出首次 JIT 编译时，报告哪些方法。</span><span class="sxs-lookup"><span data-stu-id="e7a65-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="e7a65-120">您可以通过将 name 特性的值设置为来指定报告所有方法 \* 。</span><span class="sxs-lookup"><span data-stu-id="e7a65-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="e7a65-121">示例</span><span class="sxs-lookup"><span data-stu-id="e7a65-121">Example</span></span>  
 <span data-ttu-id="e7a65-122">以下示例代码用于上述配置文件。</span><span class="sxs-lookup"><span data-stu-id="e7a65-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7a65-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7a65-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e7a65-124">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="e7a65-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e7a65-125">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="e7a65-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
