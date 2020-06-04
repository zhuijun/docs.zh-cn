---
title: 迭代器
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: e638d35aeb86837d91fb14681d300772e3c2375a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410924"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="ace1b-102">迭代器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace1b-102">Iterators (Visual Basic)</span></span>

<span data-ttu-id="ace1b-103">迭代器\*\* 可用于逐步迭代集合，例如列表和数组。</span><span class="sxs-lookup"><span data-stu-id="ace1b-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="ace1b-104">迭代器方法或 `get` 访问器可对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="ace1b-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="ace1b-105">Iterator 方法使用[Yield](../../language-reference/statements/yield-statement.md)语句每次返回一个元素。</span><span class="sxs-lookup"><span data-stu-id="ace1b-105">An iterator method uses the [Yield](../../language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="ace1b-106">到达 `Yield` 语句时，会记住当前在代码中的位置。</span><span class="sxs-lookup"><span data-stu-id="ace1b-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="ace1b-107">下次调用迭代器函数时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="ace1b-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="ace1b-108">使用 For Each ...，从客户端代码使用迭代器[下一](../../language-reference/statements/for-each-next-statement.md)条语句，或使用 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="ace1b-108">You consume an iterator from client code by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="ace1b-109">在以下示例中，`For Each` 循环的首次迭代导致 `SomeNumbers` 迭代器方法继续执行，直至到达第一个 `Yield` 语句。</span><span class="sxs-lookup"><span data-stu-id="ace1b-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="ace1b-110">此迭代返回的值为 3，并保留当前在迭代器方法中的位置。</span><span class="sxs-lookup"><span data-stu-id="ace1b-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="ace1b-111">在循环的下次迭代中，迭代器方法的执行将从其暂停的位置继续，直至到达 `Yield` 语句后才会停止。</span><span class="sxs-lookup"><span data-stu-id="ace1b-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="ace1b-112">此迭代返回的值为 5，并再次保留当前在迭代器方法中的位置。</span><span class="sxs-lookup"><span data-stu-id="ace1b-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="ace1b-113">到达迭代器方法的结尾时，循环便已完成。</span><span class="sxs-lookup"><span data-stu-id="ace1b-113">The loop completes when the end of the iterator method is reached.</span></span>

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

<span data-ttu-id="ace1b-114">迭代器方法或 `get` 访问器的返回类型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="ace1b-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="ace1b-115">您可以使用 `Exit Function` 或 `Return` 语句结束迭代。</span><span class="sxs-lookup"><span data-stu-id="ace1b-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="ace1b-116">Visual Basic 迭代器函数或 `get` 访问器声明包含[迭代器](../../language-reference/modifiers/iterator.md)修饰符。</span><span class="sxs-lookup"><span data-stu-id="ace1b-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="ace1b-117">迭代器是在 Visual Studio 2012 Visual Basic 中引入的。</span><span class="sxs-lookup"><span data-stu-id="ace1b-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="ace1b-118">**在本主题中**</span><span class="sxs-lookup"><span data-stu-id="ace1b-118">**In this topic**</span></span>

- [<span data-ttu-id="ace1b-119">简单的迭代器</span><span class="sxs-lookup"><span data-stu-id="ace1b-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="ace1b-120">创建集合类</span><span class="sxs-lookup"><span data-stu-id="ace1b-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="ace1b-121">Try 块</span><span class="sxs-lookup"><span data-stu-id="ace1b-121">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="ace1b-122">匿名方法</span><span class="sxs-lookup"><span data-stu-id="ace1b-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="ace1b-123">对泛型列表使用迭代器</span><span class="sxs-lookup"><span data-stu-id="ace1b-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="ace1b-124">语法信息</span><span class="sxs-lookup"><span data-stu-id="ace1b-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="ace1b-125">技术实现</span><span class="sxs-lookup"><span data-stu-id="ace1b-125">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="ace1b-126">迭代器的使用</span><span class="sxs-lookup"><span data-stu-id="ace1b-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="ace1b-127">对于除了简单迭代器示例之外的主题中的所有示例[Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) ，都包含用于 `System.Collections` 和 `System.Collections.Generic` 命名空间的 Imports 语句。</span><span class="sxs-lookup"><span data-stu-id="ace1b-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a><span data-ttu-id="ace1b-128">简单迭代器</span><span class="sxs-lookup"><span data-stu-id="ace1b-128">Simple Iterator</span></span>

<span data-ttu-id="ace1b-129">下面的示例包含一个 `Yield` 位于[For .。。下一个](../../language-reference/statements/for-next-statement.md)循环。</span><span class="sxs-lookup"><span data-stu-id="ace1b-129">The following example has a single `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="ace1b-130">在 `Main` 中，`For Each` 语句体的每次迭代都会创建一个对迭代器函数的调用，并将继续到下一个 `Yield` 语句。</span><span class="sxs-lookup"><span data-stu-id="ace1b-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a><span data-ttu-id="ace1b-131">创建集合类</span><span class="sxs-lookup"><span data-stu-id="ace1b-131">Creating a Collection Class</span></span>

<span data-ttu-id="ace1b-132">在以下示例中，`DaysOfTheWeek` 类实现 <xref:System.Collections.IEnumerable> 接口，此操作需要 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="ace1b-133">编译器隐式调用 `GetEnumerator` 方法，此方法返回 <xref:System.Collections.IEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="ace1b-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="ace1b-134">`GetEnumerator`方法通过使用语句每次返回一个字符串 `Yield` ，并且 `Iterator` 修饰符在函数声明中。</span><span class="sxs-lookup"><span data-stu-id="ace1b-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

<span data-ttu-id="ace1b-135">下例创建了一个包含动物集合的 `Zoo` 类。</span><span class="sxs-lookup"><span data-stu-id="ace1b-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="ace1b-136">引用类实例 (`theZoo`) 的 `For Each` 语句隐式调用 `GetEnumerator` 方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="ace1b-137">引用 `Birds` 和 `Mammals` 属性的 `For Each` 语句使用 `AnimalsForType` 命名迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a><span data-ttu-id="ace1b-138">Try 块</span><span class="sxs-lookup"><span data-stu-id="ace1b-138">Try Blocks</span></span>

<span data-ttu-id="ace1b-139">Visual Basic 允许 `Yield` 在 `Try` [Try 块 .。。Catch .。。Finally 语句](../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ace1b-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="ace1b-140">`Try`带有语句的块 `Yield` 可以有 `Catch` 块，并且可以有 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="ace1b-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="ace1b-141">下面的示例 `Try` `Catch` `Finally` 在迭代器函数中包含、和块。</span><span class="sxs-lookup"><span data-stu-id="ace1b-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="ace1b-142">迭代 `Finally` 器函数中的块在 `For Each` 迭代完成之前执行。</span><span class="sxs-lookup"><span data-stu-id="ace1b-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

<span data-ttu-id="ace1b-143">`Yield`语句不能位于 `Catch` 块或 `Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="ace1b-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="ace1b-144">如果 `For Each` 主体（而不是迭代器方法）引发异常，则 `Catch` 不会执行迭代器函数中的块，但 `Finally` 会执行迭代器函数中的块。</span><span class="sxs-lookup"><span data-stu-id="ace1b-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="ace1b-145">`Catch`Iterator 函数内的块仅捕获 iterator 函数内发生的异常。</span><span class="sxs-lookup"><span data-stu-id="ace1b-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a><span data-ttu-id="ace1b-146">匿名方法</span><span class="sxs-lookup"><span data-stu-id="ace1b-146">Anonymous Methods</span></span>

<span data-ttu-id="ace1b-147">在 Visual Basic 中，匿名函数可以是迭代器函数。</span><span class="sxs-lookup"><span data-stu-id="ace1b-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="ace1b-148">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="ace1b-148">The following example illustrates this.</span></span>

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

<span data-ttu-id="ace1b-149">下面的示例具有一个用于验证参数的非迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="ace1b-150">方法返回描述集合元素的匿名迭代器的结果。</span><span class="sxs-lookup"><span data-stu-id="ace1b-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

<span data-ttu-id="ace1b-151">如果验证是在迭代器函数中，则在开始第一次迭代的开始之前，将无法执行验证 `For Each` 。</span><span class="sxs-lookup"><span data-stu-id="ace1b-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a><span data-ttu-id="ace1b-152">对泛型列表使用迭代器</span><span class="sxs-lookup"><span data-stu-id="ace1b-152">Using Iterators with a Generic List</span></span>

<span data-ttu-id="ace1b-153">在以下示例中，`Stack(Of T)` 泛型类实现 <xref:System.Collections.Generic.IEnumerable%601> 泛型接口。</span><span class="sxs-lookup"><span data-stu-id="ace1b-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="ace1b-154">`Push` 方法将值分配给类型为 `T` 的数组。</span><span class="sxs-lookup"><span data-stu-id="ace1b-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="ace1b-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法通过使用 `Yield` 语句返回数组值。</span><span class="sxs-lookup"><span data-stu-id="ace1b-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="ace1b-156">除了泛型 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法，还必须实现非泛型 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="ace1b-157">这是因为从 <xref:System.Collections.IEnumerable> 继承了 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="ace1b-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="ace1b-158">非泛型实现遵从泛型实现的规则。</span><span class="sxs-lookup"><span data-stu-id="ace1b-158">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="ace1b-159">本示例使用命名迭代器来支持通过各种方法循环访问同一数据集合。</span><span class="sxs-lookup"><span data-stu-id="ace1b-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="ace1b-160">这些命名迭代器为 `TopToBottom` 和 `BottomToTop` 属性，以及 `TopN` 方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="ace1b-161">`BottomToTop`属性声明包含 `Iterator` 关键字。</span><span class="sxs-lookup"><span data-stu-id="ace1b-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a><span data-ttu-id="ace1b-162">语法信息</span><span class="sxs-lookup"><span data-stu-id="ace1b-162">Syntax Information</span></span>

<span data-ttu-id="ace1b-163">迭代器可用作一种方法，或一个 `get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="ace1b-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="ace1b-164">不能在事件、实例构造函数、静态构造函数或静态析构函数中使用迭代器。</span><span class="sxs-lookup"><span data-stu-id="ace1b-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="ace1b-165">`Yield` 语句中必须存在从表达式类型到迭代器返回类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="ace1b-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="ace1b-166">在 Visual Basic 中，迭代器方法不能具有任何 `ByRef` 参数。</span><span class="sxs-lookup"><span data-stu-id="ace1b-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="ace1b-167">在 Visual Basic 中，"Yield" 不是保留字，仅在 `Iterator` 方法或访问器中使用时具有特殊意义 `get` 。</span><span class="sxs-lookup"><span data-stu-id="ace1b-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a><span data-ttu-id="ace1b-168">技术实现</span><span class="sxs-lookup"><span data-stu-id="ace1b-168">Technical Implementation</span></span>

<span data-ttu-id="ace1b-169">即使将迭代器编写成方法，编译器也会将其转换为实际上是状态机的嵌套类。</span><span class="sxs-lookup"><span data-stu-id="ace1b-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="ace1b-170">只要客户端代码中的 `For Each...Next` 循环继续，此类就会跟踪迭代器的位置。</span><span class="sxs-lookup"><span data-stu-id="ace1b-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="ace1b-171">若要查看编译器执行的操作，可使用 Ildasm.exe 工具查看为迭代器方法生成的 Microsoft 中间语言代码。</span><span class="sxs-lookup"><span data-stu-id="ace1b-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="ace1b-172">为[类](../../language-reference/statements/class-statement.md)或[结构](../../language-reference/statements/structure-statement.md)创建迭代器时，不必实现整个 <xref:System.Collections.IEnumerator> 接口。</span><span class="sxs-lookup"><span data-stu-id="ace1b-172">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="ace1b-173">编译器检测到迭代器时，会自动生成 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 接口的 `Current`、`MoveNext` 和 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="ace1b-174">在 `For Each…Next` 循环（或对 `IEnumerator.MoveNext` 的直接调用）的每次后续迭代中，下一个迭代器代码体都会在上一个 `Yield` 语句之后恢复。</span><span class="sxs-lookup"><span data-stu-id="ace1b-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="ace1b-175">然后，它将继续执行下一 `Yield` 条语句，直到到达迭代器主体的末尾，或者 `Exit Function` `Return` 遇到或语句为止。</span><span class="sxs-lookup"><span data-stu-id="ace1b-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="ace1b-176">迭代器不支持 <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ace1b-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ace1b-177">若要从头开始重新迭代，必须获取新的迭代器。</span><span class="sxs-lookup"><span data-stu-id="ace1b-177">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="ace1b-178">有关其他信息，请参阅[Visual Basic 语言规范](../../reference/language-specification/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ace1b-178">For additional information, see the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a><span data-ttu-id="ace1b-179">迭代器的使用</span><span class="sxs-lookup"><span data-stu-id="ace1b-179">Use of Iterators</span></span>

<span data-ttu-id="ace1b-180">需要使用复杂代码填充列表序列时，使用迭代器可保持 `For Each` 循环的简单性。</span><span class="sxs-lookup"><span data-stu-id="ace1b-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="ace1b-181">需执行以下操作时，这可能很有用：</span><span class="sxs-lookup"><span data-stu-id="ace1b-181">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="ace1b-182">在第一次 `For Each` 循环迭代之后，修改列表序列。</span><span class="sxs-lookup"><span data-stu-id="ace1b-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="ace1b-183">避免在 `For Each` 循环的第一次迭代之前完全加载大型列表。</span><span class="sxs-lookup"><span data-stu-id="ace1b-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="ace1b-184">一个示例是用于加载一批表格行的分页提取。</span><span class="sxs-lookup"><span data-stu-id="ace1b-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="ace1b-185">另一个示例关于 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，该方法在 .NET Framework 中实现迭代器。</span><span class="sxs-lookup"><span data-stu-id="ace1b-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="ace1b-186">在迭代器中封装生成列表。</span><span class="sxs-lookup"><span data-stu-id="ace1b-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="ace1b-187">使用迭代器方法，可生成该列表，然后在循环中产出每个结果。</span><span class="sxs-lookup"><span data-stu-id="ace1b-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="ace1b-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ace1b-188">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="ace1b-189">For Each...Next 语句</span><span class="sxs-lookup"><span data-stu-id="ace1b-189">For Each...Next Statement</span></span>](../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="ace1b-190">Yield 语句</span><span class="sxs-lookup"><span data-stu-id="ace1b-190">Yield Statement</span></span>](../../language-reference/statements/yield-statement.md)
- [<span data-ttu-id="ace1b-191">迭代器</span><span class="sxs-lookup"><span data-stu-id="ace1b-191">Iterator</span></span>](../../language-reference/modifiers/iterator.md)
