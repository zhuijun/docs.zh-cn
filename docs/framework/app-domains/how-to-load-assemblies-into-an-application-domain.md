---
title: 如何：将程序集加载到应用程序域中
description: 了解如何在 .NET 中将程序集加载到应用程序域。 建议使用 System.Reflection.Assembly 中的静态（或共享）加载方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c91c70625b79002e9297755dfdfac8aa6e283208
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104760"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="19d42-104">如何：将程序集加载到应用程序域中</span><span class="sxs-lookup"><span data-stu-id="19d42-104">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="19d42-105">可通过多种方法将程序集加载到应用程序域中。</span><span class="sxs-lookup"><span data-stu-id="19d42-105">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="19d42-106">推荐方法是使用 <xref:System.Reflection.Assembly?displayProperty=nameWithType> 类的 `static`（在 Visual Basic 中为 `Shared`）<xref:System.Reflection.Assembly.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="19d42-106">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="19d42-107">加载程序集的其他方法包括：</span><span class="sxs-lookup"><span data-stu-id="19d42-107">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="19d42-108"><xref:System.Reflection.Assembly> 类的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法加载已给定其文件位置的程序集。</span><span class="sxs-lookup"><span data-stu-id="19d42-108">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="19d42-109">通过此方法加载程序集将使用不同的加载上下文。</span><span class="sxs-lookup"><span data-stu-id="19d42-109">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="19d42-110"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 和 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法将程序集加载到仅反射上下文中。</span><span class="sxs-lookup"><span data-stu-id="19d42-110">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="19d42-111">可检查但不可执行加载到该上下文中的程序集，允许检查以其他平台为目标的程序集。</span><span class="sxs-lookup"><span data-stu-id="19d42-111">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="19d42-112">请参阅[如何：将程序集加载到仅反射上下文中](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。</span><span class="sxs-lookup"><span data-stu-id="19d42-112">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19d42-113">仅反射上下文是 .NET Framework 2.0 版中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="19d42-113">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="19d42-114"><xref:System.AppDomain> 类的 <xref:System.AppDomain.CreateInstance%2A> 和 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 等方法可将程序集加载到应用程序域中。</span><span class="sxs-lookup"><span data-stu-id="19d42-114">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="19d42-115"><xref:System.Type> 类的 <xref:System.Type.GetType%2A> 方法可加载程序集。</span><span class="sxs-lookup"><span data-stu-id="19d42-115">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="19d42-116"><xref:System.AppDomain?displayProperty=nameWithType> 类的 <xref:System.AppDomain.Load%2A> 方法可加载程序集，但主要用于实现 COM 互操作性。</span><span class="sxs-lookup"><span data-stu-id="19d42-116">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="19d42-117">不应使用该方法将程序集加载到除从其中调用该方法的应用程序域以外的其他应用程序域。</span><span class="sxs-lookup"><span data-stu-id="19d42-117">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19d42-118">从 .NET Framework 2.0 版开始，对于使用版本号高于当前已加载运行时的 .NET Framework 版本所编译的程序集，运行时将不再加载此类程序集。</span><span class="sxs-lookup"><span data-stu-id="19d42-118">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="19d42-119">这同样适用于主版本号和次版本号的组合。</span><span class="sxs-lookup"><span data-stu-id="19d42-119">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="19d42-120">可指定在应用程序域间共享已加载程序集的实时 (JIT) 编译代码的方式。</span><span class="sxs-lookup"><span data-stu-id="19d42-120">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="19d42-121">有关详细信息，请参阅[应用程序域和程序集](application-domains.md#application-domains-and-assemblies)。</span><span class="sxs-lookup"><span data-stu-id="19d42-121">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19d42-122">示例</span><span class="sxs-lookup"><span data-stu-id="19d42-122">Example</span></span>  
 <span data-ttu-id="19d42-123">以下代码将名为“example.exe”或“example.dll”的程序集加载到当前应用程序域中，从该程序集获取名为 `Example` 的类型，为该类型获取名为 `MethodA` 的参数方法，然后执行该方法。</span><span class="sxs-lookup"><span data-stu-id="19d42-123">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="19d42-124">有关从已加载程序集中获取信息的完整讨论，请参阅[动态加载和使用类型](../reflection-and-codedom/dynamically-loading-and-using-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19d42-124">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="19d42-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="19d42-125">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="19d42-126">对应用程序域进行编程</span><span class="sxs-lookup"><span data-stu-id="19d42-126">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="19d42-127">反射</span><span class="sxs-lookup"><span data-stu-id="19d42-127">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="19d42-128">使用应用程序域</span><span class="sxs-lookup"><span data-stu-id="19d42-128">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="19d42-129">如何：将程序集加载到仅反射上下文中</span><span class="sxs-lookup"><span data-stu-id="19d42-129">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="19d42-130">应用程序域和程序集</span><span class="sxs-lookup"><span data-stu-id="19d42-130">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
