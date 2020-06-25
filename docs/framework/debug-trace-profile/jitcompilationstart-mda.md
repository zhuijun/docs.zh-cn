---
title: jitCompilationStart 托管调试助手（MDA）
description: 当实时（JIT）编译器开始编译 .NET 函数时，jitCompilationStart 托管调试助手（MDA）将进行报告。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325528"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="f8844-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="f8844-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="f8844-104">激活 `jitCompilationStart` 托管调试助手 (MDA) 以报告实时 (MDA) 编译器何时开始编译函数。</span><span class="sxs-lookup"><span data-stu-id="f8844-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f8844-105">症状</span><span class="sxs-lookup"><span data-stu-id="f8844-105">Symptoms</span></span>  
 <span data-ttu-id="f8844-106">由于将 mscorjit.dll 加载到进程中，因此已采用本机映像格式的程序的工作集大小增加。</span><span class="sxs-lookup"><span data-stu-id="f8844-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f8844-107">原因</span><span class="sxs-lookup"><span data-stu-id="f8844-107">Cause</span></span>  
<span data-ttu-id="f8844-108">不是程序所依赖的所有程序集都已生成为本机格式，或者程序集未正确注册。</span><span class="sxs-lookup"><span data-stu-id="f8844-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="f8844-109">解决方法</span><span class="sxs-lookup"><span data-stu-id="f8844-109">Resolution</span></span>  
 <span data-ttu-id="f8844-110">如果启用此 MDA，则可以确定正在 JIT 编译的函数。</span><span class="sxs-lookup"><span data-stu-id="f8844-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="f8844-111">请确保将包含该函数的程序集生成为本机格式并正确注册。</span><span class="sxs-lookup"><span data-stu-id="f8844-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f8844-112">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="f8844-112">Effect on the runtime</span></span>  
 <span data-ttu-id="f8844-113">此 MDA 在方法进行 JIT 编译前记录消息，因此启用此 MDA 会对性能产生重大影响。</span><span class="sxs-lookup"><span data-stu-id="f8844-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="f8844-114">如果方法是内联的，则此 MDA 不会生成单独的消息。</span><span class="sxs-lookup"><span data-stu-id="f8844-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f8844-115">输出</span><span class="sxs-lookup"><span data-stu-id="f8844-115">Output</span></span>  
 <span data-ttu-id="f8844-116">下面的代码示例显示了示例输出。</span><span class="sxs-lookup"><span data-stu-id="f8844-116">The following code sample shows sample output.</span></span> <span data-ttu-id="f8844-117">在这种情况下，输出显示，在程序集测试中，类 "ns2.CO" 上的方法 "m" 是 JIT 编译的。</span><span class="sxs-lookup"><span data-stu-id="f8844-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f8844-118">配置</span><span class="sxs-lookup"><span data-stu-id="f8844-118">Configuration</span></span>  
 <span data-ttu-id="f8844-119">以下配置文件显示多种筛选器，可筛选出首次 JIT 编译时，报告哪些方法。</span><span class="sxs-lookup"><span data-stu-id="f8844-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="f8844-120">您可以通过将 name 特性的值设置为来指定报告所有方法 \* 。</span><span class="sxs-lookup"><span data-stu-id="f8844-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f8844-121">示例</span><span class="sxs-lookup"><span data-stu-id="f8844-121">Example</span></span>  
 <span data-ttu-id="f8844-122">以下示例代码用于上述配置文件。</span><span class="sxs-lookup"><span data-stu-id="f8844-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8844-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8844-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f8844-124">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="f8844-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f8844-125">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="f8844-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
