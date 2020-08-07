---
title: 序列
description: '如果有大量的有序数据集合，但不一定要使用所有元素，请了解如何使用 F # 序列。'
ms.date: 11/04/2019
ms.openlocfilehash: fa5073f33b9dae52371c249bfb257a2446b4d26a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855317"
---
# <a name="sequences"></a>序列

*序列*是所有类型的元素的逻辑系列。 如果有大量的有序数据集合，但不一定需要使用所有元素，则序列将特别有用。 单个序列元素只会根据需要计算，因此，在不使用所有元素的情况下，序列可提供比列表更好的性能。 序列由 `seq<'T>` 类型表示，该类型是的别名 <xref:System.Collections.Generic.IEnumerable%601> 。 因此，实现接口的任何 .NET 类型 <xref:System.Collections.Generic.IEnumerable%601> 都可用作序列。 [Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)为涉及序列的操作提供支持。

> [!NOTE]
> F # 的 docs.microsoft.com API 参考未完成。 如果遇到任何断开的链接，请参阅[F # 核心库文档](https://fsharp.github.io/fsharp-core-docs/)。

## <a name="sequence-expressions"></a>序列表达式

*序列表达式*是计算结果为序列的表达式。 序列表达式可以采用多种形式。 最简单的形式是指定一个范围。 例如， `seq { 1 .. 5 }` 创建一个包含五个元素的序列，包括终结点1和5。 您还可以指定增量 (或减量) 两个双句点之间。 例如，下面的代码创建10的倍数序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

序列表达式由生成序列值的 F # 表达式组成。 还可以通过编程方式生成值：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

前面的示例使用 `->` 运算符，这允许您指定一个表达式，该表达式的值将成为序列的一部分。 仅 `->` 当其后的代码的每个部分都返回值时，才能使用。

另外，还可以指定 `do` 关键字，其中包含以下选项 `yield` ：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

下面的代码将生成一个坐标对列表，以及一个表示该网格的数组的索引。 请注意，第一个 `for` 表达式需要 `do` 指定。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`序列中使用的表达式是筛选器。 例如，若要生成一个仅包含质数的序列，假设你有一个 `isprime` 类型的函数 `int -> bool` ，请按如下所示构造序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

如前文所述， `do` 此处是必需的，因为没有 `else` 与一起的分支 `if` 。 如果你尝试使用 `->` ，将收到一条错误消息，指出并非所有分支都返回值。

## <a name="the-yield-keyword"></a>`yield!` 关键字

有时，你可能希望将一系列元素包含在另一个序列中。 若要在另一个序列内包含序列，需要使用 `yield!` 关键字：

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

考虑到的另一种方法 `yield!` 是将内部序列平展，然后将其包含在包含序列中。

`yield!`在表达式中使用时，所有其他单个值必须使用 `yield` 关键字：

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

仅 `x` 在前面的示例中指定将导致序列不生成值。

## <a name="examples"></a>示例

第一个示例使用包含迭代、筛选器和 yield 的序列表达式来生成数组。 此代码会将1到100之间的质数序列输出到控制台。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

下面的示例创建一个乘法表，其中包含三个元素的元组，每个元素包含两个因素和产品：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

下面的示例演示 `yield!` 如何使用将各个序列合并为一个最终序列。 在这种情况下，将在一个递归函数中串联二元树中每个子树的序列，以生成最终序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>使用序列

序列支持许多与[列表](lists.md)相同的函数。 序列还支持通过使用键生成函数进行分组和计数等操作。 序列还支持用于提取个子序列的更广泛的函数。

许多数据类型（例如列表、数组、集和映射）都是隐式的，因为它们是可枚举的集合。 采用序列作为参数的函数除了实现的任何 .NET 数据类型外，还适用于任何常见的 F # 数据类型 `System.Collections.Generic.IEnumerable<'T>` 。 将此与采用列表作为参数的函数相反，只能采用列表。 类型 `seq<'T>` 是的类型缩写 `IEnumerable<'T>` 。 这意味着，实现泛型的任何类型 `System.Collections.Generic.IEnumerable<'T>` （包括数组、列表、集和 F # 中的映射）以及大多数 .net 集合类型都与类型兼容， `seq` 可在需要序列的任何位置使用。

## <a name="module-functions"></a>模块函数

[Fsharp.core 命名空间](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)中的[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)包含用于处理序列的函数。 这些函数也适用于列表、数组、映射和集，因为这些类型都是可枚举的，因此可以视为序列。

## <a name="creating-sequences"></a>创建序列

您可以使用序列表达式（如前文所述）或使用特定函数来创建序列。

您可以通过使用[序列 empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)创建一个空序列，也可以通过使用[seq. singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)创建只具有一个指定元素的序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

您可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)创建使用您提供的函数为其创建元素的序列。 还可为序列提供大小。 此函数与[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)类似，只是在遍历序列之前不会创建元素。 下面的代码演示如何使用 `Seq.init` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

输出为

```console
0 10 20 30 40
```

通过使用[list.ofarray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)和[array.oflist&#60; 不&#62; 函数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，你可以从数组和列表创建序列。 不过，还可以使用转换运算符将数组和列表转换为序列。 下面的代码演示了这两种方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

通过使用[Seq](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，你可以从弱类型集合中创建一个序列，如中定义的集合 `System.Collections` 。 此类弱类型集合具有元素类型 `System.Object` ，并使用非泛型类型进行枚举 `System.Collections.Generic.IEnumerable&#96;1` 。 下面的代码演示 `Seq.cast` 如何使用将转换为 `System.Collections.ArrayList` 序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

可以通过使用[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函数来定义无限序列。 对于这种序列，你提供了一个函数，该函数从元素的索引生成每个元素。 由于延迟计算，可能会出现无限序列;根据需要通过调用指定的函数来创建元素。 下面的代码示例生成一个无限的浮点数序列，在此示例中，为连续整数的 reciprocals 序列。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq：](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)从采用状态并将其转换为生成序列中每个后续元素的计算函数生成序列。 状态只是用于计算每个元素的值，并且可以在计算每个元素时进行更改。 的第二个参数 `Seq.unfold` 是用于启动序列的初始值。 `Seq.unfold`将选项类型用于状态，这使你可以通过返回值来终止序列 `None` 。 下面的代码演示了两个序列的示例， `seq1` 以及 `fib` 由操作生成的 `unfold` 。 第一个 `seq1` 是，它是数字最多为20的简单序列。 第二个 `fib` 使用 `unfold` 来计算斐波那契序列。 因为波那契序列中的每个元素都是前两个斐波那契数的总和，所以，状态值是包含序列中前两个数字的元组。 初始值为 `(1,1)` ，序列中的前两个数字。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

输出如下所示：

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

下面的代码示例使用此处所述的许多序列模块函数来生成和计算无限序列的值。 此代码可能需要几分钟才能运行。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>搜索和查找元素

序列支持可用于列表的功能[： seq.](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1) [array.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)，seq [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [seq，](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d) [tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，，array.tryfindindex. [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。 可用于序列的这些函数的版本仅计算到所搜索的元素的顺序。 有关示例，请参阅[列表](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。

## <a name="obtaining-subsequences"></a>获取个子序列

[Seq. filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)和[seq。 choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)类似于列表可用的相应函数，但在计算序列元素之前，不会发生筛选和选择。

[Seq](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)从另一个序列创建序列，但将序列限制为指定数量的元素。 [Seq。 take 会](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)创建一个新序列，该序列只包含序列开头的指定数量的元素。 如果序列中的元素少于您指定要执行的元素， `Seq.take` 则将引发 `System.InvalidOperationException` 。 与之间的区别在于， `Seq.take` `Seq.truncate` `Seq.truncate` 如果元素数少于指定的数目，则不会产生错误。

下面的代码演示了和之间的行为 `Seq.truncate` `Seq.take` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

出现错误之前的输出如下所示。

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

通过使用[takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，你可以 (布尔函数指定一个谓词函数) 并从另一个序列中创建一个序列，该序列由该谓词的原始序列的那些元素组成 `true` ，但在该谓词返回的第一个元素之前停止 `false` 。 [Seq： skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)返回一个序列，该序列跳过另一个序列的指定数目的第一个元素，并返回剩余的元素。 [SkipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)返回一个序列，该序列在谓词返回的情况下跳过另一个序列的第一个元素 `true` ，然后返回剩余的元素（从该谓词返回的第一个元素开始） `false` 。

下面的代码示例演示了、和的行为 `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

输出如下所示。

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>转换序列

[Seq。](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)将创建一个新序列，其中输入序列的连续元素分为元组。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)类似 `Seq.pairwise` ，只是它会生成一系列数组，其中包含序列中的*窗口*)  (相邻元素的副本。 指定每个数组中所需的相邻元素的数目。

以下代码示例演示了 `Seq.windowed` 的用法。 在此示例中，窗口中的元素数为3。 该示例使用 `printSeq` 上一个代码示例中定义的。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

输出如下所示。

初始顺序：

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>具有多个序列的操作

[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)和[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)接受两个或三个序列，并生成元组序列。 这些函数类似于[列表](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)可用的对应函数。 没有相应的功能可将一个序列分隔成两个或更多个序列。 如果需要为序列使用此功能，请将序列转换为列表，并使用[list。](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)

## <a name="sorting-comparing-and-grouping"></a>排序、比较和分组

列表支持的排序函数也适用于序列。 这包括[seq](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)和[sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。 这些函数循环访问整个序列。

使用[seq.comparewith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函数比较两个序列。 函数依次比较连续的元素，并在遇到第一个不相等对时停止。 任何其他元素不参与比较。

以下代码显示了 `Seq.compareWith` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

在前面的代码中，只计算并检查第一个元素，结果为-1。

[CountBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)采用一个函数，该函数为每个元素生成一个名为*key*的值。 通过对每个元素调用此函数，为每个元素生成一个密钥。 `Seq.countBy`然后返回一个序列，其中包含键值，以及生成每个密钥值的元素数的计数。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

输出如下所示。

```console
(1, 34) (2, 33) (0, 33)
```

前面的输出显示，原始序列中有34个元素，这些元素生成了键1，33值生成了键2，并显示了生成密钥0的33值。

可以通过调用序列[groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)对序列中的元素进行分组。 `Seq.groupBy`采用一个序列和一个从元素生成键的函数。 函数在序列的每个元素上执行。 `Seq.groupBy`返回一个元组序列，其中每个元组的第一个元素是键，第二个元素是生成该键的元素的序列。

下面的代码示例演示 `Seq.groupBy` 如何使用将编号从1到100的序列分为三个组，这些组具有非重复键值0、1和2。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

输出如下所示。

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

通过调用 Seq，可以创建一个消除重复元素的序列[。](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401) 或者，可以使用[seq.distinctby](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，它采用在每个元素上调用的键生成函数。 生成的序列包含具有唯一键的原始序列的元素;随后将丢弃向早期元素生成重复键的元素。

下面的代码示例阐释了的用法 `Seq.distinct` 。 `Seq.distinct`通过生成表示二进制数字的序列，并显示唯一不同的元素是0和1来演示。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

下面的代码演示了 `Seq.distinctBy` 一个序列，该序列包含负数和正数，并使用绝对值函数作为键生成函数。 生成的序列缺少与序列中的负数相对应的所有正数，因为负数出现在序列的前面，因此选择了，而不是具有相同绝对值或键的正数。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Readonly 和缓存序列

[Seq readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)创建序列的只读副本。 `Seq.readonly`当你具有读写集合（如数组），并且你不希望修改原始集合时，此方法非常有用。 此函数可用于保留数据封装。 在下面的代码示例中，创建了一个包含数组的类型。 属性将公开数组，但不返回数组，而是返回从数组使用创建的序列 `Seq.readonly` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq：](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)创建序列的存储版本。 使用 `Seq.cache` 可以避免重新计算序列，或者当你有多个使用序列的线程时，但必须确保每个元素仅被处理一次。 如果有多个线程正在使用的序列，则可以让一个线程枚举并计算原始序列的值，其余线程可以使用缓存的序列。

## <a name="performing-computations-on-sequences"></a>对序列执行计算

简单的算术运算类似于列表的操作，如[seq](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)、seq、 [sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)、 [averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)、 [sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)等。

[序列摺](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)、 [seq、化简](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)和[seq。扫描](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)类似于列表可用的对应函数。 序列支持列出支持的这些功能的一部分完全不同。 有关详细信息和示例，请参阅[列表](lists.md)。

## <a name="see-also"></a>另请参阅

- [F# 语言参考](index.md)
- [F# 类型](fsharp-types.md)
