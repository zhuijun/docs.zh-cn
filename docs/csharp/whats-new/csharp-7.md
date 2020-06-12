---
title: C# 7.0 中的新增功能 - C# 指南
description: 大致了解 C# 语言的版本 7.0 中的新增功能。
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: e78d680e19709bf3dd854531d5d9f6b7d6464f49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392244"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 中的新增功能

C# 7.0 向 C# 语言添加了许多新功能：

- [`out` 变量](#out-variables)
  - 可以将 `out` 值内联作为参数声明到使用这些参数的方法中。
- [元组](#tuples)
  - 可以创建包含多个公共字段的轻量级未命名类型。 编译器和 IDE 工具可理解这些类型的语义。
- [弃元](#discards)
  - 弃元是指在不关心所赋予的值时，赋值中使用的临时只写变量。 在对元组和用户定义类型进行解构，以及在使用 `out` 参数调用方法时，它们的作用最大。
- [模式匹配](#pattern-matching)
  - 可以基于任意类型和这些类型的成员的值创建分支逻辑。
- [`ref` 局部变量和返回结果](#ref-locals-and-returns)
  - 方法局部参数和返回值可以是对其他存储的引用。
- [本地函数](#local-functions)
  - 可以将函数嵌套在其他函数内，以限制其范围和可见性。
- [更多的 expression-bodied 成员](#more-expression-bodied-members)
  - 可使用表达式创作的成员列表有所增长。
- [`throw` 表达式](#throw-expressions)
  - 可以在之前因为 `throw` 是语句而不被允许的代码构造中引发异常。
- [通用的异步返回类型](#generalized-async-return-types)
  - 使用 `async` 修饰符声明的方法可以返回除 `Task` 和 `Task<T>` 以外的其他类型。
- [数字文本语法改进](#numeric-literal-syntax-improvements)
  - 新令牌可提高数值常量的可读性。

本文的其余部分概述了每个功能。 你将了解每项功能背后的原理。 将了解语法。 可以使用 `dotnet try` 全局工具在环境中浏览这些功能：

1. 安装 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全局工具。
1. 克隆 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存储库。
1. 将当前目录设置为 try-samples 存储库的 csharp7 子目录 。
1. 运行 `dotnet try`。

## <a name="out-variables"></a>`out` 变量

支持 `out` 参数的现有语法已在此版本中得到改进。 现在可以在方法调用的参数列表中声明 `out` 变量，而不是编写单独的声明语句：

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

为清晰明了，可能需指定 `out` 变量的类型，如上所示。 但是，该语言支持使用隐式类型的局部变量：

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- 代码更易于阅读。
  - 在使用 out 变量的地方声明 out 变量，而不是在上面的另一行。
- 无需分配初始值。
  - 通过在方法调用中使用 `out` 变量的位置声明该变量，使得在分配它之前不可能意外使用它。

## <a name="tuples"></a>元组

C# 为用于说明设计意图的类和结构提供了丰富的语法。 但是，这种丰富的语法有时会需要额外的工作，但益处却很少。 你可能经常编写需要包含多个数据元素的简单结构的方法。 为了支持这些方案，已将元组添加到了 C#。 元组是包含多个字段以表示数据成员的轻量级数据结构。
这些字段没有经过验证，并且你无法定义自己的方法

> [!NOTE]
> 低于 C# 7.0 的版本中也提供元组，但它们效率低下且不具有语言支持。
> 这意味着元组元素只能作为 `Item1` 和 `Item2` 等引用。 C# 7.0 引入了对元组的语言支持，可利用更有效的新元组类型向元组字段赋予语义名称。

可以通过为每个成员赋值来创建元组，并可选择为元组的每个成员提供语义名称：

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` 元组包含称为 `Alpha` 和 `Beta` 的字段。 这些名称仅存在于编译时且不保留，例如在运行时使用反射来检查元组时。

在进行元组赋值时，还可以指定赋值右侧的字段的名称：

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

在某些时候，你可能想要解包从方法返回的元组的成员。  可通过为元组中的每个值声明单独的变量来实现此目的。 这种解包操作称为解构元组：

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

还可以为 .NET 中的任何类型提供类似的析构。 编写 `Deconstruct` 方法，用作类的成员。 `Deconstruct` 方法为你要提取的每个属性提供一组 `out` 参数。 考虑提供析构函数方法的此 `Point` 类，该方法提取 `X` 和 `Y` 坐标：

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

可以通过向元组分配 `Point` 来提取各个字段：

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

可在[元组相关文章](../tuples.md)中深入了解有关元组的详细信息。

## <a name="discards"></a>弃元

通常，在进行元组解构或使用 `out` 参数调用方法时，必须定义一个其值无关紧要且你不打算使用的变量。 为处理此情况，C# 增添了对弃元的支持。 弃元是一个名为 `_`（下划线字符）的只写变量，可向单个变量赋予要放弃的所有值。 弃元类似于未赋值的变量；不可在代码中使用弃元（赋值语句除外）。

在以下方案中支持弃元：

- 在对元组或用户定义的类型进行解构时。
- 在使用 [out](../language-reference/keywords/out-parameter-modifier.md) 参数调用方法时。
- 在使用 [is](../language-reference/keywords/is.md) 和 [switch](../language-reference/keywords/switch.md) 语句匹配操作的模式中。
- 在要将某赋值的值显式标识为弃元时用作独立标识符。

以下示例定义了 `QueryCityDataForYears` 方法，它返回一个包含两个不同年份的城市数据的六元组。 本例中，方法调用仅与此方法返回的两个人口值相关，因此在进行元组解构时，将元组中的其余值视为弃元。

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

有关详细信息，请参阅[弃元](../discards.md)。

## <a name="pattern-matching"></a>模式匹配

模式匹配是一种可让你对除对象类型以外的属性实现方法分派的功能。 你可能已经熟悉基于对象类型的方法分派。 在面向对象的编程中，虚拟和重写方法提供语言语法来实现基于对象类型的方法分派。 基类和派生类提供不同的实现。
模式匹配表达式扩展了这一概念，以便你可以通过继承层次结构为不相关的类型和数据元素轻松实现类似的分派模式。

模式匹配支持 `is` 表达式和 `switch` 表达式。 每个表达式都允许检查对象及其属性以确定该对象是否满足所寻求的模式。 使用 `when` 关键字来指定模式的其他规则。

`is` 模式表达式扩展了常用 [`is` 运算符](../language-reference/keywords/is.md#pattern-matching-with-is)以查询关于其类型的对象，并在一条指令分配结果。 以下代码检查变量是否为 `int`，如果是，则将其添加到当前总和：

```csharp
if (input is int count)
    sum += count;
```

前面的小型示例演示了 `is` 表达式的增强功能。 可以针对值类型和引用类型进行测试，并且可以将成功结果分配给类型正确的新变量。

switch 匹配表达式具有常见的语法，它基于已包含在 C# 语言中的 `switch` 语句。 更新后的 switch 语句有几个新构造：

- `switch` 表达式的控制类型不再局限于整数类型、`Enum` 类型、`string` 或与这些类型之一对应的可为 null 的类型。 可能会使用任何类型。
- 可以在每个 `case` 标签中测试 `switch` 表达式的类型。 与 `is` 表达式一样，可以为该类型指定一个新变量。
- 可以添加 `when` 子句以进一步测试该变量的条件。
- `case` 标签的顺序现在很重要。 执行匹配的第一个分支；其他将跳过。

以下代码演示了这些新功能：

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` 是常见的常量模式。
- `case IEnumerable<int> childSequence:` 是一种类型模式。
- `case int n when n > 0:` 是具有附加 `when` 条件的类型模式。
- `case null:` 是 null 模式。
- `default:` 是常见的默认事例。

可以在 [C# 中的模式匹配](../pattern-matching.md)中了解有关模式匹配的更多信息。

## <a name="ref-locals-and-returns"></a>Ref 局部变量和返回结果

此功能允许使用并返回对变量的引用的算法，这些变量在其他位置定义。 一个示例是使用大型矩阵并查找具有某些特征的单个位置。 下面的方法在矩阵中向该存储返回“引用”：

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

可以将返回值声明为 `ref` 并在矩阵中修改该值，如以下代码所示：

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# 语言还有多个规则，可保护你免于误用 `ref` 局部变量和返回结果：

- 必须将 `ref` 关键字添加到方法签名和方法中的所有 `return` 语句中。
  - 这清楚地表明，该方法在整个方法中通过引用返回。
- 可以将 `ref return` 分配给值变量或 `ref` 变量。
  - 调用方控制是否复制返回值。 在分配返回值时省略 `ref` 修饰符表示调用方需要该值的副本，而不是对存储的引用。
- 不可向 `ref` 本地变量赋予标准方法返回值。
  - 因为那将禁止类似 `ref int i = sequence.Count();` 这样的语句
- 不能将 `ref` 返回给其生存期不超出方法执行的变量。
  - 这意味着不可返回对本地变量或对类似作用域变量的引用。
- `ref` 局部变量和返回结果不可用于异步方法。
  - 编译器无法知道异步方法返回时，引用的变量是否已设置为其最终值。

添加 ref 局部变量和 ref 返回结果可通过避免复制值或多次执行取消引用操作，允许更为高效的算法。

向返回值添加 `ref` 是[源兼容的更改](version-update-considerations.md#source-compatible-changes)。 现有代码会进行编译，但在分配时复制 ref 返回值。 调用方必须将存储的返回值更新为 `ref` 局部变量，从而将返回值存储为引用。

有关详细信息，请参阅 [ref 关键字](../language-reference/keywords/ref.md)一文。

## <a name="local-functions"></a>本地函数

许多类的设计都包括仅从一个位置调用的方法。 这些额外的私有方法使每个方法保持小且集中。 本地函数使你能够在另一个方法的上下文内声明方法。 本地函数使得类的阅读者更容易看到本地方法仅从声明它的上下文中调用。

对于本地函数有两个常见的用例：公共迭代器方法和公共异步方法。 这两种类型的方法都生成报告错误的时间晚于程序员期望时间的代码。 在迭代器方法中，只有在调用枚举返回的序列的代码时才会观察到任何异常。 在异步方法中，只有当返回的 `Task` 处于等待状态时才会观察到任何异常。 以下示例演示如何使用本地函数将参数验证与迭代器实现分离：

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

可以对 `async` 方法采用相同的技术，以确保在异步工作开始之前引发由参数验证引起的异常：

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> 本地函数支持的某些设计也可以使用 lambda 表达式来完成。 有关详细信息，请参阅[本地函数与 Lambda 表达式](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)。

## <a name="more-expression-bodied-members"></a>更多的 expression-bodied 成员

C# 6 为成员函数和只读属性引入了 [expression-bodied 成员](csharp-6.md#expression-bodied-function-members)。 C# 7.0 扩展了可作为表达式实现的允许的成员。 在 C# 7.0 中，你可以在属性和索引器上实现构造函数、终结器以及 `get` 和 `set` 访问器。 以下代码演示了每种情况的示例：

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> 本示例不需要终结器，但显示它是为了演示语法。 不应在类中实现终结器，除非有必要发布非托管资源。 还应考虑使用 <xref:System.Runtime.InteropServices.SafeHandle> 类，而不是直接管理非托管资源。

这些 expression-bodied 成员的新位置代表了 C# 语言的一个重要里程碑：这些功能由致力于开发开放源代码 [Roslyn](https://github.com/dotnet/Roslyn) 项目的社区成员实现。

将方法更改为 expression bodied 成员是[二进制兼容的更改](version-update-considerations.md#binary-compatible-changes)。

## <a name="throw-expressions"></a>引发表达式

在 C# 中，`throw` 始终是一个语句。 因为 `throw` 是一个语句而非表达式，所以在某些 C# 构造中无法使用它。 它们包括条件表达式、null 合并表达式和一些 lambda 表达式。 添加 expression-bodied 成员将添加更多位置，在这些位置中，`throw` 表达式会很有用。 为了可以编写这些构造，C# 7.0 引入了 [*throw 表达式*](../language-reference/keywords/throw.md#the-throw-expression)。

这使得编写更多基于表达式的代码变得更容易。 不需要其他语句来进行错误检查。

## <a name="generalized-async-return-types"></a>通用的异步返回类型

从异步方法返回 `Task` 对象可能在某些路径中导致性能瓶颈。 `Task` 是引用类型，因此使用它意味着分配对象。 如果使用 `async` 修饰符声明的方法返回缓存结果或以同步方式完成，那么额外的分配在代码的性能关键部分可能要耗费相当长的时间。 如果这些分配发生在紧凑循环中，则成本会变高。

新语言功能意味着异步方法返回类型不限于 `Task`、`Task<T>` 和 `void`。 返回类型必须仍满足异步模式，这意味着 `GetAwaiter` 方法必须是可访问的。 作为一个具体示例，已将 `ValueTask` 类型添加到 .NET 中，以使用这一新语言功能：

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> 需要添加 NuGet 包 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) 才能使用 <xref:System.Threading.Tasks.ValueTask%601> 类型。

此增强功能对于库作者最有用，可避免在性能关键型代码中分配 `Task`。

## <a name="numeric-literal-syntax-improvements"></a>数字文本语法改进

误读的数值常量可能使第一次阅读代码时更难理解。 位掩码或其他符号值容易产生误解。 C# 7.0 包括两项新功能，可用于以最可读的方式写入数字来用于预期用途：二进制文本和数字分隔符 。

在创建位掩码时，或每当数字的二进制表示形式使代码最具可读性时，以二进制形式写入该数字：

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

常量开头的 `0b` 表示该数字以二进制数形式写入。 二进制数可能会很长，因此通过引入 `_` 作为数字分隔符通常更易于查看位模式，如上面二进制常量所示。 数字分隔符可以出现在常量的任何位置。 对于十进制数字，通常将其用作千位分隔符：

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

数字分隔符也可以与 `decimal`、`float` 和 `double` 类型一起使用：

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

综观来说，你可以声明可读性更强的数值常量。
