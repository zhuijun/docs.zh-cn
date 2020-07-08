---
title: memberInfoCacheCreation MDA
description: 了解 .NET 中的 memberInfoCacheCreation 托管调试助手（MDA），它在创建 MemberInfo 缓存时被激活。
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051137"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="887d1-103">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="887d1-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="887d1-104">创建 <xref:System.Reflection.MemberInfo> 缓存时，将激活 `memberInfoCacheCreation` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="887d1-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="887d1-105">这一点强烈表明程序正在使用资源昂贵的反射功能。</span><span class="sxs-lookup"><span data-stu-id="887d1-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="887d1-106">症状</span><span class="sxs-lookup"><span data-stu-id="887d1-106">Symptoms</span></span>  
 <span data-ttu-id="887d1-107">由于程序正在使用资源昂贵的反射，所以程序的工作集增加。</span><span class="sxs-lookup"><span data-stu-id="887d1-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="887d1-108">原因</span><span class="sxs-lookup"><span data-stu-id="887d1-108">Cause</span></span>  
 <span data-ttu-id="887d1-109">将涉及 <xref:System.Reflection.MemberInfo> 对象的反射操作视作资源昂贵的反射，因为这些操作必须读取存储在冷页中的元数据，并且通常指示程序正在使用某种类型的后期绑定方案。</span><span class="sxs-lookup"><span data-stu-id="887d1-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="887d1-110">解决方法</span><span class="sxs-lookup"><span data-stu-id="887d1-110">Resolution</span></span>  
 <span data-ttu-id="887d1-111">先启用此 MDA，再在调试程序中运行代码或在激活 MDA 时附加一个调试程序，即可确定程序中正在使用反射的位置。</span><span class="sxs-lookup"><span data-stu-id="887d1-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="887d1-112">在调试程序下将获得堆栈跟踪，它显示创建 <xref:System.Reflection.MemberInfo> 缓存的位置，从该位置可以确定程序正在使用反射的位置。</span><span class="sxs-lookup"><span data-stu-id="887d1-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="887d1-113">该解决方案依赖代码的目标。</span><span class="sxs-lookup"><span data-stu-id="887d1-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="887d1-114">此 MDA 提醒你，程序具有后期绑定方案。</span><span class="sxs-lookup"><span data-stu-id="887d1-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="887d1-115">可能希望确定能否替换早期绑定方案，或考虑后期绑定方案的性能。</span><span class="sxs-lookup"><span data-stu-id="887d1-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="887d1-116">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="887d1-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="887d1-117">创建的每个 <xref:System.Reflection.MemberInfo> 缓存都可激活此 MDA。</span><span class="sxs-lookup"><span data-stu-id="887d1-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="887d1-118">性能影响可以忽略不计。</span><span class="sxs-lookup"><span data-stu-id="887d1-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="887d1-119">输出</span><span class="sxs-lookup"><span data-stu-id="887d1-119">Output</span></span>  
 <span data-ttu-id="887d1-120">该 MDA 输出一条消息，指示已创建 <xref:System.Reflection.MemberInfo> 缓存。</span><span class="sxs-lookup"><span data-stu-id="887d1-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="887d1-121">使用调试程序器获取堆栈跟踪，堆栈跟踪显示程序正在使用反射的位置。</span><span class="sxs-lookup"><span data-stu-id="887d1-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="887d1-122">配置</span><span class="sxs-lookup"><span data-stu-id="887d1-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="887d1-123">示例</span><span class="sxs-lookup"><span data-stu-id="887d1-123">Example</span></span>  
 <span data-ttu-id="887d1-124">此示例代码将激活 `memberInfoCacheCreation` MDA。</span><span class="sxs-lookup"><span data-stu-id="887d1-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="887d1-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="887d1-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="887d1-126">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="887d1-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
