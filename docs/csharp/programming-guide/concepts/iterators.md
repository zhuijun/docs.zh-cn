---
title: 循环访问 C# 中的集合
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 15b77fd11c0ff606119425ec7aae8e7127315e82
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240689"
---
# <a name="iterators-c"></a><span data-ttu-id="92236-102">迭代器 (C#)</span><span class="sxs-lookup"><span data-stu-id="92236-102">Iterators (C#)</span></span>

<span data-ttu-id="92236-103">迭代器可用于逐步迭代集合，例如列表和数组。</span><span class="sxs-lookup"><span data-stu-id="92236-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="92236-104">迭代器方法或 `get` 访问器可对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="92236-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="92236-105">迭代器方法使用 [yield return](../../language-reference/keywords/yield.md) 语句返回元素，每次返回一个。</span><span class="sxs-lookup"><span data-stu-id="92236-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="92236-106">到达 `yield return` 语句时，会记住当前在代码中的位置。</span><span class="sxs-lookup"><span data-stu-id="92236-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="92236-107">下次调用迭代器函数时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="92236-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="92236-108">通过 [foreach](../../language-reference/keywords/foreach-in.md) 语句或 LINQ 查询从客户端代码中使用迭代器。</span><span class="sxs-lookup"><span data-stu-id="92236-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="92236-109">在以下示例中，`foreach` 循环的首次迭代导致 `SomeNumbers` 迭代器方法继续执行，直至到达第一个 `yield return` 语句。</span><span class="sxs-lookup"><span data-stu-id="92236-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="92236-110">此迭代返回的值为 3，并保留当前在迭代器方法中的位置。</span><span class="sxs-lookup"><span data-stu-id="92236-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="92236-111">在循环的下次迭代中，迭代器方法的执行将从其暂停的位置继续，直至到达 `yield return` 语句后才会停止。</span><span class="sxs-lookup"><span data-stu-id="92236-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="92236-112">此迭代返回的值为 5，并再次保留当前在迭代器方法中的位置。</span><span class="sxs-lookup"><span data-stu-id="92236-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="92236-113">到达迭代器方法的结尾时，循环便已完成。</span><span class="sxs-lookup"><span data-stu-id="92236-113">The loop completes when the end of the iterator method is reached.</span></span>

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

<span data-ttu-id="92236-114">迭代器方法或 `get` 访问器的返回类型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="92236-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="92236-115">可以使用 `yield break` 语句来终止迭代。</span><span class="sxs-lookup"><span data-stu-id="92236-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="92236-116">对于本主题中除简单迭代器示例以外的所有示例，请为 `System.Collections` 和 `System.Collections.Generic` 命名空间加入 [using](../../language-reference/keywords/using-directive.md) 指令。</span><span class="sxs-lookup"><span data-stu-id="92236-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="92236-117">简单的迭代器</span><span class="sxs-lookup"><span data-stu-id="92236-117">Simple Iterator</span></span>

<span data-ttu-id="92236-118">下例包含一个位于 [for](../../language-reference/keywords/for.md) 循环内的 `yield return` 语句。</span><span class="sxs-lookup"><span data-stu-id="92236-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="92236-119">在 `Main` 中，`foreach` 语句体的每次迭代都会创建一个对迭代器函数的调用，并将继续到下一个 `yield return` 语句。</span><span class="sxs-lookup"><span data-stu-id="92236-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a><span data-ttu-id="92236-120">创建集合类</span><span class="sxs-lookup"><span data-stu-id="92236-120">Creating a Collection Class</span></span>

<span data-ttu-id="92236-121">在以下示例中，`DaysOfTheWeek` 类实现 <xref:System.Collections.IEnumerable> 接口，此操作需要 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="92236-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="92236-122">编译器隐式调用 `GetEnumerator` 方法，此方法返回 <xref:System.Collections.IEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="92236-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="92236-123">`GetEnumerator` 方法通过使用 `yield return` 语句每次返回 1 个字符串。</span><span class="sxs-lookup"><span data-stu-id="92236-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

<span data-ttu-id="92236-124">下例创建了一个包含动物集合的 `Zoo` 类。</span><span class="sxs-lookup"><span data-stu-id="92236-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="92236-125">引用类实例 (`theZoo`) 的 `foreach` 语句隐式调用 `GetEnumerator` 方法。</span><span class="sxs-lookup"><span data-stu-id="92236-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="92236-126">引用 `Birds` 和 `Mammals` 属性的 `foreach` 语句使用 `AnimalsForType` 命名迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="92236-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="92236-127">对泛型列表使用迭代器</span><span class="sxs-lookup"><span data-stu-id="92236-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="92236-128">在以下示例中，<xref:System.Collections.Generic.Stack%601> 泛型类实现 <xref:System.Collections.Generic.IEnumerable%601> 泛型接口。</span><span class="sxs-lookup"><span data-stu-id="92236-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="92236-129"><xref:System.Collections.Generic.Stack%601.Push%2A> 方法将值分配给类型为 `T` 的数组。</span><span class="sxs-lookup"><span data-stu-id="92236-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="92236-130"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法通过使用 `yield return` 语句返回数组值。</span><span class="sxs-lookup"><span data-stu-id="92236-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="92236-131">除了泛型 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法，还必须实现非泛型 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="92236-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="92236-132">这是因为从 <xref:System.Collections.IEnumerable> 继承了 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="92236-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="92236-133">非泛型实现遵从泛型实现的规则。</span><span class="sxs-lookup"><span data-stu-id="92236-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="92236-134">本示例使用命名迭代器来支持通过各种方法循环访问同一数据集合。</span><span class="sxs-lookup"><span data-stu-id="92236-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="92236-135">这些命名迭代器为 `TopToBottom` 和 `BottomToTop` 属性，以及 `TopN` 方法。</span><span class="sxs-lookup"><span data-stu-id="92236-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="92236-136">`BottomToTop` 属性在 `get` 访问器中使用迭代器。</span><span class="sxs-lookup"><span data-stu-id="92236-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a><span data-ttu-id="92236-137">语法信息</span><span class="sxs-lookup"><span data-stu-id="92236-137">Syntax Information</span></span>

<span data-ttu-id="92236-138">迭代器可用作一种方法，或一个 `get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="92236-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="92236-139">不能在事件、实例构造函数、静态构造函数或静态终结器中使用迭代器。</span><span class="sxs-lookup"><span data-stu-id="92236-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="92236-140">必须存在从 `yield return` 语句中的表达式类型到迭代器返回的 `IEnumerable<T>` 类型参数的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="92236-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="92236-141">在 C# 中，迭代器方法不能有任何 `in`、`ref` 或 `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="92236-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="92236-142">在 C# 中，`yield` 不是保留字，只有在 `return` 或 `break` 关键字之前使用时才有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="92236-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="92236-143">技术实现</span><span class="sxs-lookup"><span data-stu-id="92236-143">Technical Implementation</span></span>

<span data-ttu-id="92236-144">即使将迭代器编写成方法，编译器也会将其转换为实际上是状态机的嵌套类。</span><span class="sxs-lookup"><span data-stu-id="92236-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="92236-145">只要客户端代码中的 `foreach` 循环继续，此类就会跟踪迭代器的位置。</span><span class="sxs-lookup"><span data-stu-id="92236-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="92236-146">若要查看编译器执行的操作，可使用 Ildasm.exe 工具查看为迭代器方法生成的 Microsoft 中间语言代码。</span><span class="sxs-lookup"><span data-stu-id="92236-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="92236-147">为[类](../../language-reference/keywords/class.md)或[结构](../../language-reference/builtin-types/struct.md)创建迭代器时，不必实现整个 <xref:System.Collections.IEnumerator> 接口。</span><span class="sxs-lookup"><span data-stu-id="92236-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="92236-148">编译器检测到迭代器时，会自动生成 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 接口的 `Current`、`MoveNext` 和 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="92236-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="92236-149">在 `foreach` 循环（或对 `IEnumerator.MoveNext` 的直接调用）的每次后续迭代中，下一个迭代器代码体都会在上一个 `yield return` 语句之后恢复。</span><span class="sxs-lookup"><span data-stu-id="92236-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="92236-150">然后继续下一个 `yield return` 语句，直至到达迭代器体的结尾，或直至遇到 `yield break` 语句。</span><span class="sxs-lookup"><span data-stu-id="92236-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="92236-151">迭代器不支持 <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="92236-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="92236-152">若要从头开始重新迭代，必须获取新的迭代器。</span><span class="sxs-lookup"><span data-stu-id="92236-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="92236-153">在迭代器方法返回的迭代器上调用 <xref:System.Collections.IEnumerator.Reset%2A> 会引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="92236-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="92236-154">有关其他信息，请参阅 [C# 语言规范](~/_csharplang/spec/classes.md#iterators)。</span><span class="sxs-lookup"><span data-stu-id="92236-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="92236-155">迭代器的使用</span><span class="sxs-lookup"><span data-stu-id="92236-155">Use of Iterators</span></span>

<span data-ttu-id="92236-156">需要使用复杂代码填充列表序列时，使用迭代器可保持 `foreach` 循环的简单性。</span><span class="sxs-lookup"><span data-stu-id="92236-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="92236-157">需执行以下操作时，这可能很有用：</span><span class="sxs-lookup"><span data-stu-id="92236-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="92236-158">在第一次 `foreach` 循环迭代之后，修改列表序列。</span><span class="sxs-lookup"><span data-stu-id="92236-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="92236-159">避免在 `foreach` 循环的第一次迭代之前完全加载大型列表。</span><span class="sxs-lookup"><span data-stu-id="92236-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="92236-160">一个示例是用于加载一批表格行的分页提取。</span><span class="sxs-lookup"><span data-stu-id="92236-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="92236-161">另一个示例是 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，该方法在 .NET 中实现迭代器。</span><span class="sxs-lookup"><span data-stu-id="92236-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators in .NET.</span></span>

- <span data-ttu-id="92236-162">在迭代器中封装生成列表。</span><span class="sxs-lookup"><span data-stu-id="92236-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="92236-163">使用迭代器方法，可生成该列表，然后在循环中产出每个结果。</span><span class="sxs-lookup"><span data-stu-id="92236-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="92236-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="92236-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="92236-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="92236-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="92236-166">yield</span><span class="sxs-lookup"><span data-stu-id="92236-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="92236-167">对数组使用 foreach</span><span class="sxs-lookup"><span data-stu-id="92236-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="92236-168">泛型</span><span class="sxs-lookup"><span data-stu-id="92236-168">Generics</span></span>](../generics/index.md)
