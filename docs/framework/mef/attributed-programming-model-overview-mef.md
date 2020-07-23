---
title: 特性化编程模型概述 (MEF)
description: 开始使用特性化编程模型，该模型是 .NET 中 Managed Extensibility Framework (MEF) 的默认编程模型。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: aea3a19ffe6f177901e5c0839b618bb36f573beb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281363"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="a4841-103">特性化编程模型概述 (MEF)</span><span class="sxs-lookup"><span data-stu-id="a4841-103">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="a4841-104">在 Managed Extensibility Framework (MEF) 中， *编程模型* 是定义 MEF 所操作的概念性对象集的特定方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-104">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="a4841-105">这些概念对象包括部件、导入和导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-105">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="a4841-106">MEF 使用这些对象，但未指定应如何表示这些对象。</span><span class="sxs-lookup"><span data-stu-id="a4841-106">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="a4841-107">因此，将可能有各种各样的编程模型，其中包括自定义编程模型。</span><span class="sxs-lookup"><span data-stu-id="a4841-107">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="a4841-108">在 MEF 中使用的默认编程模型是 *特性化编程模型*。</span><span class="sxs-lookup"><span data-stu-id="a4841-108">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="a4841-109">在特性化编程模型中，部件、导入、导出和其他对象是用修饰普通 .NET Framework 类的特性定义的。</span><span class="sxs-lookup"><span data-stu-id="a4841-109">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="a4841-110">本主题介绍如何使用特性化编程模型提供的特性来创建 MEF 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a4841-110">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="a4841-111">导入和导出基础知识</span><span class="sxs-lookup"><span data-stu-id="a4841-111">Import and Export Basics</span></span>

<span data-ttu-id="a4841-112">*导出* 是部件向容器中的其他部件提供的一个值，而 *导入* 是部件向要通过可用导出填充的容器提出的要求。</span><span class="sxs-lookup"><span data-stu-id="a4841-112">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="a4841-113">在特性化编程模型中，导入和导出由使用 `Import` 和 `Export` 特性的修饰类或成员声明。</span><span class="sxs-lookup"><span data-stu-id="a4841-113">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="a4841-114">`Export` 特性可修饰类、字段、属性或方法，而 `Import` 特性可修饰字段、属性或构造函数参数。</span><span class="sxs-lookup"><span data-stu-id="a4841-114">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="a4841-115">为了使导入与导出相匹配，该导入和该导出必须具有相同的 *协定*。</span><span class="sxs-lookup"><span data-stu-id="a4841-115">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="a4841-116">协定由一个字符串（称为 *协定名称*）和已导出或导入对象的类型（称为 *协定类型*）组成。</span><span class="sxs-lookup"><span data-stu-id="a4841-116">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="a4841-117">只有在协定名称和协定类型均匹配时，才会认为导出能够满足特定导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-117">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="a4841-118">协定参数中的其中任意一个或两者可能为隐式也可能为显式。</span><span class="sxs-lookup"><span data-stu-id="a4841-118">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="a4841-119">下面的代码示例演示一个声明基础导入的类。</span><span class="sxs-lookup"><span data-stu-id="a4841-119">The following code shows a class that declares a basic import.</span></span>

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

<span data-ttu-id="a4841-120">在此导入中， `Import` 特性既未附加协定类型参数，也未附加协定名称参数。</span><span class="sxs-lookup"><span data-stu-id="a4841-120">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="a4841-121">因此，这两者均将从修饰的属性推断而出。</span><span class="sxs-lookup"><span data-stu-id="a4841-121">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="a4841-122">在这种情况下，协定类型将为 `IMyAddin`，而协定名称将为依据该协定类型创建的唯一字符串。</span><span class="sxs-lookup"><span data-stu-id="a4841-122">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="a4841-123">（换言之，协定名称将仅与其名称同样从类型 `IMyAddin`推断而出的导出匹配。）</span><span class="sxs-lookup"><span data-stu-id="a4841-123">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="a4841-124">下面的示例演示与前面的导入匹配的导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-124">The following shows an export that matches the previous import.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="a4841-125">在此导出中，由于协定类型指定为 `IMyAddin` 特性的参数，因此协定类型为 `Export` 。</span><span class="sxs-lookup"><span data-stu-id="a4841-125">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="a4841-126">导出的类型必须与协定类型相同、派生自协定类型，或者实现协定类型（如果导出的类型为接口）。</span><span class="sxs-lookup"><span data-stu-id="a4841-126">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="a4841-127">在此导出中，实际类型 `MyLogger` 实现接口 `IMyAddin`。</span><span class="sxs-lookup"><span data-stu-id="a4841-127">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="a4841-128">协定名称是从协定类型推断而出的，这意味着此导出将与前面的导入匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-128">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="a4841-129">通常应对公共类或成员声明导出和导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-129">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="a4841-130">其他声明也受支持，但如果导出或导入私有成员、受保护成员或内部成员，将会损坏部件的隔离模型，因此建议不要这样做。</span><span class="sxs-lookup"><span data-stu-id="a4841-130">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="a4841-131">协定类型对于要视为匹配的导出和导入必须完全匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-131">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="a4841-132">请看下面的导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-132">Consider the following export.</span></span>

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="a4841-133">在此导出中，协定类型为 `MyLogger` ，而不是 `IMyAddin`。</span><span class="sxs-lookup"><span data-stu-id="a4841-133">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="a4841-134">即使 `MyLogger` 实现 `IMyAddin`并因此可强制转换为 `IMyAddin` 对象，此导出也将由于协定类型不匹配而与前面的导入不匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-134">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="a4841-135">通常不必指定协定名称，并且应依据协定类型和元数据定义大多数协定。</span><span class="sxs-lookup"><span data-stu-id="a4841-135">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="a4841-136">但是，在某些情况下，务必要直接指定协定名称。</span><span class="sxs-lookup"><span data-stu-id="a4841-136">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="a4841-137">最常见的情况是：类导出共享通用类型的若干值（例如基元）。</span><span class="sxs-lookup"><span data-stu-id="a4841-137">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="a4841-138">可将协定名称指定为 `Import` 或 `Export` 特性的第一个参数。</span><span class="sxs-lookup"><span data-stu-id="a4841-138">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="a4841-139">下面的代码演示具有指定协定名称 `MajorRevision`的导入和导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-139">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

<span data-ttu-id="a4841-140">如果未指定协定类型，将仍然会从导入或导出的类型推断出协定类型。</span><span class="sxs-lookup"><span data-stu-id="a4841-140">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="a4841-141">但是，即使显式指定了协定名称，协定类型对于要视为匹配的导入和导出也仍然必须完全匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-141">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="a4841-142">例如，如果 `MajorRevision` 字段为字符串，则推断出的协定类型将不匹配，并且导出将与导入不匹配（尽管具有相同的协定名称）。</span><span class="sxs-lookup"><span data-stu-id="a4841-142">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="a4841-143">导入和导出方法</span><span class="sxs-lookup"><span data-stu-id="a4841-143">Importing and Exporting a Method</span></span>

<span data-ttu-id="a4841-144">`Export` 特性还可以按照与类、属性或函数相同的方式声明方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-144">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="a4841-145">方法导出必须将协定类型或协定名称指定为类型，并且无法推断。</span><span class="sxs-lookup"><span data-stu-id="a4841-145">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="a4841-146">指定的类型可以为自定义委托或泛型类型，例如 `Func`。</span><span class="sxs-lookup"><span data-stu-id="a4841-146">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="a4841-147">下面的类导出一个名为 `DoSomething`的方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-147">The following class exports a method named `DoSomething`.</span></span>

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

<span data-ttu-id="a4841-148">在此类中， `DoSomething` 方法采用单个 `int` 参数，并返回 `string`。</span><span class="sxs-lookup"><span data-stu-id="a4841-148">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="a4841-149">若要匹配此导出，导入部件必须适当的成员。</span><span class="sxs-lookup"><span data-stu-id="a4841-149">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="a4841-150">下面的类导入 `DoSomething` 方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-150">The following class imports the `DoSomething` method.</span></span>

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

<span data-ttu-id="a4841-151">有关如何使用 `Func<T, T>` 对象的更多信息，请参见 <xref:System.Func%602>。</span><span class="sxs-lookup"><span data-stu-id="a4841-151">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="a4841-152">导入的类型</span><span class="sxs-lookup"><span data-stu-id="a4841-152">Types of Imports</span></span>

<span data-ttu-id="a4841-153">MEF 支持若干导入类型，其中包括动态导入、延迟导入、必备导入和可选导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-153">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="a4841-154">动态导入</span><span class="sxs-lookup"><span data-stu-id="a4841-154">Dynamic Imports</span></span>

<span data-ttu-id="a4841-155">在某些情况下，导入类可能需要与具有特定协定名称的任何类型的导出匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-155">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="a4841-156">在这种情况下，类可以声明 *动态导入*。</span><span class="sxs-lookup"><span data-stu-id="a4841-156">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="a4841-157">下面的导入与具有协定名称“TheString”的任何导出匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-157">The following import matches any export with contract name "TheString".</span></span>

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

<span data-ttu-id="a4841-158">如果协定类型从 `dynamic` 关键字推断而出，则它将与任何协定类型匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-158">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="a4841-159">在这种情况下，导入应 **始终** 指定要依据其进行匹配的协定名称。</span><span class="sxs-lookup"><span data-stu-id="a4841-159">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="a4841-160">（如果未指定协定名称，则会将导入视为未与导出匹配。）下面的两个导出均将与前面的导入匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-160">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

<span data-ttu-id="a4841-161">显然，导入类必须准备处理任意类型的对象。</span><span class="sxs-lookup"><span data-stu-id="a4841-161">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="a4841-162">延迟导入</span><span class="sxs-lookup"><span data-stu-id="a4841-162">Lazy Imports</span></span>

<span data-ttu-id="a4841-163">在某些情况下，导入类可能需要间接引用导入的对象，因此不会立即实例化该对象。</span><span class="sxs-lookup"><span data-stu-id="a4841-163">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="a4841-164">在这种情况下，类可以通过使用协定类型 *来声明* 延迟导入 `Lazy<T>`。</span><span class="sxs-lookup"><span data-stu-id="a4841-164">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="a4841-165">下面的导入属性声明一个延迟导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-165">The following importing property declares a lazy import.</span></span>

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="a4841-166">从组合引擎的角度来看，协定类型 `Lazy<T>` 将被视为与协定类型 `T`相同。</span><span class="sxs-lookup"><span data-stu-id="a4841-166">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="a4841-167">因此，前面的导入将与下面的导出匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-167">Therefore, the previous import would match the following export.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="a4841-168">可在 `Import` 特性中为延迟导入指定协定名称和协定类型，如前面的“导入和导出基础知识”一节中所述。</span><span class="sxs-lookup"><span data-stu-id="a4841-168">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="a4841-169">必备导入</span><span class="sxs-lookup"><span data-stu-id="a4841-169">Prerequisite Imports</span></span>

<span data-ttu-id="a4841-170">导出的 MEF 部件通常由组合引擎创建，以响应填写匹配的导入的直接请求或需求。</span><span class="sxs-lookup"><span data-stu-id="a4841-170">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="a4841-171">默认情况下，在创建部件时，组合引擎将使用无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="a4841-171">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="a4841-172">若要使该引擎使用其他构造函数，你可以用 `ImportingConstructor` 特性标记它。</span><span class="sxs-lookup"><span data-stu-id="a4841-172">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="a4841-173">每个部件都可能只有一个供组合引擎使用的构造函数。</span><span class="sxs-lookup"><span data-stu-id="a4841-173">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="a4841-174">如果不提供无参数构造函数和 `ImportingConstructor` 特性，或者提供多个 `ImportingConstructor` 特性，将会产生错误。</span><span class="sxs-lookup"><span data-stu-id="a4841-174">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="a4841-175">为了填充用 `ImportingConstructor` 特性标记的构造函数的参数，所有这些参数均将自动声明为导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-175">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="a4841-176">这样可以方便地声明在部件初始化过程中使用的导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-176">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="a4841-177">下面的类使用 `ImportingConstructor` 来声明导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-177">The following class uses `ImportingConstructor` to declare an import.</span></span>

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

<span data-ttu-id="a4841-178">默认情况下， `ImportingConstructor` 特性为所有参数导入使用推断出的协定类型和协定名称。</span><span class="sxs-lookup"><span data-stu-id="a4841-178">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="a4841-179">可以通过用 `Import` 特性修饰参数来重写此行为，这些特性随后可显式定义协定类型和协定名称。</span><span class="sxs-lookup"><span data-stu-id="a4841-179">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="a4841-180">下面的代码演示一个使用此语法来导入派生类（而不是父类）的构造函数。</span><span class="sxs-lookup"><span data-stu-id="a4841-180">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

<span data-ttu-id="a4841-181">在使用集合参数时应特别小心。</span><span class="sxs-lookup"><span data-stu-id="a4841-181">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="a4841-182">例如，如果你使用类型为 `ImportingConstructor` 的参数在构造函数上指定 `IEnumerable<int>`，则导入将与类型为 `IEnumerable<int>`的单个导出（而不是类型为 `int`的一组导入）匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-182">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="a4841-183">若要与类型为 `int`的一组导出匹配，你必须用 `ImportMany` 特性修饰参数。</span><span class="sxs-lookup"><span data-stu-id="a4841-183">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="a4841-184">由 `ImportingConstructor` 特性声明为导入的参数也标记为 *必备导入*。</span><span class="sxs-lookup"><span data-stu-id="a4841-184">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="a4841-185">MEF 通常允许导出和导入形成 *循环*。</span><span class="sxs-lookup"><span data-stu-id="a4841-185">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="a4841-186">例如，循环是指对象 A 导入对象 B，后者反过来又导入对象 A。在一般情况下，循环不会成为问题，并且组合容器将正常构造两个对象。</span><span class="sxs-lookup"><span data-stu-id="a4841-186">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="a4841-187">当部件的构造函数需要导入的值时，该对象将无法参与循环。</span><span class="sxs-lookup"><span data-stu-id="a4841-187">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="a4841-188">如果对象 A 要求在其自身可构造之前构造对象 B，并且对象 B 导入对象 A，则循环将无法解决，并将发生组合错误。</span><span class="sxs-lookup"><span data-stu-id="a4841-188">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="a4841-189">因此，在构造函数参数上声明的导入为必备导入，必须先满足这些导入，之后才能使用需要这些导入的对象中的任何导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-189">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="a4841-190">可选导入</span><span class="sxs-lookup"><span data-stu-id="a4841-190">Optional Imports</span></span>

<span data-ttu-id="a4841-191">`Import` 特性指定部件正常运行的要求。</span><span class="sxs-lookup"><span data-stu-id="a4841-191">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="a4841-192">如果导入无法得到满足，则该部件的组合将失败，并且部件将不可用。</span><span class="sxs-lookup"><span data-stu-id="a4841-192">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="a4841-193">通过使用 *属性指定导入为* 可选 `AllowDefault` 。</span><span class="sxs-lookup"><span data-stu-id="a4841-193">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="a4841-194">在这种情况下，即使导入未与任何可用的导出匹配，组合也将成功，并且导入属性将设置为其属性类型的默认值（对于对象属性则为 `null`，对于布尔值则为 `false`，对于数值属性则为零。）下面的类使用可选导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-194">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a><span data-ttu-id="a4841-195">导入多个对象</span><span class="sxs-lookup"><span data-stu-id="a4841-195">Importing Multiple Objects</span></span>

<span data-ttu-id="a4841-196">只有当 `Import` 特性与一个导出匹配并且仅与一个导出匹配时，才能成功构成该特性。</span><span class="sxs-lookup"><span data-stu-id="a4841-196">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="a4841-197">其他类将生成组合错误。</span><span class="sxs-lookup"><span data-stu-id="a4841-197">Other cases will produce a composition error.</span></span> <span data-ttu-id="a4841-198">若要导入与同一协定匹配的多个导出，请使用 `ImportMany` 特性。</span><span class="sxs-lookup"><span data-stu-id="a4841-198">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="a4841-199">用此特性标记的导入始终是可选的。</span><span class="sxs-lookup"><span data-stu-id="a4841-199">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="a4841-200">例如，如果不存在匹配导出，组合将失败。</span><span class="sxs-lookup"><span data-stu-id="a4841-200">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="a4841-201">下面的类将导入任意数量类型为 `IMyAddin`的导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-201">The following class imports any number of exports of type `IMyAddin`.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="a4841-202">可以使用普通 `IEnumerable<T>` 语法和方法访问导入的数组。</span><span class="sxs-lookup"><span data-stu-id="a4841-202">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="a4841-203">也可以改用普通数组 (`IMyAddin[]`)。</span><span class="sxs-lookup"><span data-stu-id="a4841-203">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="a4841-204">当你将此模式与 `Lazy<T>` 语法结合使用时，它可能非常重要。</span><span class="sxs-lookup"><span data-stu-id="a4841-204">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="a4841-205">例如，通过使用 `ImportMany`、 `IEnumerable<T>`和 `Lazy<T>`，你可以导入对任意数量的对象的间接引用，并仅实例化必要的对象。</span><span class="sxs-lookup"><span data-stu-id="a4841-205">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="a4841-206">下面的类演示此模式。</span><span class="sxs-lookup"><span data-stu-id="a4841-206">The following class shows this pattern.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a><span data-ttu-id="a4841-207">避免发现</span><span class="sxs-lookup"><span data-stu-id="a4841-207">Avoiding Discovery</span></span>

<span data-ttu-id="a4841-208">在某些情况下，你可能需要防止部件作为目录的一部分被发现。</span><span class="sxs-lookup"><span data-stu-id="a4841-208">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="a4841-209">例如，部件可能是应从中继承（而不是使用）的基类。</span><span class="sxs-lookup"><span data-stu-id="a4841-209">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="a4841-210">可通过两种方式来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="a4841-210">There are two ways to accomplish this.</span></span> <span data-ttu-id="a4841-211">首先，可以对部件类使用 `abstract` 关键字。</span><span class="sxs-lookup"><span data-stu-id="a4841-211">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="a4841-212">尽管抽象类能够向派生自抽象类的类提供继承的导出，但抽象类从不提供导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-212">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="a4841-213">如果无法使类成为抽象类，你可以使用 `PartNotDiscoverable` 特性来修饰它。</span><span class="sxs-lookup"><span data-stu-id="a4841-213">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="a4841-214">用此特性修饰的部件将不会包括在任何目录中。</span><span class="sxs-lookup"><span data-stu-id="a4841-214">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="a4841-215">下面的示例演示这些模式。</span><span class="sxs-lookup"><span data-stu-id="a4841-215">The following example demonstrates these patterns.</span></span> <span data-ttu-id="a4841-216">`DataOne` 将被目录发现。</span><span class="sxs-lookup"><span data-stu-id="a4841-216">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="a4841-217">由于 `DataTwo` 是抽象的，因此它将不会被发现。</span><span class="sxs-lookup"><span data-stu-id="a4841-217">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="a4841-218">由于 `DataThree` 使用了 `PartNotDiscoverable` 特性，因此它将不会被发现。</span><span class="sxs-lookup"><span data-stu-id="a4841-218">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="a4841-219">元数据和元数据视图</span><span class="sxs-lookup"><span data-stu-id="a4841-219">Metadata and Metadata Views</span></span>

<span data-ttu-id="a4841-220">导出可提供有关自身的附加信息（称为“元数据” ）。</span><span class="sxs-lookup"><span data-stu-id="a4841-220">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="a4841-221">元数据可用于将导出的对象的属性传递到导入部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-221">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="a4841-222">导入部件可以使用此数据来决定要使用哪些导出，或收集有关导出的信息而不必构造导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-222">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="a4841-223">因此，导入必须为延迟导入才能使用元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-223">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="a4841-224">为了使用元数据，你通常会声明一个称为 *元数据视图*的接口，该接口声明哪些元数据将可用。</span><span class="sxs-lookup"><span data-stu-id="a4841-224">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="a4841-225">元数据视图接口必须只有属性，并且这些属性必须具有 `get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="a4841-225">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="a4841-226">下面的接口是一个示例元数据视图。</span><span class="sxs-lookup"><span data-stu-id="a4841-226">The following interface is an example metadata view.</span></span>

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

<span data-ttu-id="a4841-227">也可以使用泛型集合 `IDictionary<string, object>`作为元数据视图，但这样将会丧失类型检查的优点，因此应避免这样做。</span><span class="sxs-lookup"><span data-stu-id="a4841-227">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="a4841-228">通常，在元数据视图中命名的所有属性都是必需的，并且不会将未提供这些属性的任何导出视为匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-228">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="a4841-229">`DefaultValue` 特性指定属性是可选的。</span><span class="sxs-lookup"><span data-stu-id="a4841-229">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="a4841-230">如果未包括属性，则将为其分配指定为 `DefaultValue`的参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="a4841-230">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="a4841-231">下面是用元数据修饰的两个不同的类。</span><span class="sxs-lookup"><span data-stu-id="a4841-231">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="a4841-232">这两个类都将与前面的元数据视图匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-232">Both of these classes would match the previous metadata view.</span></span>

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

<span data-ttu-id="a4841-233">元数据是通过使用 `Export` 特性在 `ExportMetadata` 特性之后表示的。</span><span class="sxs-lookup"><span data-stu-id="a4841-233">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="a4841-234">每一段元数据都由一个名称/值对组成。</span><span class="sxs-lookup"><span data-stu-id="a4841-234">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="a4841-235">元数据的名称部分必须与元数据视图中相应属性的名称匹配，并且值将分配给该属性。</span><span class="sxs-lookup"><span data-stu-id="a4841-235">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="a4841-236">导入程序负责指定将使用的元数据视图（如果有）。</span><span class="sxs-lookup"><span data-stu-id="a4841-236">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="a4841-237">包含元数据的导入将声明为延迟导入，其元数据接口作为 `Lazy<T,T>`的第二个类型参数。</span><span class="sxs-lookup"><span data-stu-id="a4841-237">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="a4841-238">下面的类导入前面的部件以及元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-238">The following class imports the previous part with metadata.</span></span>

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

<span data-ttu-id="a4841-239">在许多情况下，你需要将元数据与 `ImportMany` 特性结合，以便分析各个可用的导入并选择仅实例化一个导入，或者筛选集合以匹配特定条件。</span><span class="sxs-lookup"><span data-stu-id="a4841-239">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="a4841-240">下面的类仅实例化具有 `IPlugin` 值“Logger”的 `Name` 对象。</span><span class="sxs-lookup"><span data-stu-id="a4841-240">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a><span data-ttu-id="a4841-241">导入和导出继承</span><span class="sxs-lookup"><span data-stu-id="a4841-241">Import and Export Inheritance</span></span>

<span data-ttu-id="a4841-242">如果某个类继承自部件，则该类也可能会成为部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-242">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="a4841-243">导入始终由子类继承。</span><span class="sxs-lookup"><span data-stu-id="a4841-243">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="a4841-244">因此，部件的子类将始终为部件，并具有与其父类相同的导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-244">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="a4841-245">通过使用 `Export` 特性的声明的导出不会由子类继承。</span><span class="sxs-lookup"><span data-stu-id="a4841-245">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="a4841-246">但是，部件可通过使用 `InheritedExport` 特性继承自身。</span><span class="sxs-lookup"><span data-stu-id="a4841-246">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="a4841-247">部件的子类将继承并提供相同的导出，其中包括协定名称和协定类型。</span><span class="sxs-lookup"><span data-stu-id="a4841-247">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="a4841-248">与 `Export` 特性不同， `InheritedExport` 只能在类级别（而不是成员级别）应用。</span><span class="sxs-lookup"><span data-stu-id="a4841-248">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="a4841-249">因此，成员级别导出永远不能被继承。</span><span class="sxs-lookup"><span data-stu-id="a4841-249">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="a4841-250">下面四个类演示了导入和导出继承的原则。</span><span class="sxs-lookup"><span data-stu-id="a4841-250">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="a4841-251">`NumTwo` 继承自 `NumOne`，因此 `NumTwo` 将导入 `IMyData`。</span><span class="sxs-lookup"><span data-stu-id="a4841-251">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="a4841-252">普通导出不会被继承，因此 `NumTwo` 将不会导出任何内容。</span><span class="sxs-lookup"><span data-stu-id="a4841-252">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="a4841-253">`NumFour` 继承自 `NumThree`。</span><span class="sxs-lookup"><span data-stu-id="a4841-253">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="a4841-254">由于 `NumThree` 使用了 `InheritedExport`，因此 `NumFour` 具有一个协定类型为 `NumThree`的导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-254">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="a4841-255">成员级别导出从不会被继承，因此不会导出 `IMyData` 。</span><span class="sxs-lookup"><span data-stu-id="a4841-255">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

<span data-ttu-id="a4841-256">如果存在与 `InheritedExport` 特性关联的元数据，该元数据也将被继承。</span><span class="sxs-lookup"><span data-stu-id="a4841-256">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="a4841-257">（有关详细信息，请参阅前面的“元数据和元数据视图”一节。）子类无法修改继承的元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-257">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="a4841-258">但是，通过使用相同协定名称和协定类型但使用新元数据重新声明 `InheritedExport` 特性，子类可以将继承的元数据替换为新元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-258">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="a4841-259">下面的类演示此原则。</span><span class="sxs-lookup"><span data-stu-id="a4841-259">The following class demonstrates this principle.</span></span> <span data-ttu-id="a4841-260">`MegaLogger` 部件继承自 `Logger` 并包括 `InheritedExport` 特性。</span><span class="sxs-lookup"><span data-stu-id="a4841-260">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="a4841-261">由于 `MegaLogger` 重新声明名为 Status 的新元数据，因此它不会从 `Logger`中继承 Name 和 Version 元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-261">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

<span data-ttu-id="a4841-262">在重新声明 `InheritedExport` 特性以重写元数据时，请确保协定类型相同。</span><span class="sxs-lookup"><span data-stu-id="a4841-262">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="a4841-263">（在前面的示例中，`IPlugin` 为协定类型。）如果协定类型不同，则第二个特性将创建另一个独立于部件的导出（而不是重写）。</span><span class="sxs-lookup"><span data-stu-id="a4841-263">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="a4841-264">通常，这意味着你必须在重写 `InheritedExport` 特性时显式指定协定类型，如前面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a4841-264">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="a4841-265">由于无法直接实例化接口，因此通常无法用 `Export` 或 `Import` 特性来修饰接口。</span><span class="sxs-lookup"><span data-stu-id="a4841-265">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="a4841-266">不过，可以在接口级别用 `InheritedExport` 特性修饰接口，并且任何实现类将随任何关联的元数据一起继承该导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-266">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="a4841-267">但是，接口本身将不可用作部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-267">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="a4841-268">自定义导出特性</span><span class="sxs-lookup"><span data-stu-id="a4841-268">Custom Export Attributes</span></span>

<span data-ttu-id="a4841-269">可以对基本导出特性 `Export` 和 `InheritedExport`进行扩展，以包括元数据作为特性属性。</span><span class="sxs-lookup"><span data-stu-id="a4841-269">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="a4841-270">在将类似的元数据应用于多个部件或创建元数据特性的继承树时，此方法十分有用。</span><span class="sxs-lookup"><span data-stu-id="a4841-270">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="a4841-271">自定义特性可以指定协定类型、协定名称或任何其他元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-271">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="a4841-272">为了定义自定义特性，必须使用 `ExportAttribute` 特性来修饰继承自 `InheritedExportAttribute`（或 `MetadataAttribute` ）的类。</span><span class="sxs-lookup"><span data-stu-id="a4841-272">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="a4841-273">下面的类定义一个自定义特性。</span><span class="sxs-lookup"><span data-stu-id="a4841-273">The following class defines a custom attribute.</span></span>

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

<span data-ttu-id="a4841-274">此类定义一个名为 `MyAttribute` 的自定义特性，具有协定类型 `IMyAddin` 和某些名为 `MyMetadata`的元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-274">This class defines a custom attribute named `MyAttribute` with contract type `IMyAddin` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="a4841-275">用 `MetadataAttribute` 特性标记的类中的所有属性都将被视为自定义特性中定义的元数据。</span><span class="sxs-lookup"><span data-stu-id="a4841-275">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="a4841-276">下面两个声明等效。</span><span class="sxs-lookup"><span data-stu-id="a4841-276">The following two declarations are equivalent.</span></span>

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

<span data-ttu-id="a4841-277">在第一个声明中，协定类型和元数据是显式定义的。</span><span class="sxs-lookup"><span data-stu-id="a4841-277">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="a4841-278">在第二个声明中，协定类型和元数据在自定义特性中是隐式的。</span><span class="sxs-lookup"><span data-stu-id="a4841-278">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="a4841-279">特别是，在必须将大量的相同元数据（例如，作者或版权信息）应用于多个部件的情况下，使用自定义特性可以节约大量的时间和重复工作。</span><span class="sxs-lookup"><span data-stu-id="a4841-279">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="a4841-280">此外，可以创建自定义特性的继承树来为变体留出余地。</span><span class="sxs-lookup"><span data-stu-id="a4841-280">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="a4841-281">若要在自定义特性中创建可选元数据，你可以使用 `DefaultValue` 特性。</span><span class="sxs-lookup"><span data-stu-id="a4841-281">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="a4841-282">如果此特性应用于自定义特性类中的属性，它将指定修饰的属性是可选的，并且不必由导出程序提供。</span><span class="sxs-lookup"><span data-stu-id="a4841-282">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="a4841-283">如果未提供属性的值，则将为属性分配其属性类型的默认值（通常为 `null`、 `false`或 0。）</span><span class="sxs-lookup"><span data-stu-id="a4841-283">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="a4841-284">创建策略</span><span class="sxs-lookup"><span data-stu-id="a4841-284">Creation Policies</span></span>

<span data-ttu-id="a4841-285">当部件指定执行导入和组合时，组合容器将尝试查找匹配的导出。</span><span class="sxs-lookup"><span data-stu-id="a4841-285">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="a4841-286">如果它将导入与导出成功匹配，则导入成员将设置为导出的对象的实例。</span><span class="sxs-lookup"><span data-stu-id="a4841-286">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="a4841-287">导出部件的 *创建策略*控制此实例来源于何处。</span><span class="sxs-lookup"><span data-stu-id="a4841-287">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="a4841-288">两个可能的创建策略为： *共享* 和 *非共享*。</span><span class="sxs-lookup"><span data-stu-id="a4841-288">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="a4841-289">在具有该协定的部件的容器中，创建策略为“共享”的部件将在每个导入之间共享。</span><span class="sxs-lookup"><span data-stu-id="a4841-289">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="a4841-290">当组合引擎找到匹配项并且必须设置导入属性时，它只有在部件尚不存在时才会实例化部件的新副本；否则它将提供现有副本。</span><span class="sxs-lookup"><span data-stu-id="a4841-290">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="a4841-291">这意味着许多对象可能会引用相同部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-291">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="a4841-292">此类部件不应依赖于可能会从许多地方更改的内部状态。</span><span class="sxs-lookup"><span data-stu-id="a4841-292">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="a4841-293">此策略适用于静态部件、提供服务的部件，以及消耗大量内存或其他资源的部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-293">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="a4841-294">在每次找到部件的其中一个导出的匹配导入时，将会创建创建策略为“非共享”的部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-294">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="a4841-295">因此，将为与部件的其中一个已导出协定匹配的容器中的每个导入实例化一个新副本。</span><span class="sxs-lookup"><span data-stu-id="a4841-295">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="a4841-296">这些副本的内部状态将不会共享。</span><span class="sxs-lookup"><span data-stu-id="a4841-296">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="a4841-297">此策略适用于每个导入需要其自己的内部状态的部件。</span><span class="sxs-lookup"><span data-stu-id="a4841-297">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="a4841-298">导入和导出都可从值 `Shared`、 `NonShared`或 `Any`中指定部件的创建策略。</span><span class="sxs-lookup"><span data-stu-id="a4841-298">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="a4841-299">导入和导出的默认值均为 `Any` 。</span><span class="sxs-lookup"><span data-stu-id="a4841-299">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="a4841-300">指定 `Shared` 或 `NonShared` 的导出将仅与指定相同值或指定 `Any`的导入匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-300">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="a4841-301">同样，指定 `Shared` 或 `NonShared` 的导入将仅与指定相同值或指定 `Any`的导出匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-301">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="a4841-302">就像其协定名称或协定类型不匹配的导入和导出一样，创建策略不兼容的导入和导出也不会被视为匹配。</span><span class="sxs-lookup"><span data-stu-id="a4841-302">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="a4841-303">如果导入和导出均指定 `Any`，或者未指定创建策略并默认为 `Any`，则创建策略将默认为“共享”。</span><span class="sxs-lookup"><span data-stu-id="a4841-303">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="a4841-304">以下示例说明了导入和导出均指定创建策略。</span><span class="sxs-lookup"><span data-stu-id="a4841-304">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="a4841-305">`PartOne` 未指定创建策略，因此默认值为 `Any`。</span><span class="sxs-lookup"><span data-stu-id="a4841-305">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="a4841-306">`PartTwo` 未指定创建策略，因此默认值为 `Any`。</span><span class="sxs-lookup"><span data-stu-id="a4841-306">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="a4841-307">由于导入和导出均默认为 `Any`，因此将共享 `PartOne` 。</span><span class="sxs-lookup"><span data-stu-id="a4841-307">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="a4841-308">`PartThree` 指定 `Shared` 创建策略，因此 `PartTwo` 和 `PartThree` 将共享 `PartOne`的同一副本。</span><span class="sxs-lookup"><span data-stu-id="a4841-308">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="a4841-309">`PartFour` 指定 `NonShared` 创建策略，因此 `PartFour` 在 `PartFive`中将为非共享。</span><span class="sxs-lookup"><span data-stu-id="a4841-309">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="a4841-310">`PartSix` 指定一个 `NonShared` 创建策略。</span><span class="sxs-lookup"><span data-stu-id="a4841-310">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="a4841-311">`PartFive` 和 `PartSix` 将各自收到 `PartFour`的单独副本。</span><span class="sxs-lookup"><span data-stu-id="a4841-311">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="a4841-312">`PartSeven` 指定一个 `Shared` 创建策略。</span><span class="sxs-lookup"><span data-stu-id="a4841-312">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="a4841-313">由于没有创建策略为 `PartFour` 的已导出 `Shared`，因此 `PartSeven` 导入不与任何内容匹配，并且将不会得到满足。</span><span class="sxs-lookup"><span data-stu-id="a4841-313">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="a4841-314">生命周期和释放</span><span class="sxs-lookup"><span data-stu-id="a4841-314">Life Cycle and Disposing</span></span>

<span data-ttu-id="a4841-315">由于部件承载于组合容器中，因此其生命周期可能比普通对象更复杂。</span><span class="sxs-lookup"><span data-stu-id="a4841-315">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="a4841-316">部件可实现两个重要的生命周期相关接口： `IDisposable` 和 `IPartImportsSatisfiedNotification`。</span><span class="sxs-lookup"><span data-stu-id="a4841-316">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="a4841-317">需要在关闭时执行工作的部件和需要释放资源的部件应照常为 .NET Framework 对象实现 `IDisposable`。</span><span class="sxs-lookup"><span data-stu-id="a4841-317">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="a4841-318">但是，由于容器创建并维护对部件的引用，因此只有拥有部件的容器才应对其调用 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-318">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="a4841-319">容器本身实现 `IDisposable`，并且作为 `Dispose` 中其清理的一部分，它将对拥有的所有部件调用 `Dispose` 。</span><span class="sxs-lookup"><span data-stu-id="a4841-319">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="a4841-320">因此，当不再需要组合容器及其拥有的任何部件时，你应始终释放该组合容器。</span><span class="sxs-lookup"><span data-stu-id="a4841-320">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="a4841-321">对于生存期很长的组合容器，创建策略为“非共享”的部件的内存消耗可能会成为问题。</span><span class="sxs-lookup"><span data-stu-id="a4841-321">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="a4841-322">这些非共享部件可以多次创建，并且在容器本身被释放之前将不会得到释放。</span><span class="sxs-lookup"><span data-stu-id="a4841-322">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="a4841-323">为了应对这种情况，容器提供了 `ReleaseExport` 方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-323">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="a4841-324">如果对非共享导出调用此方法，将会从组合容器中移除该导出并将其释放。</span><span class="sxs-lookup"><span data-stu-id="a4841-324">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="a4841-325">仅由移除的导出使用的部件以及树中更深层的诸如此类部件将也会被移除并得到释放。</span><span class="sxs-lookup"><span data-stu-id="a4841-325">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="a4841-326">通过这种方式，不必释放组合窗口本身即可回收资源。</span><span class="sxs-lookup"><span data-stu-id="a4841-326">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="a4841-327">`IPartImportsSatisfiedNotification` 包含一个名为 `OnImportsSatisfied`的方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-327">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="a4841-328">当组合已完成并且部件的导入可供使用时，组合窗口将对实现接口的任何部件调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a4841-328">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="a4841-329">部件是组合引擎创建，用于满足其他部件的导入。</span><span class="sxs-lookup"><span data-stu-id="a4841-329">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="a4841-330">在设置好部件的导入之前，你无法执行任何依赖于部件构造函数中的导入值或对这些值进行操作的初始化，除非已通过使用 `ImportingConstructor` 特性将这些指定为必备。</span><span class="sxs-lookup"><span data-stu-id="a4841-330">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="a4841-331">此方法通常为首选方法，但在某些情况下，构造函数注入可能不可用。</span><span class="sxs-lookup"><span data-stu-id="a4841-331">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="a4841-332">在这些情况下，可以在 `OnImportsSatisfied`中执行初始化，并且部件应实现 `IPartImportsSatisfiedNotification`。</span><span class="sxs-lookup"><span data-stu-id="a4841-332">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4841-333">请参阅</span><span class="sxs-lookup"><span data-stu-id="a4841-333">See also</span></span>

- [<span data-ttu-id="a4841-334">第 9 频道视频：使用 Managed Extensibility Framework 打开应用程序</span><span class="sxs-lookup"><span data-stu-id="a4841-334">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="a4841-335">第 9 频道视频：Managed Extensibility Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="a4841-335">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
