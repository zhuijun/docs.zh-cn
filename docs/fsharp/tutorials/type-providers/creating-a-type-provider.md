---
title: 教程：创建类型提供程序
description: '了解如何在 F # 3.0 中创建自己的 F # 类型提供程序，具体方法是检查几个简单的类型提供程序来说明基本概念。'
ms.date: 11/04/2019
ms.openlocfilehash: 67ebd91007ff814370573ebc1a65b2c7a8399f7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202135"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="aed79-103">教程：创建类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="aed79-104">F # 中的类型提供程序机制是其对信息丰富编程支持的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="aed79-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="aed79-105">本教程介绍了如何创建自己的类型提供程序，逐步讲解如何开发几个简单的类型提供程序来说明基本概念。</span><span class="sxs-lookup"><span data-stu-id="aed79-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="aed79-106">有关 F # 中的类型提供程序机制的详细信息，请参阅[类型提供程序](index.md)。</span><span class="sxs-lookup"><span data-stu-id="aed79-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="aed79-107">F # 生态系统包含一系列常用的 Internet 和企业数据服务的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="aed79-108">例如：</span><span class="sxs-lookup"><span data-stu-id="aed79-108">For example:</span></span>

- <span data-ttu-id="aed79-109">[Fsharp.core](https://fsharp.github.io/FSharp.Data/)包含 JSON、XML、CSV 和 HTML 文档格式的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="aed79-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/)通过对象映射以及针对这些数据源的 F # LINQ 查询，提供对 SQL 数据库的强类型访问。</span><span class="sxs-lookup"><span data-stu-id="aed79-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="aed79-111">[Fsharp.core](https://fsprojects.github.io/FSharp.Data.SqlClient/)包含一组用于编译时的类型提供程序，用于在 F # 中嵌入 t-sql。</span><span class="sxs-lookup"><span data-stu-id="aed79-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="aed79-112">[Fsharp.core](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是一组较旧的类型提供程序，仅用于访问 SQL、实体框架、ODATA 和 WSDL 数据服务 .NET Framework 编程。</span><span class="sxs-lookup"><span data-stu-id="aed79-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="aed79-113">必要时，可以创建自定义类型提供程序，也可以引用其他人创建的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="aed79-114">例如，你的组织可能有一个数据服务，该服务提供了数量不断增长的命名数据集，每个数据集都有其自己的稳定数据架构。</span><span class="sxs-lookup"><span data-stu-id="aed79-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="aed79-115">您可以创建一个类型提供程序，用于读取架构并以强类型方式向程序员显示当前数据集。</span><span class="sxs-lookup"><span data-stu-id="aed79-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="aed79-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="aed79-116">Before You Start</span></span>

<span data-ttu-id="aed79-117">类型提供程序机制主要用于向 F # 编程体验中注入稳定的数据和服务信息空间。</span><span class="sxs-lookup"><span data-stu-id="aed79-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="aed79-118">此机制不能用于注入其架构在程序执行过程中发生更改的信息空间，这种方式与程序逻辑相关。</span><span class="sxs-lookup"><span data-stu-id="aed79-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="aed79-119">此外，该机制不是针对语言内的元编程而设计的，即使该域包含一些有效的用途。</span><span class="sxs-lookup"><span data-stu-id="aed79-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="aed79-120">只有在必要时才应使用此机制，而在何处开发类型提供程序会产生非常高的值。</span><span class="sxs-lookup"><span data-stu-id="aed79-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="aed79-121">你应避免在架构不可用的情况下编写类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="aed79-122">同样，您应该避免编写一个类型提供程序，在这种情况下，一般（甚至是现有的） .NET 库即可满足需要。</span><span class="sxs-lookup"><span data-stu-id="aed79-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="aed79-123">在开始之前，您可能会提出以下问题：</span><span class="sxs-lookup"><span data-stu-id="aed79-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="aed79-124">你的信息源是否有架构？</span><span class="sxs-lookup"><span data-stu-id="aed79-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="aed79-125">如果是这样，什么是 F # 和 .NET 类型系统的映射？</span><span class="sxs-lookup"><span data-stu-id="aed79-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="aed79-126">能否使用现有的（动态类型的） API 作为实现的起始点？</span><span class="sxs-lookup"><span data-stu-id="aed79-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="aed79-127">你和你的组织是否有足够的类型提供商的使用来使写入它有价值？</span><span class="sxs-lookup"><span data-stu-id="aed79-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="aed79-128">正常的 .NET 库是否能满足您的需要？</span><span class="sxs-lookup"><span data-stu-id="aed79-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="aed79-129">你的架构将更改多少？</span><span class="sxs-lookup"><span data-stu-id="aed79-129">How much will your schema change?</span></span>

- <span data-ttu-id="aed79-130">它是否会在编码过程中更改？</span><span class="sxs-lookup"><span data-stu-id="aed79-130">Will it change during coding?</span></span>

- <span data-ttu-id="aed79-131">它是否会在编码会话之间更改？</span><span class="sxs-lookup"><span data-stu-id="aed79-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="aed79-132">它是否会在程序执行过程中更改？</span><span class="sxs-lookup"><span data-stu-id="aed79-132">Will it change during program execution?</span></span>

<span data-ttu-id="aed79-133">类型提供程序最适用于架构在运行时和编译代码的生存期内稳定的情况。</span><span class="sxs-lookup"><span data-stu-id="aed79-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="aed79-134">简单类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-134">A Simple Type Provider</span></span>

<span data-ttu-id="aed79-135">此示例为 HelloWorldTypeProvider，类似于 `examples` [F # 类型提供程序 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)的目录中的示例。</span><span class="sxs-lookup"><span data-stu-id="aed79-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="aed79-136">提供程序提供了一个包含100个已擦除类型的 "类型空间"，如以下代码通过使用 F # 签名语法和省略除之外的详细信息中所示 `Type1` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="aed79-137">有关已擦除的类型的详细信息，请参阅本主题后面的有关已擦除的所[提供类型的详细](#details-about-erased-provided-types)信息。</span><span class="sxs-lookup"><span data-stu-id="aed79-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="aed79-138">请注意，提供的类型和成员集是静态已知的。</span><span class="sxs-lookup"><span data-stu-id="aed79-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="aed79-139">此示例不利用提供程序提供依赖于架构的类型的能力。</span><span class="sxs-lookup"><span data-stu-id="aed79-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="aed79-140">下面的代码概述了类型提供程序的实现，详细信息将在本主题的后面部分中介绍。</span><span class="sxs-lookup"><span data-stu-id="aed79-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="aed79-141">此代码与联机示例之间可能存在差异。</span><span class="sxs-lookup"><span data-stu-id="aed79-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

<span data-ttu-id="aed79-142">若要使用此提供程序，请打开一个单独的 Visual Studio 实例，创建一个 F # 脚本，然后使用 #r 从脚本添加对提供程序的引用，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="aed79-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="aed79-143">然后，在该 `Samples.HelloWorldTypeProvider` 类型提供程序生成的命名空间下查找类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="aed79-144">重新编译提供程序之前，请确保已关闭使用提供程序 DLL 的所有 Visual Studio 和 F# 交互窗口的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="aed79-145">否则，将发生生成错误，因为输出 DLL 将被锁定。</span><span class="sxs-lookup"><span data-stu-id="aed79-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="aed79-146">若要使用 print 语句调试此访问接口，请生成一个脚本，用于公开提供程序的问题，然后使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="aed79-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="aed79-147">若要使用 Visual Studio 调试此提供程序，请使用管理凭据打开适用于 Visual Studio 的开发人员命令提示，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="aed79-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="aed79-148">作为替代方法，请打开 Visual Studio，打开 "调试" 菜单，选择 `Debug/Attach to process…` 并附加到 `devenv` 正在编辑脚本的其他进程。</span><span class="sxs-lookup"><span data-stu-id="aed79-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="aed79-149">通过使用此方法，您可以通过以交互方式将表达式键入到第二个实例（使用完整的 IntelliSense 和其他功能），更轻松地定位类型提供程序中的特定逻辑。</span><span class="sxs-lookup"><span data-stu-id="aed79-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="aed79-150">可以禁用仅我的代码调试，以便更好地识别生成的代码中的错误。</span><span class="sxs-lookup"><span data-stu-id="aed79-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="aed79-151">有关如何启用或禁用此功能的信息，请参阅[使用调试器在代码中导航](/visualstudio/debugger/navigating-through-code-with-the-debugger)。</span><span class="sxs-lookup"><span data-stu-id="aed79-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="aed79-152">此外，还可以通过打开 `Debug` 菜单，然后选择 `Exceptions` "Ctrl + Alt + E 键" 打开对话框，来设置第一次异常捕获 `Exceptions` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="aed79-153">在该对话框的 "" 下 `Common Language Runtime Exceptions` ，选中相应的 `Thrown` 复选框。</span><span class="sxs-lookup"><span data-stu-id="aed79-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="aed79-154">类型提供程序的实现</span><span class="sxs-lookup"><span data-stu-id="aed79-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="aed79-155">本部分将指导你完成类型提供程序实现的主要部分。</span><span class="sxs-lookup"><span data-stu-id="aed79-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="aed79-156">首先，为自定义类型提供程序本身定义类型：</span><span class="sxs-lookup"><span data-stu-id="aed79-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="aed79-157">此类型必须是公共的，并且必须使用[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)属性进行标记，以便编译器在单独的 F # 项目引用包含该类型的程序集时识别该类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="aed79-158">*Config*参数是可选的，如果存在，则包含 F # 编译器创建的类型提供程序实例的上下文配置信息。</span><span class="sxs-lookup"><span data-stu-id="aed79-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="aed79-159">接下来，实现[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)接口。</span><span class="sxs-lookup"><span data-stu-id="aed79-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="aed79-160">在这种情况下，将 `TypeProviderForNamespaces` API 中的类型用作 `ProvidedTypes` 基类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="aed79-161">此帮助器类型可以提供积极提供的命名空间的有限集合，其中每个命名空间都直接包含有限数量的固定、积极提供的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="aed79-162">在此上下文中，提供程序*积极*将生成类型，即使它们不需要或不使用也是如此。</span><span class="sxs-lookup"><span data-stu-id="aed79-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="aed79-163">接下来，定义为提供的类型指定命名空间的本地私有值，并查找类型提供程序程序集本身。</span><span class="sxs-lookup"><span data-stu-id="aed79-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="aed79-164">此程序集稍后用作所提供的已擦除类型的逻辑父类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="aed79-165">接下来，创建一个函数以提供每个类型 Type1 .。。Type100.</span><span class="sxs-lookup"><span data-stu-id="aed79-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="aed79-166">本主题稍后将对此函数进行更详细的介绍。</span><span class="sxs-lookup"><span data-stu-id="aed79-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="aed79-167">接下来，生成100提供的类型：</span><span class="sxs-lookup"><span data-stu-id="aed79-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="aed79-168">接下来，将类型添加为提供的命名空间：</span><span class="sxs-lookup"><span data-stu-id="aed79-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="aed79-169">最后，添加一个程序集特性，该特性指示你正在创建类型提供程序 DLL：</span><span class="sxs-lookup"><span data-stu-id="aed79-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="aed79-170">提供一种类型及其成员</span><span class="sxs-lookup"><span data-stu-id="aed79-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="aed79-171">`makeOneProvidedType`函数执行提供一种类型的实际工作。</span><span class="sxs-lookup"><span data-stu-id="aed79-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="aed79-172">此步骤说明了此函数的实现。</span><span class="sxs-lookup"><span data-stu-id="aed79-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="aed79-173">首先，创建提供的类型（例如，Type1，当 n = 1 或 Type57 时，n = 57）。</span><span class="sxs-lookup"><span data-stu-id="aed79-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="aed79-174">您应注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="aed79-174">You should note the following points:</span></span>

- <span data-ttu-id="aed79-175">此提供的类型会被清除。</span><span class="sxs-lookup"><span data-stu-id="aed79-175">This provided type is erased.</span></span>  <span data-ttu-id="aed79-176">由于您指示基类型为，因此 `obj` ，实例将在编译的代码中显示为类型为[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)的值。</span><span class="sxs-lookup"><span data-stu-id="aed79-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="aed79-177">指定非嵌套类型时，必须指定程序集和命名空间。</span><span class="sxs-lookup"><span data-stu-id="aed79-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="aed79-178">对于已擦除的类型，程序集应为类型提供程序程序集本身。</span><span class="sxs-lookup"><span data-stu-id="aed79-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="aed79-179">接下来，将 XML 文档添加到该类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="aed79-180">此文档被延迟，即，如果主机编译器需要，则按需计算。</span><span class="sxs-lookup"><span data-stu-id="aed79-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="aed79-181">接下来，将提供的静态属性添加到类型中：</span><span class="sxs-lookup"><span data-stu-id="aed79-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="aed79-182">获取此属性的计算结果将始终为字符串 "Hello！"。</span><span class="sxs-lookup"><span data-stu-id="aed79-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="aed79-183">属性的可 `GetterCode` 使用 F # 引号，表示宿主编译器为获取属性而生成的代码。</span><span class="sxs-lookup"><span data-stu-id="aed79-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="aed79-184">有关报价的详细信息，请参阅[代码引用（F #）](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。</span><span class="sxs-lookup"><span data-stu-id="aed79-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="aed79-185">将 XML 文档添加到属性。</span><span class="sxs-lookup"><span data-stu-id="aed79-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="aed79-186">现在，将提供的属性附加到提供的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="aed79-187">您必须将提供的成员附加到一个且仅有一个类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="aed79-188">否则，该成员将永远无法访问。</span><span class="sxs-lookup"><span data-stu-id="aed79-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="aed79-189">现在，创建一个不采用任何参数的提供的构造函数。</span><span class="sxs-lookup"><span data-stu-id="aed79-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="aed79-190">`InvokeCode`构造函数的返回一个 F # 引号，该引号表示在调用构造函数时宿主编译器生成的代码。</span><span class="sxs-lookup"><span data-stu-id="aed79-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="aed79-191">例如，可以使用以下构造函数：</span><span class="sxs-lookup"><span data-stu-id="aed79-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="aed79-192">将使用基础数据 "对象数据" 创建所提供类型的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="aed79-193">带引号的代码包含到[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)的转换，因为该类型是所提供的类型的擦除（在声明所提供的类型时指定的类型）。</span><span class="sxs-lookup"><span data-stu-id="aed79-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="aed79-194">向构造函数添加 XML 文档，并将提供的构造函数添加到提供的类型中：</span><span class="sxs-lookup"><span data-stu-id="aed79-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="aed79-195">创建另一个采用一个参数的提供的构造函数：</span><span class="sxs-lookup"><span data-stu-id="aed79-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="aed79-196">`InvokeCode`构造函数的再次返回 F # 引号，表示宿主编译器为对方法的调用而生成的代码。</span><span class="sxs-lookup"><span data-stu-id="aed79-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="aed79-197">例如，可以使用以下构造函数：</span><span class="sxs-lookup"><span data-stu-id="aed79-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="aed79-198">使用基础数据 "10" 创建所提供类型的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="aed79-199">您可能已注意到该 `InvokeCode` 函数返回了一个引号。</span><span class="sxs-lookup"><span data-stu-id="aed79-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="aed79-200">此函数的输入为表达式列表，每个构造函数参数一个。</span><span class="sxs-lookup"><span data-stu-id="aed79-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="aed79-201">在这种情况下，可在中找到表示单个参数值的表达式 `args.[0]` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="aed79-202">对构造函数的调用的代码会将返回值强制转换为已清除的类型 `obj` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="aed79-203">将第二个提供的构造函数添加到类型后，将创建一个提供的实例属性：</span><span class="sxs-lookup"><span data-stu-id="aed79-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="aed79-204">获取此属性将返回字符串的长度，即表示形式对象。</span><span class="sxs-lookup"><span data-stu-id="aed79-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="aed79-205">`GetterCode`属性返回一个 F # 引号，该引号指定宿主编译器生成以获取属性的代码。</span><span class="sxs-lookup"><span data-stu-id="aed79-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="aed79-206">与一样 `InvokeCode` ，该 `GetterCode` 函数返回一个引号。</span><span class="sxs-lookup"><span data-stu-id="aed79-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="aed79-207">宿主编译器使用参数列表调用此函数。</span><span class="sxs-lookup"><span data-stu-id="aed79-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="aed79-208">在这种情况下，参数只包含表示正在调用 getter 的实例的单个表达式，你可以使用访问该实例 `args.[0]` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="aed79-209">`GetterCode`然后，将接合的实现转换为已删除类型的结果引用 `obj` ，并使用强制转换来满足编译器用于检查对象是否为字符串的类型的机制。</span><span class="sxs-lookup"><span data-stu-id="aed79-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="aed79-210">下一部分提供了 `makeOneProvidedType` 包含一个参数的实例方法。</span><span class="sxs-lookup"><span data-stu-id="aed79-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="aed79-211">最后，创建包含100嵌套属性的嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="aed79-212">此嵌套类型和其属性的创建延迟，即按需计算。</span><span class="sxs-lookup"><span data-stu-id="aed79-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="aed79-213">已清除的提供的类型的详细信息</span><span class="sxs-lookup"><span data-stu-id="aed79-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="aed79-214">本部分中的示例仅提供已*清除的提供的类型*，这些类型在下列情况下特别有用：</span><span class="sxs-lookup"><span data-stu-id="aed79-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="aed79-215">当你为仅包含数据和方法的信息空间编写提供程序时。</span><span class="sxs-lookup"><span data-stu-id="aed79-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="aed79-216">编写准确的运行时类型语义对于实际使用信息空间不重要的访问接口。</span><span class="sxs-lookup"><span data-stu-id="aed79-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="aed79-217">当你为信息空间编写提供程序时，这些信息空间非常大且相互互连，因此无法为信息空间生成真实的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="aed79-218">在此示例中，每个提供的类型都将被清除为类型 `obj` ，并且该类型的所有使用将 `obj` 在编译的代码中显示为类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="aed79-219">事实上，这些示例中的基础对象是字符串，但该类型在 `System.Object` .net 编译的代码中显示为。</span><span class="sxs-lookup"><span data-stu-id="aed79-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="aed79-220">与类型擦除的所有使用一样，可以使用显式装箱、取消装箱和强制转换为破坏的已擦除类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="aed79-221">在这种情况下，当使用对象时，可能会导致无效的强制转换异常。</span><span class="sxs-lookup"><span data-stu-id="aed79-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="aed79-222">提供程序运行时可以定义自己的专用表示类型，以帮助防止出现 false 表示形式。</span><span class="sxs-lookup"><span data-stu-id="aed79-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="aed79-223">不能在 F # 本身中定义已删除的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="aed79-224">仅可删除所提供的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-224">Only provided types may be erased.</span></span> <span data-ttu-id="aed79-225">您必须了解使用类型提供程序的已擦除类型或提供擦除的类型的提供程序的各种后果，这两者都是不切实际的。</span><span class="sxs-lookup"><span data-stu-id="aed79-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="aed79-226">擦除的类型没有真正的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="aed79-227">因此，不能对该类型执行准确的反射，如果使用运行时强制转换和依赖于确切运行时类型语义的其他技术，则可能破坏已擦除的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="aed79-228">在运行时，通常会导致类型强制转换异常。</span><span class="sxs-lookup"><span data-stu-id="aed79-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="aed79-229">为已清除的提供的类型选择表示形式</span><span class="sxs-lookup"><span data-stu-id="aed79-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="aed79-230">对于某些使用已擦除的提供类型，不需要表示形式。</span><span class="sxs-lookup"><span data-stu-id="aed79-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="aed79-231">例如，已清除的提供的类型可能只包含静态属性和成员，不包含任何构造函数，并且没有方法或属性返回类型的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="aed79-232">如果可以访问已清除的提供的类型的实例，则必须考虑以下问题：</span><span class="sxs-lookup"><span data-stu-id="aed79-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="aed79-233">**提供的类型的擦除内容是什么？**</span><span class="sxs-lookup"><span data-stu-id="aed79-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="aed79-234">所提供类型的擦除是类型在已编译的 .NET 代码中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="aed79-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="aed79-235">所提供的已擦除类类型的擦除始终是该类型的继承链中的第一个非擦除基类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="aed79-236">所提供的已擦除接口类型的擦除始终为 `System.Object` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="aed79-237">**提供的类型的表示形式有哪些？**</span><span class="sxs-lookup"><span data-stu-id="aed79-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="aed79-238">已清除的提供的类型的可能的对象集称为其表示形式。</span><span class="sxs-lookup"><span data-stu-id="aed79-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="aed79-239">在本文档的示例中，所有已清除的提供的类型的表示形式 `Type1..Type100` 始终为字符串对象。</span><span class="sxs-lookup"><span data-stu-id="aed79-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="aed79-240">提供的类型的所有表示形式都必须与提供的类型的擦除兼容。</span><span class="sxs-lookup"><span data-stu-id="aed79-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="aed79-241">（否则，F # 编译器将在使用类型提供程序时提供错误，否则将生成无效的 .NET 代码。</span><span class="sxs-lookup"><span data-stu-id="aed79-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="aed79-242">如果类型提供程序返回的代码给出无效的表示形式，则该类型提供程序无效。）</span><span class="sxs-lookup"><span data-stu-id="aed79-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="aed79-243">您可以使用下列方法之一为所提供的对象选择表示形式，这两种方法都非常常见：</span><span class="sxs-lookup"><span data-stu-id="aed79-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="aed79-244">如果你只是在现有 .NET 类型上提供强类型包装，则你的类型可能会擦除到该类型，将该类型的实例用作表示形式，或同时使用这两种类型的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="aed79-245">使用强类型版本时，此方法适用于该类型的大多数现有方法。</span><span class="sxs-lookup"><span data-stu-id="aed79-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="aed79-246">如果要创建与任何现有 .NET API 明显不同的 API，请创建运行时类型，这些运行时类型将为所提供的类型的擦除和表示形式。</span><span class="sxs-lookup"><span data-stu-id="aed79-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="aed79-247">本文档中的示例使用字符串作为提供的对象的表示形式。</span><span class="sxs-lookup"><span data-stu-id="aed79-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="aed79-248">通常，将其他对象用于表示形式可能会非常合适。</span><span class="sxs-lookup"><span data-stu-id="aed79-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="aed79-249">例如，可以使用字典作为属性包：</span><span class="sxs-lookup"><span data-stu-id="aed79-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="aed79-250">作为替代方法，你可以在类型提供程序中定义一个类型，该类型将在运行时用于形成表示形式，以及一个或多个运行时操作：</span><span class="sxs-lookup"><span data-stu-id="aed79-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="aed79-251">然后，提供的成员可以构造该对象类型的实例：</span><span class="sxs-lookup"><span data-stu-id="aed79-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="aed79-252">在这种情况下，可以（可选）通过在构造时将此类型指定为，将此类型用作类型擦除 `baseType` `ProvidedTypeDefinition` ：</span><span class="sxs-lookup"><span data-stu-id="aed79-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="aed79-253">关键课程</span><span class="sxs-lookup"><span data-stu-id="aed79-253">Key Lessons</span></span>

<span data-ttu-id="aed79-254">上一部分介绍了如何创建简单的擦除类型提供程序，该提供程序提供一系列类型、属性和方法。</span><span class="sxs-lookup"><span data-stu-id="aed79-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="aed79-255">本部分还介绍了类型擦除的概念，包括提供类型提供程序中的已删除类型的一些优点和缺点，并讨论了已擦除的类型的表示形式。</span><span class="sxs-lookup"><span data-stu-id="aed79-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="aed79-256">使用静态参数的类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="aed79-257">即使在访问接口不需要访问任何本地或远程数据的情况下，通过静态数据参数化类型提供程序的能力也能实现很多有趣的方案。</span><span class="sxs-lookup"><span data-stu-id="aed79-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="aed79-258">在本部分中，你将了解将此类提供程序组合在一起的一些基本方法。</span><span class="sxs-lookup"><span data-stu-id="aed79-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="aed79-259">类型检查 Regex 提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="aed79-260">假设要实现用于 <xref:System.Text.RegularExpressions.Regex> 在提供以下编译时保证的接口中包装 .net 库的正则表达式的类型提供程序：</span><span class="sxs-lookup"><span data-stu-id="aed79-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="aed79-261">正在验证正则表达式是否有效。</span><span class="sxs-lookup"><span data-stu-id="aed79-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="aed79-262">提供基于正则表达式中的任何组名称的匹配项的命名属性。</span><span class="sxs-lookup"><span data-stu-id="aed79-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="aed79-263">本部分说明如何使用类型提供程序创建 `RegexTyped` 正则表达式模式参数化的类型以提供这些优点。</span><span class="sxs-lookup"><span data-stu-id="aed79-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="aed79-264">如果提供的模式无效，则编译器将报告错误，类型提供程序可以从模式中提取组，以便可以通过使用匹配的命名属性来访问这些组。</span><span class="sxs-lookup"><span data-stu-id="aed79-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="aed79-265">设计类型提供程序时，应考虑其公开的 API 应如何向最终用户显示，以及此设计如何转换为 .NET 代码。</span><span class="sxs-lookup"><span data-stu-id="aed79-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="aed79-266">下面的示例演示如何使用此类 API 获取区域代码的组件：</span><span class="sxs-lookup"><span data-stu-id="aed79-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="aed79-267">下面的示例演示类型提供程序如何转换这些调用：</span><span class="sxs-lookup"><span data-stu-id="aed79-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="aed79-268">请注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="aed79-268">Note the following points:</span></span>

- <span data-ttu-id="aed79-269">标准 Regex 类型表示参数化 `RegexTyped` 类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="aed79-270">`RegexTyped`构造函数导致调用 Regex 构造函数，并传入模式的静态类型参数。</span><span class="sxs-lookup"><span data-stu-id="aed79-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="aed79-271">方法的结果 `Match` 以标准 <xref:System.Text.RegularExpressions.Match> 类型表示。</span><span class="sxs-lookup"><span data-stu-id="aed79-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="aed79-272">每个命名组都生成提供的属性，而访问属性会导致在匹配的集合上使用索引器 `Groups` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="aed79-273">下面的代码是实现此类提供程序的逻辑的核心，此示例省略了向所提供类型添加所有成员的情况。</span><span class="sxs-lookup"><span data-stu-id="aed79-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="aed79-274">有关每个已添加成员的信息，请参阅本主题后面的相应部分。</span><span class="sxs-lookup"><span data-stu-id="aed79-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="aed79-275">有关完整的代码，请从 CodePlex 网站上的[F # 3.0 示例包](https://archive.codeplex.com/?p=fsharp3sample)下载该示例。</span><span class="sxs-lookup"><span data-stu-id="aed79-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="aed79-276">请注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="aed79-276">Note the following points:</span></span>

- <span data-ttu-id="aed79-277">该类型提供程序采用两个静态参数： `pattern` （必需）和（ `options` 这是可选的，因为提供了默认值）。</span><span class="sxs-lookup"><span data-stu-id="aed79-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="aed79-278">提供静态参数后，可以创建正则表达式的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="aed79-279">如果正则表达式格式不正确，此实例将引发异常，并向用户报告此错误。</span><span class="sxs-lookup"><span data-stu-id="aed79-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="aed79-280">在 `DefineStaticParameters` 回调中，可以定义在提供参数后将返回的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="aed79-281">此代码会将设置 `HideObjectMethods` 为 true，以使 IntelliSense 体验保持简单。</span><span class="sxs-lookup"><span data-stu-id="aed79-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="aed79-282">此属性将导致 `Equals` `GetHashCode` `Finalize` `GetType` 从提供的对象的 IntelliSense 列表中抑制、、和成员。</span><span class="sxs-lookup"><span data-stu-id="aed79-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="aed79-283">使用 `obj` 作为方法的基类型，但会将 `Regex` 对象用作此类型的运行时表示形式，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="aed79-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="aed79-284">`Regex` <xref:System.ArgumentException> 当正则表达式无效时，对构造函数的调用将引发。</span><span class="sxs-lookup"><span data-stu-id="aed79-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="aed79-285">编译器将捕获此异常并向用户报告编译时或 Visual Studio 编辑器中的错误消息。</span><span class="sxs-lookup"><span data-stu-id="aed79-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="aed79-286">此异常允许验证正则表达式，而无需运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="aed79-287">上面定义的类型不太有用，因为它不包含任何有意义的方法或属性。</span><span class="sxs-lookup"><span data-stu-id="aed79-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="aed79-288">首先，添加一个静态 `IsMatch` 方法：</span><span class="sxs-lookup"><span data-stu-id="aed79-288">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

<span data-ttu-id="aed79-289">前面的代码定义了一个方法 `IsMatch` ，该方法采用字符串作为输入并返回 `bool` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="aed79-290">唯一难用的部分是 `args` 定义中的参数 `InvokeCode` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="aed79-291">在此示例中， `args` 是表示此方法的参数的引号列表。</span><span class="sxs-lookup"><span data-stu-id="aed79-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="aed79-292">如果该方法是实例方法，则第一个参数表示 `this` 参数。</span><span class="sxs-lookup"><span data-stu-id="aed79-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="aed79-293">但对于静态方法，参数只是方法的显式参数。</span><span class="sxs-lookup"><span data-stu-id="aed79-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="aed79-294">请注意，带引号的值的类型应与指定的返回类型（在本例中为 `bool` ）匹配。</span><span class="sxs-lookup"><span data-stu-id="aed79-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="aed79-295">另请注意，此代码使用 `AddXmlDoc` 方法来确保所提供的方法也具有可通过 IntelliSense 提供的有用文档。</span><span class="sxs-lookup"><span data-stu-id="aed79-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="aed79-296">接下来，添加实例 Match 方法。</span><span class="sxs-lookup"><span data-stu-id="aed79-296">Next, add an instance Match method.</span></span> <span data-ttu-id="aed79-297">但是，此方法应返回提供的类型的值， `Match` 以便能够以强类型方式访问组。</span><span class="sxs-lookup"><span data-stu-id="aed79-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="aed79-298">因此，首先声明 `Match` 类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="aed79-299">由于此类型依赖于以静态参数形式提供的模式，因此，此类型必须嵌套在参数化类型定义中：</span><span class="sxs-lookup"><span data-stu-id="aed79-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="aed79-300">然后，将一个属性添加到每个组的匹配类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="aed79-301">在运行时，匹配项表示为 <xref:System.Text.RegularExpressions.Match> 值，因此，定义属性的引用必须使用 <xref:System.Text.RegularExpressions.Match.Groups> 索引属性来获取相关组。</span><span class="sxs-lookup"><span data-stu-id="aed79-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

<span data-ttu-id="aed79-302">同样，请注意，将 XML 文档添加到提供的属性。</span><span class="sxs-lookup"><span data-stu-id="aed79-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="aed79-303">另请注意，如果提供了函数，则可以读取属性 `GetterCode` ; 如果提供了函数，则可以编写属性 `SetterCode` ，因此，生成的属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="aed79-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="aed79-304">现在，你可以创建返回此类型的值的实例方法 `Match` ：</span><span class="sxs-lookup"><span data-stu-id="aed79-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="aed79-305">由于您正在创建实例方法，因此 `args.[0]` 表示在 `RegexTyped` 其上调用方法的实例， `args.[1]` 是输入参数。</span><span class="sxs-lookup"><span data-stu-id="aed79-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="aed79-306">最后，提供一个构造函数，以便可以创建提供的类型的实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="aed79-307">构造函数只需擦除到标准 .NET 正则表达式实例的创建，这会再次装箱到对象，因为它 `obj` 是所提供的类型的擦除。</span><span class="sxs-lookup"><span data-stu-id="aed79-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="aed79-308">通过此更改，本主题中前面指定的示例 API 用法按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="aed79-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="aed79-309">以下代码已完成，并且是最终的：</span><span class="sxs-lookup"><span data-stu-id="aed79-309">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="aed79-310">关键课程</span><span class="sxs-lookup"><span data-stu-id="aed79-310">Key Lessons</span></span>

<span data-ttu-id="aed79-311">本部分介绍如何创建在其静态参数上操作的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="aed79-312">提供程序将检查静态参数，并根据其值提供操作。</span><span class="sxs-lookup"><span data-stu-id="aed79-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="aed79-313">本地数据支持的类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="aed79-314">通常，可能需要类型提供程序基于静态参数提供 Api，而不是本地或远程系统中的信息。</span><span class="sxs-lookup"><span data-stu-id="aed79-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="aed79-315">本部分讨论基于本地数据（如本地数据文件）的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="aed79-316">简单 CSV 文件提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-316">Simple CSV File Provider</span></span>

<span data-ttu-id="aed79-317">作为一个简单的示例，请考虑用逗号分隔值（CSV）格式访问科学数据的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="aed79-318">本部分假定 CSV 文件包含标题行，后跟浮点数据，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="aed79-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="aed79-319">距离（计量）</span><span class="sxs-lookup"><span data-stu-id="aed79-319">Distance (meter)</span></span>|<span data-ttu-id="aed79-320">时间（秒）</span><span class="sxs-lookup"><span data-stu-id="aed79-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="aed79-321">50.0</span><span class="sxs-lookup"><span data-stu-id="aed79-321">50.0</span></span>|<span data-ttu-id="aed79-322">3.7</span><span class="sxs-lookup"><span data-stu-id="aed79-322">3.7</span></span>|
|<span data-ttu-id="aed79-323">100.0</span><span class="sxs-lookup"><span data-stu-id="aed79-323">100.0</span></span>|<span data-ttu-id="aed79-324">5.2</span><span class="sxs-lookup"><span data-stu-id="aed79-324">5.2</span></span>|
|<span data-ttu-id="aed79-325">150.0</span><span class="sxs-lookup"><span data-stu-id="aed79-325">150.0</span></span>|<span data-ttu-id="aed79-326">6.4</span><span class="sxs-lookup"><span data-stu-id="aed79-326">6.4</span></span>|

<span data-ttu-id="aed79-327">本部分说明如何提供可用于获取具有 `Distance` 类型的属性的行 `float<meter>` 和 `Time` 类型的属性的类型 `float<second>` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="aed79-328">为简单起见，进行了以下假设：</span><span class="sxs-lookup"><span data-stu-id="aed79-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="aed79-329">标头名称要么不小于单位，要么格式为 "Name （unit）" 且不包含逗号。</span><span class="sxs-lookup"><span data-stu-id="aed79-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="aed79-330">单元是所有系统国际（SI）单位，因为[Fsharp.core 模块（F #）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模块定义。</span><span class="sxs-lookup"><span data-stu-id="aed79-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="aed79-331">单元是简单的（例如计量），而不是复合（例如，计量/秒）。</span><span class="sxs-lookup"><span data-stu-id="aed79-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="aed79-332">所有列都包含浮点数据。</span><span class="sxs-lookup"><span data-stu-id="aed79-332">All columns contain floating point data.</span></span>

<span data-ttu-id="aed79-333">更完整的提供程序会放宽这些限制。</span><span class="sxs-lookup"><span data-stu-id="aed79-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="aed79-334">第一步是考虑 API 的外观。</span><span class="sxs-lookup"><span data-stu-id="aed79-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="aed79-335">由于给出了包含上表内容的 `info.csv` 文件（采用逗号分隔格式），提供程序的用户应该能够编写与以下示例类似的代码：</span><span class="sxs-lookup"><span data-stu-id="aed79-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="aed79-336">在这种情况下，编译器应将这些调用转换为类似于以下示例的内容：</span><span class="sxs-lookup"><span data-stu-id="aed79-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="aed79-337">最佳转换需要类型提供程序 `CsvFile` 在类型提供程序的程序集中定义实类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="aed79-338">类型提供程序经常依赖几个帮助程序类型和方法来包装重要逻辑。</span><span class="sxs-lookup"><span data-stu-id="aed79-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="aed79-339">由于度量值会在运行时被清除，因此可以使用 `float[]` 作为行的已擦除类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="aed79-340">编译器会将不同的列视为具有不同的度量值类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="aed79-341">例如，我们的示例中的第一列的类型为，第二列的类型为 `float<meter>` `float<second>` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="aed79-342">但是，清除的表示形式可能会变得非常简单。</span><span class="sxs-lookup"><span data-stu-id="aed79-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="aed79-343">下面的代码显示了实现的核心。</span><span class="sxs-lookup"><span data-stu-id="aed79-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="aed79-344">请注意以下有关实现的要点：</span><span class="sxs-lookup"><span data-stu-id="aed79-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="aed79-345">重载的构造函数允许读取原始文件或具有相同架构的文件。</span><span class="sxs-lookup"><span data-stu-id="aed79-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="aed79-346">当你为本地或远程数据源编写类型提供程序时，此模式很常见，并且此模式允许将本地文件用作远程数据的模板。</span><span class="sxs-lookup"><span data-stu-id="aed79-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="aed79-347">您可以使用传入到类型提供程序构造函数的[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)值来解析相对文件名。</span><span class="sxs-lookup"><span data-stu-id="aed79-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="aed79-348">您可以使用 `AddDefinitionLocation` 方法来定义所提供属性的位置。</span><span class="sxs-lookup"><span data-stu-id="aed79-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="aed79-349">因此，如果在 `Go To Definition` 提供的属性上使用，则将在 Visual Studio 中打开 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="aed79-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="aed79-350">您可以使用该 `ProvidedMeasureBuilder` 类型来查找 SI 单位并生成相关 `float<_>` 类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="aed79-351">关键课程</span><span class="sxs-lookup"><span data-stu-id="aed79-351">Key Lessons</span></span>

<span data-ttu-id="aed79-352">本部分说明了如何使用数据源本身中包含的简单架构为本地数据源创建类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="aed79-353">深入探索</span><span class="sxs-lookup"><span data-stu-id="aed79-353">Going Further</span></span>

<span data-ttu-id="aed79-354">以下部分包含有关进一步研究的建议。</span><span class="sxs-lookup"><span data-stu-id="aed79-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="aed79-355">查看已清除类型的已编译代码</span><span class="sxs-lookup"><span data-stu-id="aed79-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="aed79-356">若要让你了解如何使用类型提供程序与发出的代码相对应的情况，请参阅以下函数，方法是使用 `HelloWorldTypeProvider` 本主题前面部分中使用的。</span><span class="sxs-lookup"><span data-stu-id="aed79-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="aed79-357">下面是通过使用 ildasm 生成的代码反编译的图像：</span><span class="sxs-lookup"><span data-stu-id="aed79-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="aed79-358">如示例所示， `Type1` 已清除类型和属性的所有提到 `InstanceProperty` ，只保留对所涉及的运行时类型的操作。</span><span class="sxs-lookup"><span data-stu-id="aed79-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="aed79-359">类型提供程序的设计和命名约定</span><span class="sxs-lookup"><span data-stu-id="aed79-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="aed79-360">在创作类型提供程序时，请遵循以下约定。</span><span class="sxs-lookup"><span data-stu-id="aed79-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="aed79-361">**连接协议的提供程序**通常，数据和服务连接协议的大多数提供程序 Dll 的名称（如 OData 或 SQL 连接）应以或结尾 `TypeProvider` `TypeProviders` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="aed79-362">例如，使用类似于以下字符串的 DLL 名称：</span><span class="sxs-lookup"><span data-stu-id="aed79-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="aed79-363">确保你提供的类型为相应命名空间的成员，并指示你实现的连接协议：</span><span class="sxs-lookup"><span data-stu-id="aed79-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="aed79-364">**用于常规编码的实用工具提供程序**。</span><span class="sxs-lookup"><span data-stu-id="aed79-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="aed79-365">对于适用于正则表达式的实用工具类型提供程序，类型提供程序可能是基库的一部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="aed79-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="aed79-366">在这种情况下，提供的类型会根据正常的 .NET 设计约定显示在适当的点上：</span><span class="sxs-lookup"><span data-stu-id="aed79-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="aed79-367">**单独数据源**。</span><span class="sxs-lookup"><span data-stu-id="aed79-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="aed79-368">某些类型提供程序连接到单个专用数据源并只提供数据。</span><span class="sxs-lookup"><span data-stu-id="aed79-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="aed79-369">在这种情况下，应删除此 `TypeProvider` 后缀并使用标准的 .net 命名约定：</span><span class="sxs-lookup"><span data-stu-id="aed79-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="aed79-370">有关详细信息，请参阅 `GetConnection` 本主题后面部分介绍的设计约定。</span><span class="sxs-lookup"><span data-stu-id="aed79-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="aed79-371">类型提供程序的设计模式</span><span class="sxs-lookup"><span data-stu-id="aed79-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="aed79-372">以下各节介绍了在创作类型提供程序时可以使用的设计模式。</span><span class="sxs-lookup"><span data-stu-id="aed79-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="aed79-373">GetConnection 设计模式</span><span class="sxs-lookup"><span data-stu-id="aed79-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="aed79-374">大多数类型提供程序应编写为使用 `GetConnection` fsharp.core 中的类型提供程序使用的模式，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="aed79-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="aed79-375">由远程数据和服务支持的类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="aed79-376">在创建由远程数据和服务支持的类型提供程序之前，必须考虑连接编程中固有的一系列问题。</span><span class="sxs-lookup"><span data-stu-id="aed79-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="aed79-377">这些问题包括以下注意事项：</span><span class="sxs-lookup"><span data-stu-id="aed79-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="aed79-378">架构映射</span><span class="sxs-lookup"><span data-stu-id="aed79-378">schema mapping</span></span>

- <span data-ttu-id="aed79-379">发生架构更改时的活动和无效</span><span class="sxs-lookup"><span data-stu-id="aed79-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="aed79-380">架构缓存</span><span class="sxs-lookup"><span data-stu-id="aed79-380">schema caching</span></span>

- <span data-ttu-id="aed79-381">数据访问操作的异步实现</span><span class="sxs-lookup"><span data-stu-id="aed79-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="aed79-382">支持查询，包括 LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="aed79-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="aed79-383">凭据和身份验证</span><span class="sxs-lookup"><span data-stu-id="aed79-383">credentials and authentication</span></span>

<span data-ttu-id="aed79-384">本主题不会进一步探讨这些问题。</span><span class="sxs-lookup"><span data-stu-id="aed79-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="aed79-385">其他创作技术</span><span class="sxs-lookup"><span data-stu-id="aed79-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="aed79-386">编写自己的类型提供程序时，可能需要使用以下其他技术。</span><span class="sxs-lookup"><span data-stu-id="aed79-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="aed79-387">按需创建类型和成员</span><span class="sxs-lookup"><span data-stu-id="aed79-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="aed79-388">ProvidedType API 具有延迟版本的 AddMember。</span><span class="sxs-lookup"><span data-stu-id="aed79-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="aed79-389">这些版本用于创建类型的按需空间。</span><span class="sxs-lookup"><span data-stu-id="aed79-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="aed79-390">提供数组类型和泛型类型实例化</span><span class="sxs-lookup"><span data-stu-id="aed79-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="aed79-391">通过在任何实例上使用 normal、和，可使提供的成员（其签名包括数组类型、byref 类型和泛型类型的实例化） `MakeArrayType` `MakePointerType` `MakeGenericType` <xref:System.Type> ，其中包括 `ProvidedTypeDefinitions` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="aed79-392">在某些情况下，您可能必须使用中的帮助器 `ProvidedTypeBuilder.MakeGenericType` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="aed79-393">有关更多详细信息，请参阅[类型提供程序 SDK 文档](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)。</span><span class="sxs-lookup"><span data-stu-id="aed79-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="aed79-394">提供度量单位批注</span><span class="sxs-lookup"><span data-stu-id="aed79-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="aed79-395">ProvidedTypes API 提供了提供度量值注释的帮助器。</span><span class="sxs-lookup"><span data-stu-id="aed79-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="aed79-396">例如，若要提供类型 `float<kg>` ，请使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="aed79-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="aed79-397">若要提供类型 `Nullable<decimal<kg/m^2>>` ，请使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="aed79-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="aed79-398">访问项目本地资源或脚本本地资源</span><span class="sxs-lookup"><span data-stu-id="aed79-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="aed79-399">在构造过程中，可以为类型提供程序的每个实例指定一个 `TypeProviderConfig` 值。</span><span class="sxs-lookup"><span data-stu-id="aed79-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="aed79-400">此值包含提供程序的 "解析文件夹" （即，编译的项目文件夹或包含脚本的目录）、被引用程序集的列表和其他信息。</span><span class="sxs-lookup"><span data-stu-id="aed79-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="aed79-401">失效</span><span class="sxs-lookup"><span data-stu-id="aed79-401">Invalidation</span></span>

<span data-ttu-id="aed79-402">提供程序可以引发无效信号，以通知 F # 语言服务，架构假设可能已发生更改。</span><span class="sxs-lookup"><span data-stu-id="aed79-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="aed79-403">当发生失效时，如果提供程序承载于 Visual Studio 中，将重做 typecheck。</span><span class="sxs-lookup"><span data-stu-id="aed79-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="aed79-404">当提供程序托管在 F# 交互窗口或由 F # 编译器（fsc.exe）承载时，将忽略此信号。</span><span class="sxs-lookup"><span data-stu-id="aed79-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="aed79-405">缓存架构信息</span><span class="sxs-lookup"><span data-stu-id="aed79-405">Caching Schema Information</span></span>

<span data-ttu-id="aed79-406">提供程序通常必须缓存对架构信息的访问。</span><span class="sxs-lookup"><span data-stu-id="aed79-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="aed79-407">应使用指定为静态参数或用户数据的文件名来存储缓存的数据。</span><span class="sxs-lookup"><span data-stu-id="aed79-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="aed79-408">架构缓存的一个示例是 `LocalSchemaFile` 程序集的类型提供程序中的 `FSharp.Data.TypeProviders` 参数。</span><span class="sxs-lookup"><span data-stu-id="aed79-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="aed79-409">在这些提供程序的实现中，此静态参数指示类型提供程序使用指定的本地文件中的架构信息，而不是通过网络访问数据源。</span><span class="sxs-lookup"><span data-stu-id="aed79-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="aed79-410">若要使用缓存的架构信息，还必须将静态参数设置 `ForceUpdate` 为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="aed79-411">您可以使用类似的技术来启用联机和脱机数据访问。</span><span class="sxs-lookup"><span data-stu-id="aed79-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="aed79-412">支持程序集</span><span class="sxs-lookup"><span data-stu-id="aed79-412">Backing Assembly</span></span>

<span data-ttu-id="aed79-413">在编译 `.dll` 或文件时 `.exe` ，生成的类型的支持 .dll 文件将静态链接到生成的程序集中。</span><span class="sxs-lookup"><span data-stu-id="aed79-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="aed79-414">通过将中间语言（IL）类型定义和任何托管资源从支持程序集复制到最终程序集来创建此链接。</span><span class="sxs-lookup"><span data-stu-id="aed79-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="aed79-415">使用 F# 交互窗口时，不会复制后备 .dll 文件，而是直接加载到 F# 交互窗口进程。</span><span class="sxs-lookup"><span data-stu-id="aed79-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="aed79-416">类型提供程序中的异常和诊断</span><span class="sxs-lookup"><span data-stu-id="aed79-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="aed79-417">提供的类型中所有成员的所有使用可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="aed79-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="aed79-418">在所有情况下，如果类型提供程序引发异常，则宿主编译器会将错误的属性指定给特定的类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="aed79-419">类型提供程序异常决不会导致内部编译器错误。</span><span class="sxs-lookup"><span data-stu-id="aed79-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="aed79-420">类型提供程序无法报告警告。</span><span class="sxs-lookup"><span data-stu-id="aed79-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="aed79-421">在 F # 编译器、F # 开发环境或 F# 交互窗口中承载类型提供程序时，将捕获该提供程序的所有异常。</span><span class="sxs-lookup"><span data-stu-id="aed79-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="aed79-422">Message 属性始终是错误文本，并且不会显示任何堆栈跟踪。</span><span class="sxs-lookup"><span data-stu-id="aed79-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="aed79-423">如果要引发异常，可以引发以下示例： `System.NotSupportedException` 、 `System.IO.IOException` 、 `System.Exception` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="aed79-424">提供生成的类型</span><span class="sxs-lookup"><span data-stu-id="aed79-424">Providing Generated Types</span></span>

<span data-ttu-id="aed79-425">到目前为止，本文档介绍了如何提供擦除的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="aed79-426">你还可以使用 F # 中的类型提供程序机制来提供生成的类型，这些类型将作为真实 .NET 类型定义添加到用户的程序中。</span><span class="sxs-lookup"><span data-stu-id="aed79-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="aed79-427">您必须使用类型定义引用生成的提供类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="aed79-428">F # 3.0 发行版中的 ProvidedTypes-0.2 helper 代码仅对提供生成的类型提供有限支持。</span><span class="sxs-lookup"><span data-stu-id="aed79-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="aed79-429">对于生成的类型定义，以下语句必须为 true：</span><span class="sxs-lookup"><span data-stu-id="aed79-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="aed79-430">`isErased` 必须设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="aed79-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="aed79-431">必须将生成的类型添加到新构造的 `ProvidedAssembly()` ，它表示生成的代码片段的容器。</span><span class="sxs-lookup"><span data-stu-id="aed79-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="aed79-432">提供程序必须有一个程序集，该程序集具有包含在磁盘上的匹配 .dll 文件的实际后备 .NET .dll 文件。</span><span class="sxs-lookup"><span data-stu-id="aed79-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="aed79-433">规则和限制</span><span class="sxs-lookup"><span data-stu-id="aed79-433">Rules and Limitations</span></span>

<span data-ttu-id="aed79-434">编写类型提供程序时，请记住以下规则和限制。</span><span class="sxs-lookup"><span data-stu-id="aed79-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="aed79-435">提供的类型必须是可访问的</span><span class="sxs-lookup"><span data-stu-id="aed79-435">Provided types must be reachable</span></span>

<span data-ttu-id="aed79-436">应可从非嵌套类型访问所有提供的类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="aed79-437">非嵌套类型是在对 `TypeProviderForNamespaces` 构造函数的调用或对的调用中提供的 `AddNamespace` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="aed79-438">例如，如果提供程序提供类型 `StaticClass.P : T` ，则必须确保 T 为非嵌套类型或嵌套在一个类型下。</span><span class="sxs-lookup"><span data-stu-id="aed79-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="aed79-439">例如，某些提供程序有一个 `DataTypes` 包含这些类型的静态类，例如 `T1, T2, T3, ...` 。</span><span class="sxs-lookup"><span data-stu-id="aed79-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="aed79-440">否则，此错误表明找到了对程序集 A 中的类型 T 的引用，但无法在该程序集中找到该类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="aed79-441">如果出现此错误，请验证是否可以从提供程序类型中访问所有子类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="aed79-442">注意：这些 `T1, T2, T3...` 类型称为 "*即时*类型"。</span><span class="sxs-lookup"><span data-stu-id="aed79-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="aed79-443">请记住将其放在可访问的命名空间或父类型中。</span><span class="sxs-lookup"><span data-stu-id="aed79-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="aed79-444">类型提供程序机制的限制</span><span class="sxs-lookup"><span data-stu-id="aed79-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="aed79-445">F # 中的类型提供程序机制具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="aed79-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="aed79-446">F # 中的类型提供程序的基础结构不支持提供的泛型类型或提供的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="aed79-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="aed79-447">该机制不支持具有静态参数的嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="aed79-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="aed79-448">开发提示</span><span class="sxs-lookup"><span data-stu-id="aed79-448">Development Tips</span></span>

<span data-ttu-id="aed79-449">在开发过程中，你可能会发现以下提示很有用：</span><span class="sxs-lookup"><span data-stu-id="aed79-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="aed79-450">运行 Visual Studio 的两个实例</span><span class="sxs-lookup"><span data-stu-id="aed79-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="aed79-451">您可以在一个实例中开发类型提供程序，并在另一个实例中测试该提供程序，因为测试 IDE 将对 .dll 文件执行锁定，从而阻止重新生成类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="aed79-452">因此，在第一个实例中生成提供程序时，必须关闭 Visual Studio 的第二个实例，然后必须在生成提供程序之后重新打开第二个实例。</span><span class="sxs-lookup"><span data-stu-id="aed79-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="aed79-453">使用 fsc.exe 的调用调试类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="aed79-454">您可以使用以下工具调用类型提供程序：</span><span class="sxs-lookup"><span data-stu-id="aed79-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="aed79-455">fsc.exe （F # 命令行编译器）</span><span class="sxs-lookup"><span data-stu-id="aed79-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="aed79-456">fsi.exe （F# 交互窗口编译器）</span><span class="sxs-lookup"><span data-stu-id="aed79-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="aed79-457">devenv （Visual Studio）</span><span class="sxs-lookup"><span data-stu-id="aed79-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="aed79-458">通常可以使用 fsc.exe 在测试脚本文件（例如 .fsx）上最轻松地调试类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed79-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="aed79-459">你可以从命令提示符处启动调试器。</span><span class="sxs-lookup"><span data-stu-id="aed79-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="aed79-460">您可以使用打印到 stdout 的日志记录。</span><span class="sxs-lookup"><span data-stu-id="aed79-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="aed79-461">请参阅</span><span class="sxs-lookup"><span data-stu-id="aed79-461">See also</span></span>

- [<span data-ttu-id="aed79-462">类型提供程序</span><span class="sxs-lookup"><span data-stu-id="aed79-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="aed79-463">类型提供程序 SDK</span><span class="sxs-lookup"><span data-stu-id="aed79-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
