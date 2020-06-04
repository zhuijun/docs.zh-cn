---
title: 重构为纯函数
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 415b088661eca347330f4776901d68ee514d8dad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413474"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="16239-102">重构为纯函数（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="16239-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="16239-103">纯函数转换的一个重要方面是学习如何使用纯函数重构代码。</span><span class="sxs-lookup"><span data-stu-id="16239-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="16239-104">如本节前面所述，纯函数具有两个有用的特性：</span><span class="sxs-lookup"><span data-stu-id="16239-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="16239-105">它没有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="16239-105">It has no side effects.</span></span> <span data-ttu-id="16239-106">函数不会更改函数以外的任何变量或任何类型的数据。</span><span class="sxs-lookup"><span data-stu-id="16239-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="16239-107">它具有一致性。</span><span class="sxs-lookup"><span data-stu-id="16239-107">It is consistent.</span></span> <span data-ttu-id="16239-108">在提供同一组输入数据的情况下，它将始终返回相同的输出值。</span><span class="sxs-lookup"><span data-stu-id="16239-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="16239-109">转换为函数编程的一种方式是重构现有代码以消除不必要的副作用和外部依赖项。</span><span class="sxs-lookup"><span data-stu-id="16239-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="16239-110">这样，您可以创建现有代码的纯函数版本。</span><span class="sxs-lookup"><span data-stu-id="16239-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="16239-111">本主题讨论什么是纯函数，什么不是纯函数。</span><span class="sxs-lookup"><span data-stu-id="16239-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="16239-112">[教程：在 WordprocessingML 文档中操作内容（Visual Basic）](tutorial-manipulating-content-in-a-wordprocessingml-document.md)教程介绍了如何操作 WordprocessingML 文档，并包括两个如何使用纯函数重构的示例。</span><span class="sxs-lookup"><span data-stu-id="16239-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="16239-113">消除副作用和外部依赖项</span><span class="sxs-lookup"><span data-stu-id="16239-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="16239-114">下面的示例对比两个非纯函数和一个纯函数。</span><span class="sxs-lookup"><span data-stu-id="16239-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="16239-115">可更改类成员的非纯函数</span><span class="sxs-lookup"><span data-stu-id="16239-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="16239-116">在下面的代码中，`HyphenatedConcat` 函数不是纯函数，因为它修改了类中的 `aMember` 数据成员：</span><span class="sxs-lookup"><span data-stu-id="16239-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="16239-117">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="16239-117">This code produces the following output:</span></span>

```console
StringOne-StringTwo
```

<span data-ttu-id="16239-118">请注意，无论修改的数据是具有 `public` 还是 `private` 访问，或是 `shared` 成员还是实例成员，都是不相关的。</span><span class="sxs-lookup"><span data-stu-id="16239-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="16239-119">纯函数不会更改函数以外的任何数据。</span><span class="sxs-lookup"><span data-stu-id="16239-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="16239-120">可更改参数的非纯函数</span><span class="sxs-lookup"><span data-stu-id="16239-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="16239-121">此外，此同一个函数的下面版本不是纯函数，因为它修改了其参数 `sb` 的内容。</span><span class="sxs-lookup"><span data-stu-id="16239-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="16239-122">此版本的程序生成的输出与第一个版本相同，因为 `HyphenatedConcat` 函数已通过调用 <xref:System.Text.StringBuilder.Append%2A> 成员函数而更改了其第一个参数的值（状态）。</span><span class="sxs-lookup"><span data-stu-id="16239-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="16239-123">请注意，即使 `HyphenatedConcat` 实际上使用了按值调用参数传递，也会发生此更改。</span><span class="sxs-lookup"><span data-stu-id="16239-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16239-124">对于引用类型，按值传递参数会得到对所传递对象的引用的副本。</span><span class="sxs-lookup"><span data-stu-id="16239-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="16239-125">此副本与原始引用一样，仍与同一个实例数据关联（除非为引用变量分配新对象）。</span><span class="sxs-lookup"><span data-stu-id="16239-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="16239-126">函数修改参数不一定需要按引用调用。</span><span class="sxs-lookup"><span data-stu-id="16239-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="16239-127">纯函数</span><span class="sxs-lookup"><span data-stu-id="16239-127">Pure Function</span></span>

<span data-ttu-id="16239-128">下面版本的程序演示如何将 `HyphenatedConcat` 函数作为纯函数实现。</span><span class="sxs-lookup"><span data-stu-id="16239-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="16239-129">此版本同样生成相同的输出行：`StringOne-StringTwo`。</span><span class="sxs-lookup"><span data-stu-id="16239-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="16239-130">请注意保留串联值，它存储在中间变量 `s2` 中。</span><span class="sxs-lookup"><span data-stu-id="16239-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="16239-131">一种非常实用的方法是编写本地不纯（即声明和修改本地变量）但在全局为纯的函数。</span><span class="sxs-lookup"><span data-stu-id="16239-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="16239-132">这些函数具有许多需要的可组合特性，但舍弃了一些较为繁复的函数编程语法，如在使用简单的循环即可完成同样操作时必须使用递归。</span><span class="sxs-lookup"><span data-stu-id="16239-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="16239-133">标准查询运算符</span><span class="sxs-lookup"><span data-stu-id="16239-133">Standard Query Operators</span></span>

<span data-ttu-id="16239-134">标准查询运算符的重要特性是它们以纯函数的形式实现。</span><span class="sxs-lookup"><span data-stu-id="16239-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="16239-135">有关详细信息，请参阅[标准查询运算符概述（Visual Basic）](standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="16239-135">For more information, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16239-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16239-136">See also</span></span>

- [<span data-ttu-id="16239-137">纯功能转换简介（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="16239-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="16239-138">函数编程与命令式编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="16239-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](functional-programming-vs-imperative-programming.md)
