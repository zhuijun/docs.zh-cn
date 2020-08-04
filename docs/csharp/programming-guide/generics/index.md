---
title: 泛型 - C# 编程指南
description: 了解泛型。 泛型类型可以最大程度地提高代码重用、类型安全性和性能，通常用于创建集合类。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: beef9c20e3ac62505bc7a4584b404637935de1dc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299391"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="3e05c-104">泛型（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="3e05c-104">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="3e05c-105">泛型将类型参数的概念引入 .NET，这样就可设计具有以下特征的类和方法：在客户端代码声明并初始化这些类或方法之前，这些类或方法会延迟指定一个或多个类型。</span><span class="sxs-lookup"><span data-stu-id="3e05c-105">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="3e05c-106">例如，通过使用泛型类型参数 `T`，可以编写其他客户端代码能够使用的单个类，而不会产生运行时转换或装箱操作的成本或风险，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e05c-106">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="3e05c-107">泛型类和泛型方法兼具可重用性、类型安全性和效率，这是非泛型类和非泛型方法无法实现的。</span><span class="sxs-lookup"><span data-stu-id="3e05c-107">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="3e05c-108">泛型通常与集合以及作用于集合的方法一起使用。</span><span class="sxs-lookup"><span data-stu-id="3e05c-108">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="3e05c-109"><xref:System.Collections.Generic> 命名空间包含几个基于泛型的集合类。</span><span class="sxs-lookup"><span data-stu-id="3e05c-109">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="3e05c-110">非泛型集合（如 <xref:System.Collections.ArrayList>）不建议使用，并且保留用于兼容性目的。</span><span class="sxs-lookup"><span data-stu-id="3e05c-110">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="3e05c-111">有关详细信息，请参阅 [.NET 中的泛型](../../../standard/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3e05c-111">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="3e05c-112">当然，也可以创建自定义泛型类型和泛型方法，以提供自己的通用解决方案，设计类型安全的高效模式。</span><span class="sxs-lookup"><span data-stu-id="3e05c-112">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="3e05c-113">以下代码示例演示了出于演示目的的简单泛型链接列表类。</span><span class="sxs-lookup"><span data-stu-id="3e05c-113">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="3e05c-114">（大多数情况下，应使用 .NET 提供的 <xref:System.Collections.Generic.List%601> 类，而不是自行创建类。）在通常使用具体类型来指示列表中所存储项的类型的情况下，可使用类型参数 `T`。</span><span class="sxs-lookup"><span data-stu-id="3e05c-114">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="3e05c-115">其使用方法如下：</span><span class="sxs-lookup"><span data-stu-id="3e05c-115">It is used in the following ways:</span></span>

- <span data-ttu-id="3e05c-116">在 `AddHead` 方法中作为方法参数的类型。</span><span class="sxs-lookup"><span data-stu-id="3e05c-116">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="3e05c-117">在 `Node` 嵌套类中作为 `Data` 属性的返回类型。</span><span class="sxs-lookup"><span data-stu-id="3e05c-117">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="3e05c-118">在嵌套类中作为私有成员 `data` 的类型。</span><span class="sxs-lookup"><span data-stu-id="3e05c-118">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="3e05c-119">请注意，`T` 可用于 `Node` 嵌套类。</span><span class="sxs-lookup"><span data-stu-id="3e05c-119">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="3e05c-120">如果使用具体类型实例化 `GenericList<T>`（例如，作为 `GenericList<int>`），则出现的所有 `T` 都将替换为 `int`。</span><span class="sxs-lookup"><span data-stu-id="3e05c-120">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="3e05c-121">以下代码示例演示了客户端代码如何使用泛型 `GenericList<T>` 类来创建整数列表。</span><span class="sxs-lookup"><span data-stu-id="3e05c-121">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="3e05c-122">只需更改类型参数，即可轻松修改以下代码，创建字符串或任何其他自定义类型的列表：</span><span class="sxs-lookup"><span data-stu-id="3e05c-122">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="3e05c-123">泛型概述</span><span class="sxs-lookup"><span data-stu-id="3e05c-123">Generics overview</span></span>

- <span data-ttu-id="3e05c-124">使用泛型类型可以最大限度地重用代码、保护类型安全性以及提高性能。</span><span class="sxs-lookup"><span data-stu-id="3e05c-124">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="3e05c-125">泛型最常见的用途是创建集合类。</span><span class="sxs-lookup"><span data-stu-id="3e05c-125">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="3e05c-126">.NET 类库在 <xref:System.Collections.Generic> 命名空间中包含几个新的泛型集合类。</span><span class="sxs-lookup"><span data-stu-id="3e05c-126">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="3e05c-127">应尽可能使用这些类来代替某些类，如 <xref:System.Collections> 命名空间中的 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="3e05c-127">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="3e05c-128">可以创建自己的泛型接口、泛型类、泛型方法、泛型事件和泛型委托。</span><span class="sxs-lookup"><span data-stu-id="3e05c-128">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="3e05c-129">可以对泛型类进行约束以访问特定数据类型的方法。</span><span class="sxs-lookup"><span data-stu-id="3e05c-129">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="3e05c-130">在泛型数据类型中所用类型的信息可在运行时通过使用反射来获取。</span><span class="sxs-lookup"><span data-stu-id="3e05c-130">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3e05c-131">相关章节</span><span class="sxs-lookup"><span data-stu-id="3e05c-131">Related sections</span></span>

- [<span data-ttu-id="3e05c-132">泛型类型参数</span><span class="sxs-lookup"><span data-stu-id="3e05c-132">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="3e05c-133">类型参数的约束</span><span class="sxs-lookup"><span data-stu-id="3e05c-133">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="3e05c-134">泛型类</span><span class="sxs-lookup"><span data-stu-id="3e05c-134">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="3e05c-135">泛型接口</span><span class="sxs-lookup"><span data-stu-id="3e05c-135">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="3e05c-136">泛型方法</span><span class="sxs-lookup"><span data-stu-id="3e05c-136">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="3e05c-137">泛型委托</span><span class="sxs-lookup"><span data-stu-id="3e05c-137">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="3e05c-138">C++ 模板和 C# 泛型之间的区别</span><span class="sxs-lookup"><span data-stu-id="3e05c-138">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="3e05c-139">泛型和反射</span><span class="sxs-lookup"><span data-stu-id="3e05c-139">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="3e05c-140">运行时中的泛型</span><span class="sxs-lookup"><span data-stu-id="3e05c-140">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="3e05c-141">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="3e05c-141">C# language specification</span></span>

<span data-ttu-id="3e05c-142">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/types.md#constructed-types)。</span><span class="sxs-lookup"><span data-stu-id="3e05c-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e05c-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="3e05c-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3e05c-144">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="3e05c-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3e05c-145">类型</span><span class="sxs-lookup"><span data-stu-id="3e05c-145">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="3e05c-146">.NET 中的泛型</span><span class="sxs-lookup"><span data-stu-id="3e05c-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
