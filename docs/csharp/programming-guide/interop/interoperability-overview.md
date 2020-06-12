---
title: 互操作性概述 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 6546a379d6d851aafbced0931221dc19ca022a72
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241729"
---
# <a name="interoperability-overview-c-programming-guide"></a><span data-ttu-id="13e7a-102">互操作性概述（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="13e7a-102">Interoperability Overview (C# Programming Guide)</span></span>
<span data-ttu-id="13e7a-103">本主题描述在 C# 托管代码和非托管代码之间实现互操作性的方法。</span><span class="sxs-lookup"><span data-stu-id="13e7a-103">The topic describes methods to enable interoperability between C# managed code and unmanaged code.</span></span>  
  
## <a name="platform-invoke"></a><span data-ttu-id="13e7a-104">平台调用</span><span class="sxs-lookup"><span data-stu-id="13e7a-104">Platform Invoke</span></span>  
 <span data-ttu-id="13e7a-105">平台调用是一项服务，它使托管代码能够调用动态链接库 (DLL) 中实现的非托管函数，例如 Microsoft Windows API 中的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="13e7a-105">*Platform invoke* is a service that enables managed code to call unmanaged functions that are implemented in dynamic link libraries (DLLs), such as those in the Microsoft Windows API.</span></span> <span data-ttu-id="13e7a-106">此服务定位并调用导出的函数，并根据需要跨交互操作边界封送其自变量（整数、字符串、数组、结构等）。</span><span class="sxs-lookup"><span data-stu-id="13e7a-106">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
<span data-ttu-id="13e7a-107">有关详细信息，请参阅[使用非托管 DLL 函数](../../../framework/interop/consuming-unmanaged-dll-functions.md)和[如何使用平台调用播放 WAV 文件](./how-to-use-platform-invoke-to-play-a-wave-file.md)。</span><span class="sxs-lookup"><span data-stu-id="13e7a-107">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md) and [How to use platform invoke to play a WAV file](./how-to-use-platform-invoke-to-play-a-wave-file.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="13e7a-108">[公共语言运行时](../../../standard/clr.md) (CLR) 管理对系统资源的访问。</span><span class="sxs-lookup"><span data-stu-id="13e7a-108">The [Common Language Runtime](../../../standard/clr.md) (CLR) manages access to system resources.</span></span> <span data-ttu-id="13e7a-109">调用 CLR 外部的非托管代码将避开这种安全机制，因此会带来安全风险。</span><span class="sxs-lookup"><span data-stu-id="13e7a-109">Calling unmanaged code that is outside the CLR bypasses this security mechanism, and therefore presents a security risk.</span></span> <span data-ttu-id="13e7a-110">例如，非托管代码可能直接调用非托管代码中的资源，从而避开 CLR 安全机制。</span><span class="sxs-lookup"><span data-stu-id="13e7a-110">For example, unmanaged code might call resources in unmanaged code directly, bypassing CLR security mechanisms.</span></span> <span data-ttu-id="13e7a-111">有关详细信息，请参阅 [ .NET 中的安全性](../../../standard/security/index.md)。</span><span class="sxs-lookup"><span data-stu-id="13e7a-111">For more information, see [Security in .NET](../../../standard/security/index.md).</span></span>  
  
## <a name="c-interop"></a><span data-ttu-id="13e7a-112">C++ 互操作</span><span class="sxs-lookup"><span data-stu-id="13e7a-112">C++ Interop</span></span>  
 <span data-ttu-id="13e7a-113">可使用 C++ interop（又称为 It Just Works (IJW)）包装本机 C++ 类，以便用 C# 或其他 .NET 语言编写的代码可以使用此类。</span><span class="sxs-lookup"><span data-stu-id="13e7a-113">You can use C++ interop, also known as It Just Works (IJW), to wrap a native C++ class so that it can be consumed by code that is authored in C# or another .NET language.</span></span> <span data-ttu-id="13e7a-114">为此，请编写 C++ 代码来包装本机 DLL 或 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="13e7a-114">To do this, you write C++ code to wrap a native DLL or COM component.</span></span> <span data-ttu-id="13e7a-115">与其他 .NET 语言不同，Visual C++ 具有互操作性支持，可使托管和非托管代码放置在同一个应用程序（甚至同一个文件）中。</span><span class="sxs-lookup"><span data-stu-id="13e7a-115">Unlike other .NET languages, Visual C++ has interoperability support that enables managed and unmanaged code to be located in the same application and even in the same file.</span></span> <span data-ttu-id="13e7a-116">然后使用 **/clr** 编译器开关生成托管程序集，以便生成 C++ 代码。</span><span class="sxs-lookup"><span data-stu-id="13e7a-116">You then build the C++ code by using the **/clr** compiler switch to produce a managed assembly.</span></span> <span data-ttu-id="13e7a-117">最后，在 C# 项目中添加一个对该程序集的引用，并像使用其他托管类那样使用被包装对象。</span><span class="sxs-lookup"><span data-stu-id="13e7a-117">Finally, you add a reference to the assembly in your C# project and use the wrapped objects just as you would use other managed classes.</span></span>  
  
## <a name="exposing-com-components-to-c"></a><span data-ttu-id="13e7a-118">向 C\# 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="13e7a-118">Exposing COM Components to C\#</span></span>
 <span data-ttu-id="13e7a-119">可以使用 C# 项目中的 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="13e7a-119">You can consume a COM component from a C# project.</span></span> <span data-ttu-id="13e7a-120">常规步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="13e7a-120">The general steps are as follows:</span></span>  
  
1. <span data-ttu-id="13e7a-121">找到要使用的 COM 组件并注册。</span><span class="sxs-lookup"><span data-stu-id="13e7a-121">Locate a COM component to use and register it.</span></span> <span data-ttu-id="13e7a-122">使用 regsvr32.exe 注册或注销 COM DLL。</span><span class="sxs-lookup"><span data-stu-id="13e7a-122">Use regsvr32.exe to register or un–register a COM DLL.</span></span>  
  
2. <span data-ttu-id="13e7a-123">向项目添加对 COM 组件或类型库的引用。</span><span class="sxs-lookup"><span data-stu-id="13e7a-123">Add to the project a reference to the COM component or type library.</span></span>  
  
     <span data-ttu-id="13e7a-124">添加引用时，Visual Studio 使用 [Tlbimp.exe（类型库导入程序）](../../../framework/tools/tlbimp-exe-type-library-importer.md)。此程序需要使用类型库作为输入，以输出 .NET 互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="13e7a-124">When you add the reference, Visual Studio uses the [Tlbimp.exe (Type Library Importer)](../../../framework/tools/tlbimp-exe-type-library-importer.md), which takes a type library as input, to output a .NET interop assembly.</span></span> <span data-ttu-id="13e7a-125">该程序集又称为运行时可调用包装器 (RCW)，其中包含包装类型库中的 COM 类和接口的托管类和接口。</span><span class="sxs-lookup"><span data-stu-id="13e7a-125">The assembly, also named a runtime callable wrapper (RCW), contains managed classes and interfaces that wrap the COM classes and interfaces that are in the type library.</span></span> <span data-ttu-id="13e7a-126">Visual Studio 向项目添加对生成程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="13e7a-126">Visual Studio adds to the project a reference to the generated assembly.</span></span>  
  
3. <span data-ttu-id="13e7a-127">创建在 RCW 中定义的类的实例。</span><span class="sxs-lookup"><span data-stu-id="13e7a-127">Create an instance of a class that is defined in the RCW.</span></span> <span data-ttu-id="13e7a-128">这会创建 COM 对象的实例。</span><span class="sxs-lookup"><span data-stu-id="13e7a-128">This, in turn, creates an instance of the COM object.</span></span>  
  
4. <span data-ttu-id="13e7a-129">像使用其他托管对象那样使用该对象。</span><span class="sxs-lookup"><span data-stu-id="13e7a-129">Use the object just as you use other managed objects.</span></span> <span data-ttu-id="13e7a-130">当垃圾回收对该对象进行回收后，COM 对象的实例也会从内存中释放出来。</span><span class="sxs-lookup"><span data-stu-id="13e7a-130">When the object is reclaimed by garbage collection, the instance of the COM object is also released from memory.</span></span>  
  
 <span data-ttu-id="13e7a-131">有关详细信息，请参阅[向 .NET Framework 公开 COM 组件](../../../framework/interop/exposing-com-components.md)。</span><span class="sxs-lookup"><span data-stu-id="13e7a-131">For more information, see [Exposing COM Components to the .NET Framework](../../../framework/interop/exposing-com-components.md).</span></span>  
  
## <a name="exposing-c-to-com"></a><span data-ttu-id="13e7a-132">向 COM 公开 C#</span><span class="sxs-lookup"><span data-stu-id="13e7a-132">Exposing C# to COM</span></span>  
 <span data-ttu-id="13e7a-133">COM 客户端可以使用已经正确公开的 C# 类型。</span><span class="sxs-lookup"><span data-stu-id="13e7a-133">COM clients can consume C# types that have been correctly exposed.</span></span> <span data-ttu-id="13e7a-134">公开 C# 类型的基本步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="13e7a-134">The basic steps to expose C# types are as follows:</span></span>  
  
1. <span data-ttu-id="13e7a-135">在 C# 项目中添加互操作特性。</span><span class="sxs-lookup"><span data-stu-id="13e7a-135">Add interop attributes in the C# project.</span></span>  
  
     <span data-ttu-id="13e7a-136">可通过修改 Visual C# 项目属性使程序集 COM 可见。</span><span class="sxs-lookup"><span data-stu-id="13e7a-136">You can make an assembly COM visible by modifying Visual C# project properties.</span></span> <span data-ttu-id="13e7a-137">有关详细信息，请参阅[“程序集信息”对话框](/visualstudio/ide/reference/assembly-information-dialog-box)。</span><span class="sxs-lookup"><span data-stu-id="13e7a-137">For more information, see [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box).</span></span>  
  
2. <span data-ttu-id="13e7a-138">生成 COM 类型库并对它进行注册以供 COM 使用。</span><span class="sxs-lookup"><span data-stu-id="13e7a-138">Generate a COM type library and register it for COM usage.</span></span>  
  
     <span data-ttu-id="13e7a-139">可修改 Visual C# 项目属性以自动注册 COM 互操作的 C# 程序集。</span><span class="sxs-lookup"><span data-stu-id="13e7a-139">You can modify Visual C# project properties to automatically register the C# assembly for COM interop.</span></span> <span data-ttu-id="13e7a-140">Visual Studio 通过 `/tlb` 命令行开关使用 [Regasm.exe（程序集注册工具）](../../../framework/tools/regasm-exe-assembly-registration-tool.md)。此工具使用托管组件作为输入，以生成类型库。</span><span class="sxs-lookup"><span data-stu-id="13e7a-140">Visual Studio uses the [Regasm.exe (Assembly Registration Tool)](../../../framework/tools/regasm-exe-assembly-registration-tool.md), using the `/tlb` command-line switch, which takes a managed assembly as input, to generate a type library.</span></span> <span data-ttu-id="13e7a-141">此类型库描述程序集中的 `public` 类型并添加注册表项，以便 COM 客户端可以创建托管类。</span><span class="sxs-lookup"><span data-stu-id="13e7a-141">This type library describes the `public` types in the assembly and adds registry entries so that COM clients can create managed classes.</span></span>  
  
 <span data-ttu-id="13e7a-142">有关详细信息，请参阅[向 COM 公开 .NET Framework 组件](../../../framework/interop/exposing-dotnet-components-to-com.md)和 [COM 类示例](./example-com-class.md)。</span><span class="sxs-lookup"><span data-stu-id="13e7a-142">For more information, see [Exposing .NET Framework Components to COM](../../../framework/interop/exposing-dotnet-components-to-com.md) and [Example COM Class](./example-com-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e7a-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="13e7a-143">See also</span></span>

- <span data-ttu-id="13e7a-144">[Improving Interop Performance](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)（提高互操作性能）</span><span class="sxs-lookup"><span data-stu-id="13e7a-144">[Improving Interop Performance](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)</span></span>
- [<span data-ttu-id="13e7a-145">COM 和 .NET 之间的互操作性简介</span><span class="sxs-lookup"><span data-stu-id="13e7a-145">Introduction to Interoperability between COM and .NET</span></span>](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [<span data-ttu-id="13e7a-146">Visual Basic 中的 COM 互操作简介</span><span class="sxs-lookup"><span data-stu-id="13e7a-146">Introduction to COM Interop in Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [<span data-ttu-id="13e7a-147">托管代码与非托管代码之间的封送处理</span><span class="sxs-lookup"><span data-stu-id="13e7a-147">Marshaling between Managed and Unmanaged Code</span></span>](../../../framework/interop/interop-marshaling.md)
- [<span data-ttu-id="13e7a-148">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="13e7a-148">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="13e7a-149">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="13e7a-149">C# Programming Guide</span></span>](../index.md)
