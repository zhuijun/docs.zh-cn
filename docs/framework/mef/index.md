---
title: Managed Extensibility Framework (MEF)
description: 探索 Managed Extensibility Framework (MEF)，它可便于应用程序开发人员发现并使用扩展，而无需在 .NET 4 或更高版本中进行配置。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: b743a26dd401e7015c588be2a197551aa891a687
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555570"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="dcce0-103">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="dcce0-103">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="dcce0-104">该话题为在 .NET Framework 4 中引入的 Managed Extensibility Framework 提供了一个概述。</span><span class="sxs-lookup"><span data-stu-id="dcce0-104">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="dcce0-105">什么是 MEF？</span><span class="sxs-lookup"><span data-stu-id="dcce0-105">What is MEF?</span></span>

<span data-ttu-id="dcce0-106">Managed Extensibility Framework (MEF) 是用于创建可扩展的轻量级应用程序的库。</span><span class="sxs-lookup"><span data-stu-id="dcce0-106">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="dcce0-107">它让应用程序开发人员得以发现和使用扩展且无需配置。</span><span class="sxs-lookup"><span data-stu-id="dcce0-107">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="dcce0-108">它还让扩展开发人员得以轻松地封装代码并避免脆弱的紧密依赖性。</span><span class="sxs-lookup"><span data-stu-id="dcce0-108">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="dcce0-109">MEF 让扩展不仅可在应用程序内重复使用，还可以跨程序重复使用。</span><span class="sxs-lookup"><span data-stu-id="dcce0-109">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="dcce0-110">扩展性问题</span><span class="sxs-lookup"><span data-stu-id="dcce0-110">The problem of extensibility</span></span>

<span data-ttu-id="dcce0-111">想象你是必须为扩展性提供支持的大型应用程序的设计者。</span><span class="sxs-lookup"><span data-stu-id="dcce0-111">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="dcce0-112">你的应用程序必须包含可能很多的较小组件，且其负责创建和运行较小组件。</span><span class="sxs-lookup"><span data-stu-id="dcce0-112">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="dcce0-113">解决问题最简单的方法就是将组件作为源代码包括在你的应用程序并直接从代码中调用它们。</span><span class="sxs-lookup"><span data-stu-id="dcce0-113">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="dcce0-114">这有很多明显缺点。</span><span class="sxs-lookup"><span data-stu-id="dcce0-114">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="dcce0-115">最重要的是，你无法在未调试源代码的情况下添加新组件，这是一项可能被接受的限制（例如在 Web 应用程序中），但不适用于客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="dcce0-115">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="dcce0-116">同样造成问题的是，你无法访问组件的源代码，因为组件可能由第三方进行了发展，同时由于同样的原因你不能允许第三方访问你的源代码。</span><span class="sxs-lookup"><span data-stu-id="dcce0-116">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="dcce0-117">一个稍许复杂的方法为提供扩展点或接口来允许应用程序和组件间的分离。</span><span class="sxs-lookup"><span data-stu-id="dcce0-117">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="dcce0-118">在此模块下，你可能提供组件可实现的接口以及使接口能与应用程序交互使用的 API。</span><span class="sxs-lookup"><span data-stu-id="dcce0-118">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="dcce0-119">这解决了要求源代码访问的问题，但它仍然存在自身问题。</span><span class="sxs-lookup"><span data-stu-id="dcce0-119">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="dcce0-120">因为应用程序缺少自行发现组件的能力，所以必须明确对其指出可用且应加载的组件。</span><span class="sxs-lookup"><span data-stu-id="dcce0-120">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="dcce0-121">这通常通过在配置文件中明确记录可用组件来完成。</span><span class="sxs-lookup"><span data-stu-id="dcce0-121">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="dcce0-122">这意味着确保组件正确变成了维护问题，尤其当要求执行更新的人员是最终用户而非开发人员时。</span><span class="sxs-lookup"><span data-stu-id="dcce0-122">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="dcce0-123">此外，组件能够与另外的组件进行沟通，除了通过应用程序自身的严格定义的通道。</span><span class="sxs-lookup"><span data-stu-id="dcce0-123">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="dcce0-124">通常不会出现应用程序设计者未预测到特定通信的需求的情况。</span><span class="sxs-lookup"><span data-stu-id="dcce0-124">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="dcce0-125">最终，组件开发人员必须接受包含他们实现的接口的程序集所在的硬依赖项。</span><span class="sxs-lookup"><span data-stu-id="dcce0-125">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="dcce0-126">这使得在一个以上的应用程序中使用组件变得困难，且它还会在你创建组件的测试框架时造成问题。</span><span class="sxs-lookup"><span data-stu-id="dcce0-126">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="dcce0-127">MEF 所含内容</span><span class="sxs-lookup"><span data-stu-id="dcce0-127">What MEF provides</span></span>

<span data-ttu-id="dcce0-128">MEF 通过组合提供了一种隐式发现它们的方法，而不是明确记录可用组件。</span><span class="sxs-lookup"><span data-stu-id="dcce0-128">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="dcce0-129">MEF 组件（称为一个部件），以声明方式详细说明了其依赖项（称为导入）及其可提供的功能（称为导出）。</span><span class="sxs-lookup"><span data-stu-id="dcce0-129">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="dcce0-130">当创建一个部分时，MEF 组合引擎利用从其他部分获得的功能满足其导入需要。</span><span class="sxs-lookup"><span data-stu-id="dcce0-130">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="dcce0-131">该方法解决了在之前部分中讨论的问题。</span><span class="sxs-lookup"><span data-stu-id="dcce0-131">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="dcce0-132">因为 MEF 部分以声明方式详细说明了其可在运行时发现自身的功能，这意味着应用程序不使用硬编码引用或脆弱的配置文件也能够使用 MEF 部分。</span><span class="sxs-lookup"><span data-stu-id="dcce0-132">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="dcce0-133">MEF 让应用程序得以通过元数据发现和检查部分，而无须将部分实例化甚至于加载其程序集。</span><span class="sxs-lookup"><span data-stu-id="dcce0-133">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="dcce0-134">因此，无须仔细说明应当何时加载扩展以及如何加载。</span><span class="sxs-lookup"><span data-stu-id="dcce0-134">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="dcce0-135">除了它提供的导出之外，部件能够指出其导入（将由其他部件填写）。</span><span class="sxs-lookup"><span data-stu-id="dcce0-135">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="dcce0-136">这不仅使部件之间的通信成为可能还使其变得简单，并且实现了良好的代码分解。</span><span class="sxs-lookup"><span data-stu-id="dcce0-136">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="dcce0-137">例如，对于许多组件都很普通的服务可被分解为单独部分，可轻易地进行调试和替换。</span><span class="sxs-lookup"><span data-stu-id="dcce0-137">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="dcce0-138">因为 MEF 模块在特定的应用程序集上没有硬依赖项，所以它允许扩展在不同应用程序之间重复使用。</span><span class="sxs-lookup"><span data-stu-id="dcce0-138">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="dcce0-139">这使得开发用于测试扩展组件的测试工具（独立于应用程序）变得简单。</span><span class="sxs-lookup"><span data-stu-id="dcce0-139">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="dcce0-140">通过使用 MEF 编写的可扩展应用程序声明了一个可由扩展组件填写的输入，它还可能为了向扩展揭示应用程序服务而声明导出。</span><span class="sxs-lookup"><span data-stu-id="dcce0-140">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="dcce0-141">每个扩展组件都声明一个导出，还有可能声明导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-141">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="dcce0-142">通过此方法，扩展组件自身为自动可扩展。</span><span class="sxs-lookup"><span data-stu-id="dcce0-142">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="dcce0-143">MEF 适用场景</span><span class="sxs-lookup"><span data-stu-id="dcce0-143">Where MEF is available</span></span>

<span data-ttu-id="dcce0-144">MEF 是 .NET Framework 4 的组成部分，适用于所有使用 .NET Framework 的地方。</span><span class="sxs-lookup"><span data-stu-id="dcce0-144">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="dcce0-145">可以在客户端应用程序（不论其是否使用 Windows 窗体或其他技术）或使用 ASP.NET 的服务端应用程序里使用 MEF。</span><span class="sxs-lookup"><span data-stu-id="dcce0-145">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="dcce0-146">MEF 和 MAF</span><span class="sxs-lookup"><span data-stu-id="dcce0-146">MEF and MAF</span></span>

<span data-ttu-id="dcce0-147">.NET Framework 的早期版本引入了 Managed Add-in Framework (MAF)，旨在让应用程序隔离和托管扩展。</span><span class="sxs-lookup"><span data-stu-id="dcce0-147">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="dcce0-148">MAF 与 MEF 相比，MAF 的重点级别较高，它关注扩展隔离和程序集加载及卸载，而 MEF 则关注可发现性、可扩展性和可移植性。</span><span class="sxs-lookup"><span data-stu-id="dcce0-148">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="dcce0-149">这两个框架可以平稳地相互操作，且一个单独的应用程序可以利用这两者。</span><span class="sxs-lookup"><span data-stu-id="dcce0-149">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="dcce0-150">简单计算器：一个示例应用程序</span><span class="sxs-lookup"><span data-stu-id="dcce0-150">SimpleCalculator: An example application</span></span>

<span data-ttu-id="dcce0-151">查看 MEF 能做什么最简单的方法就是构建一个简单的 MEF 应用程序。</span><span class="sxs-lookup"><span data-stu-id="dcce0-151">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="dcce0-152">在此示例中，你构建了一个叫作简单计算器的非常简单的计算器。</span><span class="sxs-lookup"><span data-stu-id="dcce0-152">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="dcce0-153">简单计算器旨在创建一个接受形式为“5+3”或“6-2”的基础运算命令然后返回正确答案的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="dcce0-153">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="dcce0-154">使用 MEF，能够添加新的操作人员而无须更改应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="dcce0-154">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="dcce0-155">要下载此示例的完整代码，请参阅 [SimpleCalculator 示例 (Visual Basic)](/samples/dotnet/samples/simple-calculator-vb/)。</span><span class="sxs-lookup"><span data-stu-id="dcce0-155">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="dcce0-156">简单计算器旨在演示 MEF 的概念和语法而非必须为其使用提供现实情况。</span><span class="sxs-lookup"><span data-stu-id="dcce0-156">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="dcce0-157">许多将从 MEF 的功能受益最大的应用程序比简单计算器更加复杂。</span><span class="sxs-lookup"><span data-stu-id="dcce0-157">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="dcce0-158">有关更多扩展性示例，请参阅 GitHub 上的 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef)。</span><span class="sxs-lookup"><span data-stu-id="dcce0-158">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="dcce0-159">首先，在 Visual Studio 中，创建一个新的控制台应用程序项目，并将其命名为 `SimpleCalculator`。</span><span class="sxs-lookup"><span data-stu-id="dcce0-159">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="dcce0-160">添加对 MEF 所驻留的 `System.ComponentModel.Composition` 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="dcce0-160">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="dcce0-161">打开 Module1.vb 或 Program.cs，再为 `System.ComponentModel.Composition` 和 `System.ComponentModel.Composition.Hosting` 添加 `Imports` 或 `using` 语句 。</span><span class="sxs-lookup"><span data-stu-id="dcce0-161">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="dcce0-162">这两个名称空间包含你开发可扩展应用程序将需要的 MEF 类型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-162">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="dcce0-163">如果使用的是 Visual Basic，则将 `Public` 关键字添加到声明 `Module1` 模块的行中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-163">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="dcce0-164">撰写容器和目录</span><span class="sxs-lookup"><span data-stu-id="dcce0-164">Composition container and catalogs</span></span>

<span data-ttu-id="dcce0-165">MEF 组合模型的核心是包含所有可用部件并执行组合的组合容器。</span><span class="sxs-lookup"><span data-stu-id="dcce0-165">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="dcce0-166">组合是对导入到导出进行的匹配。</span><span class="sxs-lookup"><span data-stu-id="dcce0-166">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="dcce0-167">撰写容器最常用的类型是 <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>，它将用于简单计算器。</span><span class="sxs-lookup"><span data-stu-id="dcce0-167">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="dcce0-168">如果使用的是 Visual Basic，则在 Module1.vb 中添加一个名为 `Program` 的公共类。</span><span class="sxs-lookup"><span data-stu-id="dcce0-168">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="dcce0-169">将以下行添加到 Module1.vb 或 Program.cs 中的 `Program` 类 ：</span><span class="sxs-lookup"><span data-stu-id="dcce0-169">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="dcce0-170">为了发现对其可用的部件，组合容器使用目录。</span><span class="sxs-lookup"><span data-stu-id="dcce0-170">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="dcce0-171">目录是让你从某些来源中发现可用部件的对象。</span><span class="sxs-lookup"><span data-stu-id="dcce0-171">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="dcce0-172">MEF 提供目录来发现来自提供的类型、程序集或目录的部件。</span><span class="sxs-lookup"><span data-stu-id="dcce0-172">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="dcce0-173">应用程序开发人员可以轻松地创建新的目录来发现来自其他来源（例如 Web 服务）的部件。</span><span class="sxs-lookup"><span data-stu-id="dcce0-173">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="dcce0-174">将下面的构造函数添加到 `Program` 类中:</span><span class="sxs-lookup"><span data-stu-id="dcce0-174">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="dcce0-175">对 <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> 的调用通知撰写容器撰写一组特定组件，在此情况下即为 `Program` 的当前实例。</span><span class="sxs-lookup"><span data-stu-id="dcce0-175">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="dcce0-176">但此时不会发生任何情况，因为 `Program` 没有需要填充的导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-176">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="dcce0-177">具有属性的导入和导出</span><span class="sxs-lookup"><span data-stu-id="dcce0-177">Imports and Exports with attributes</span></span>

<span data-ttu-id="dcce0-178">首先，你已向 `Program` 导入一个计算器。</span><span class="sxs-lookup"><span data-stu-id="dcce0-178">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="dcce0-179">这使得用户界面顾虑（例如将转到 `Program` 的控制台输入和导出）从计算机逻辑中隔离出来。</span><span class="sxs-lookup"><span data-stu-id="dcce0-179">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="dcce0-180">将下面的代码添加到 `Program` 类中:</span><span class="sxs-lookup"><span data-stu-id="dcce0-180">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="dcce0-181">请注意，`calculator` 对象的声明并非异常，但它使用了 <xref:System.ComponentModel.Composition.ImportAttribute> 属性进行修饰。</span><span class="sxs-lookup"><span data-stu-id="dcce0-181">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="dcce0-182">属性声明了某些操作为导入；在撰写对象时，它将由组合引擎进行填写。</span><span class="sxs-lookup"><span data-stu-id="dcce0-182">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="dcce0-183">每个导入都有一个决定其与什么导出相匹配的协定。</span><span class="sxs-lookup"><span data-stu-id="dcce0-183">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="dcce0-184">协定可以是显示指定的字符串，还可由 MEF 在给定类型中自动产生，在此情况下即为界面 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="dcce0-184">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="dcce0-185">任一使用匹配协定进行声明的导出将完成此导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-185">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="dcce0-186">请注意，尽管 `calculator` 对象的类型实际上为 `ICalculator`，但对此并无要求。</span><span class="sxs-lookup"><span data-stu-id="dcce0-186">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="dcce0-187">协定独立于导入对象的类型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-187">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="dcce0-188">（在此情况下，可以略去 `typeof(ICalculator)`。</span><span class="sxs-lookup"><span data-stu-id="dcce0-188">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="dcce0-189">除非你明确指定，否则 MEF 会自动假定协定基于导入的类型。）</span><span class="sxs-lookup"><span data-stu-id="dcce0-189">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="dcce0-190">将此非常简单的界面添加到模块或 `SimpleCalculator` 名称空间中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-190">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="dcce0-191">既然你已经定义了 `ICalculator`，则需要一个执行它的类。</span><span class="sxs-lookup"><span data-stu-id="dcce0-191">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="dcce0-192">将下面的类添加到模块或 `SimpleCalculator` 命名空间中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-192">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

<span data-ttu-id="dcce0-193">下面是将与 `Program` 中的导入相匹配的导出。</span><span class="sxs-lookup"><span data-stu-id="dcce0-193">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="dcce0-194">为了使导出与导入相匹配，导出必须使用相同的协定。</span><span class="sxs-lookup"><span data-stu-id="dcce0-194">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="dcce0-195">在基于 `typeof(MySimpleCalculator)` 的协定下导出将生成不匹配，也不会填写导入，因此协定需要完全匹配。</span><span class="sxs-lookup"><span data-stu-id="dcce0-195">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="dcce0-196">鉴于此程序集中的所有可用部件将填充撰写容器，`MySimpleCalculator` 部件将可使用。</span><span class="sxs-lookup"><span data-stu-id="dcce0-196">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="dcce0-197">当用于 `Program` 的构造函数在 `Program` 上执行组合时，`MySimpleCalculator` 对象（将处于此目的进行创建）将填写其导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-197">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="dcce0-198">用户界面层（`Program`）无需了解其他内容。</span><span class="sxs-lookup"><span data-stu-id="dcce0-198">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="dcce0-199">因此，可以填写 `Main` 方法中的用户界面逻辑的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="dcce0-199">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="dcce0-200">将以下代码添加到 `Main` 方法中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-200">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="dcce0-201">该代码仅读出一行导入并在结尾调用 `Calculate` 的 `ICalculator` 函数（由代码写回控制台）。</span><span class="sxs-lookup"><span data-stu-id="dcce0-201">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="dcce0-202">这是你在 `Program` 中所需的全部代码。</span><span class="sxs-lookup"><span data-stu-id="dcce0-202">That is all the code you need in `Program`.</span></span> <span data-ttu-id="dcce0-203">剩余工作将在部件中进行。</span><span class="sxs-lookup"><span data-stu-id="dcce0-203">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="dcce0-204">进一步的导入和 ImportMany</span><span class="sxs-lookup"><span data-stu-id="dcce0-204">Further Imports and ImportMany</span></span>

<span data-ttu-id="dcce0-205">为了使简单计算器获得可扩性，它需要导入一组操作。</span><span class="sxs-lookup"><span data-stu-id="dcce0-205">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="dcce0-206">一般 <xref:System.ComponentModel.Composition.ImportAttribute> 属性由且只能由 <xref:System.ComponentModel.Composition.ExportAttribute> 填写。</span><span class="sxs-lookup"><span data-stu-id="dcce0-206">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="dcce0-207">如果可用数目超过一，则组合引擎生成错误。</span><span class="sxs-lookup"><span data-stu-id="dcce0-207">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="dcce0-208">可以使用 <xref:System.ComponentModel.Composition.ImportManyAttribute> 属性来创建可由任意数目的导出填写的导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-208">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="dcce0-209">将下列操作属性添加到 `MySimpleCalculator` 类：</span><span class="sxs-lookup"><span data-stu-id="dcce0-209">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="dcce0-210"><xref:System.Lazy%602> 是由 MEF 提供来保存对导出的间接引用的类型。</span><span class="sxs-lookup"><span data-stu-id="dcce0-210"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="dcce0-211">除了导出对象本身，还可以获取导出元数据，或描述导出对象的信息。</span><span class="sxs-lookup"><span data-stu-id="dcce0-211">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="dcce0-212">每个 <xref:System.Lazy%602> 都包含一个代表实际操作的 `IOperation` 对象和一个代表元数据的 `IOperationData` 对象。</span><span class="sxs-lookup"><span data-stu-id="dcce0-212">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="dcce0-213">将下列简单界面添加到模块或 `SimpleCalculator` 名称空间中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-213">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="dcce0-214">在此情况下，每项操作的元数据是表示该操作的符号，例如 +、-、\*。</span><span class="sxs-lookup"><span data-stu-id="dcce0-214">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="dcce0-215">为了运行加法操作，将下面的类添加到模块或 `SimpleCalculator` 名称空间中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-215">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

<span data-ttu-id="dcce0-216"><xref:System.ComponentModel.Composition.ExportAttribute> 属性函数和之前一致。</span><span class="sxs-lookup"><span data-stu-id="dcce0-216">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="dcce0-217"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> 属性将采用名称值对形式的元数据附加到导出。</span><span class="sxs-lookup"><span data-stu-id="dcce0-217">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="dcce0-218">尽管 `Add` 类执行 `IOperation`，但执行 `IOperationData` 的类并无明确定义。</span><span class="sxs-lookup"><span data-stu-id="dcce0-218">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="dcce0-219">相反，由 MEF 隐式创建的类具有基于提供的元数据名称的属性。</span><span class="sxs-lookup"><span data-stu-id="dcce0-219">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="dcce0-220">（这是用于访问 MEF 中的元数据的方法之一。）</span><span class="sxs-lookup"><span data-stu-id="dcce0-220">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="dcce0-221">MEF 中的组合是递归的。</span><span class="sxs-lookup"><span data-stu-id="dcce0-221">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="dcce0-222">你明确撰写了 `Program` 对象（导入了结果为 `ICalculator` 类型的 `MySimpleCalculator`）。</span><span class="sxs-lookup"><span data-stu-id="dcce0-222">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="dcce0-223">反过来，`MySimpleCalculator` 导入一组 `IOperation` 对象，且该导入将在创建 `MySimpleCalculator` 时进行填写，同时进行 `Program` 的导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-223">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="dcce0-224">如果 `Add` 类声明了一项进一步的导入，则该导入也须进行填写，等等。</span><span class="sxs-lookup"><span data-stu-id="dcce0-224">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="dcce0-225">任何将空缺结果留在撰写错误中的导入。</span><span class="sxs-lookup"><span data-stu-id="dcce0-225">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="dcce0-226">（然而，有可能声明导入为可选的或为其分配默认值。）</span><span class="sxs-lookup"><span data-stu-id="dcce0-226">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="dcce0-227">计算器逻辑</span><span class="sxs-lookup"><span data-stu-id="dcce0-227">Calculator Logic</span></span>

<span data-ttu-id="dcce0-228">准备好这些部件，剩下的就是计算器逻辑本身了。</span><span class="sxs-lookup"><span data-stu-id="dcce0-228">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="dcce0-229">将下面的代码添加到 `MySimpleCalculator` 类来执行 `Calculate` 方法中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-229">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

<span data-ttu-id="dcce0-230">初始步骤将输入字符串解析到左右操作数和一个运算符字符。</span><span class="sxs-lookup"><span data-stu-id="dcce0-230">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="dcce0-231">在 `foreach` 循环中，`operations` 集合的每个成员都要检查。</span><span class="sxs-lookup"><span data-stu-id="dcce0-231">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="dcce0-232">这些对象是 <xref:System.Lazy%602> 类型，其元数据值和导出对象可分别使用 <xref:System.Lazy%602.Metadata%2A> 属性和<xref:System.Lazy%601.Value%2A> 属性进行访问。</span><span class="sxs-lookup"><span data-stu-id="dcce0-232">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="dcce0-233">在此情况下，如果发现 `Symbol` 对象的 `IOperationData` 属性为匹配项，则计算器调用 `Operate` 对象的 `IOperation` 方法并返回结果。</span><span class="sxs-lookup"><span data-stu-id="dcce0-233">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="dcce0-234">还需要返回字符串中的首个非数字字符位置的 helper 方法来完成计算器。</span><span class="sxs-lookup"><span data-stu-id="dcce0-234">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="dcce0-235">将下面的 helper 方法添加到 `MySimpleCalculator` 类中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-235">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="dcce0-236">现在，应该可以编译和运行项目了。</span><span class="sxs-lookup"><span data-stu-id="dcce0-236">You should now be able to compile and run the project.</span></span> <span data-ttu-id="dcce0-237">确保在 Visual Basic 里将 `Public` 关键字添加到 `Module1` 中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-237">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="dcce0-238">在控制台窗口中键入“5+3”等加法运算计算器会返回结果。</span><span class="sxs-lookup"><span data-stu-id="dcce0-238">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="dcce0-239">任何其他运算符会导致“找不到运算!”</span><span class="sxs-lookup"><span data-stu-id="dcce0-239">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="dcce0-240">消息。</span><span class="sxs-lookup"><span data-stu-id="dcce0-240">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="dcce0-241">采用新类扩展 SimpleCalculator</span><span class="sxs-lookup"><span data-stu-id="dcce0-241">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="dcce0-242">既然计算器能够运行，则可以简单地添加新操作。</span><span class="sxs-lookup"><span data-stu-id="dcce0-242">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="dcce0-243">将下面的类添加到模块或 `SimpleCalculator` 命名空间中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-243">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

<span data-ttu-id="dcce0-244">编译并运行该项目。</span><span class="sxs-lookup"><span data-stu-id="dcce0-244">Compile and run the project.</span></span> <span data-ttu-id="dcce0-245">键入“5-3”等减法运算。</span><span class="sxs-lookup"><span data-stu-id="dcce0-245">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="dcce0-246">现在，计算器既支持减法运算也支持加法运算。</span><span class="sxs-lookup"><span data-stu-id="dcce0-246">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="dcce0-247">采用新程序集扩展 SimpleCalculator</span><span class="sxs-lookup"><span data-stu-id="dcce0-247">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="dcce0-248">将类添加到源代码非常简单，但 MEF 提供了观察应用程序部件源之外的内容的功能。</span><span class="sxs-lookup"><span data-stu-id="dcce0-248">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="dcce0-249">为了演示它，将需要通过添加 <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> 来修改简单计算器从而为部件搜索目录以及其自身的程序集。</span><span class="sxs-lookup"><span data-stu-id="dcce0-249">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="dcce0-250">将叫作 `Extensions` 的新目录添加到 SimpleCalculator 项目中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-250">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="dcce0-251">确保将其添加到项目级别（而非解决方法级别）中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-251">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="dcce0-252">然后将新类库项目添加到叫作 `ExtendedOperations` 的解决方法中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-252">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="dcce0-253">新项目将编译为一个单独的程序集。</span><span class="sxs-lookup"><span data-stu-id="dcce0-253">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="dcce0-254">打开 ExtendedOperations 项目的项目属性设计器，然后单击“编译”或“生成”选项卡。更改“生成输出路径”或“输出路径”以指向扩展目录，它位于 SimpleCalculator 项目目录中 (..\SimpleCalculator\Extensions\\) 。</span><span class="sxs-lookup"><span data-stu-id="dcce0-254">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="dcce0-255">在 Module1.vb 或 Program.cs 中，将以下行添加到 `Program` 构造函数中 ：</span><span class="sxs-lookup"><span data-stu-id="dcce0-255">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="dcce0-256">将示例路径替换为指向扩展目录的路径。</span><span class="sxs-lookup"><span data-stu-id="dcce0-256">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="dcce0-257">（此绝对路径仅供调试目的使用。</span><span class="sxs-lookup"><span data-stu-id="dcce0-257">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="dcce0-258">在生产应用程序中，应该使用相对路径。）现在，<xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> 将把在扩展目录中的所有程序集中发现的部件添加到撰写容器中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-258">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="dcce0-259">在扩展操作项目中，将参考添加到简单计算器和 System.ComponentModel.Composition 中。</span><span class="sxs-lookup"><span data-stu-id="dcce0-259">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="dcce0-260">在扩展操作类文件中，添加一个 System.ComponentModel.Composition 的 `Imports` 或 `using` 语句。</span><span class="sxs-lookup"><span data-stu-id="dcce0-260">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="dcce0-261">在 Visual Basic 中，也添加一个简单计算器的 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="dcce0-261">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="dcce0-262">然后将下面的类添加到扩展操作类文件中：</span><span class="sxs-lookup"><span data-stu-id="dcce0-262">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

<span data-ttu-id="dcce0-263">请注意，为了使协定匹配，<xref:System.ComponentModel.Composition.ExportAttribute> 属性必须与 <xref:System.ComponentModel.Composition.ImportAttribute> 的类型相同。</span><span class="sxs-lookup"><span data-stu-id="dcce0-263">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="dcce0-264">编译并运行该项目。</span><span class="sxs-lookup"><span data-stu-id="dcce0-264">Compile and run the project.</span></span> <span data-ttu-id="dcce0-265">测试新的 Mod (%) 运算符。</span><span class="sxs-lookup"><span data-stu-id="dcce0-265">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="dcce0-266">结束语</span><span class="sxs-lookup"><span data-stu-id="dcce0-266">Conclusion</span></span>

<span data-ttu-id="dcce0-267">本主题包括 MEF 的基础概念。</span><span class="sxs-lookup"><span data-stu-id="dcce0-267">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="dcce0-268">部件，目录和撰写容器</span><span class="sxs-lookup"><span data-stu-id="dcce0-268">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="dcce0-269">部件和撰写容器是 MEF 应用程序的基础构造块。</span><span class="sxs-lookup"><span data-stu-id="dcce0-269">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="dcce0-270">部件是所有导入或导出值（最多包含自己）的对象。</span><span class="sxs-lookup"><span data-stu-id="dcce0-270">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="dcce0-271">目录提供了一组来自特定源的部件。</span><span class="sxs-lookup"><span data-stu-id="dcce0-271">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="dcce0-272">撰写容器使用目录提供的部件来执行将导入绑定到导出的组合。</span><span class="sxs-lookup"><span data-stu-id="dcce0-272">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="dcce0-273">导入和导出</span><span class="sxs-lookup"><span data-stu-id="dcce0-273">Imports and exports</span></span>

     <span data-ttu-id="dcce0-274">导入和导出是组件进行通信的方式。</span><span class="sxs-lookup"><span data-stu-id="dcce0-274">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="dcce0-275">组件使用导入指定对特定值或对象的需求，使用导出指定值的可用性。</span><span class="sxs-lookup"><span data-stu-id="dcce0-275">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="dcce0-276">每个导入都通过其协定匹配了一组导出。</span><span class="sxs-lookup"><span data-stu-id="dcce0-276">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dcce0-277">后续步骤</span><span class="sxs-lookup"><span data-stu-id="dcce0-277">Next steps</span></span>

<span data-ttu-id="dcce0-278">要下载此示例的完整代码，请参阅 [SimpleCalculator 示例 (Visual Basic)](/samples/dotnet/samples/simple-calculator-vb/)。</span><span class="sxs-lookup"><span data-stu-id="dcce0-278">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="dcce0-279">有关详细信息和代码示例，请参阅 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef)。</span><span class="sxs-lookup"><span data-stu-id="dcce0-279">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="dcce0-280">有关 MEF 类型的列表，请参阅 <xref:System.ComponentModel.Composition?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="dcce0-280">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
