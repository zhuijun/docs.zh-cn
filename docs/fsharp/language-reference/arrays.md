---
title: 数组
description: '了解如何在 F # 编程语言中创建和使用数组。'
ms.date: 05/16/2016
ms.openlocfilehash: f95ca3274e098fda044973a48205cb591ec30b27
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855603"
---
# <a name="arrays"></a>数组

数组是固定大小的、从零开始、可变的连续数据元素集合，这些元素属于同一类型。

> [!NOTE]
> F # 的 docs.microsoft.com API 参考未完成。 如果遇到任何断开的链接，请参阅[F # 核心库文档](https://fsharp.github.io/fsharp-core-docs/)。

## <a name="create-arrays"></a>创建数组

可以通过多种方式创建数组。 您可以通过在和之间列出连续的值并 `[|` 用分号分隔，来创建一个小型数组 `|]` ，如下面的示例中所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

您还可以将每个元素放在单独的行上，在这种情况下，分号分隔符是可选的。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

数组元素的类型是从使用的文本中推断出来的，并且必须一致。 下面的代码会导致错误，因为1.0 为 float，2和3是整数。

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

您还可以使用序列表达式来创建数组。 下面的示例创建一个从1到10的整数的平方的数组。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

若要创建将所有元素都初始化为零的数组，请使用 `Array.zeroCreate` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a>访问元素

您可以使用点运算符 (`.`) 和括号 (和) 来访问数组 `[` 元素 `]` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

数组索引从0开始。

您还可以通过使用切片表示法来访问数组元素，这使您能够指定数组的子范围。 下面是切片表示法的示例。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

使用切片表示法时，将创建数组的新副本。

## <a name="array-types-and-modules"></a>数组类型和模块

所有 F # 数组的类型都是 .NET Framework 类型 <xref:System.Array?displayProperty=nameWithType> 。 因此，F # 数组支持中所有可用的功能 <xref:System.Array?displayProperty=nameWithType> 。

库模块 [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) 支持对一维数组进行的操作。 模块 `Array2D` 、 `Array3D` 和 `Array4D` 包含的函数分别支持对2、3和4维数组的操作。 可以使用创建秩大于四的数组 <xref:System.Array?displayProperty=nameWithType> 。

### <a name="simple-functions"></a>简单函数

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)获取元素。 [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)给出数组的长度。 [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)将元素设置为指定值。 下面的代码示例阐释了这些函数的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

输出如下所示。

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>创建数组的函数

多个函数创建数组，无需现有数组。 [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)创建不包含任何元素的新数组。 [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)创建指定大小的数组，并将所有元素设置为提供的值。 [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)在给定维度和函数以生成元素的情况下，创建一个数组。 [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)创建一个数组，其中所有元素都初始化为数组的类型的零值。 下面的代码演示了这些函数。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

输出如下所示。

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)创建一个新数组，其中包含从现有数组中复制的元素。 请注意，副本是一个浅表复制，这意味着，如果元素类型为引用类型，则仅复制引用，而不复制基础对象。 下面的代码示例阐释了这一点。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

上述代码的输出如下所示：

```console
[|Test1; Test2; |]
[|; Test2; |]
```

字符串 `Test1` 仅出现在第一个数组中，因为创建新元素的操作会覆盖中的引用， `firstArray` 但不会影响对仍存在于中的空字符串的原始引用 `secondArray` 。 此字符串 `Test2` 出现在两个数组中 `Insert` ，因为对该类型的操作 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 会影响 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 在这两个数组中引用的基础对象。

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)从数组的子范围生成新数组。 可以通过提供起始索引和长度来指定子范围。 以下代码演示了 `Array.sub` 的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

输出显示子数组从元素5开始，包含10个元素。

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)通过合并两个现有的数组创建新的数组。

下面的代码演示了**数组 append**。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

上述代码的输出如下所示。

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)选择要包含在新数组中的数组元素。 下面的代码演示了 `Array.choose` 。 请注意，数组的元素类型不必与选项类型中返回的值的类型相匹配。 在此示例中，元素类型为 `int` ，而选项是多项式函数的结果， `elem*elem - 1` 作为浮点数。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

上述代码的输出如下所示。

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)在现有数组的每个数组元素上运行指定函数，然后收集该函数生成的元素，并将它们合并到新数组中。 下面的代码演示了 `Array.collect` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

上述代码的输出如下所示。

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)采用一系列数组，并将它们合并到一个数组中。 下面的代码演示了 `Array.concat` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

上述代码的输出如下所示。

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)采用布尔条件函数并生成一个新数组，该数组仅包含其条件为 true 的输入数组中的元素。 下面的代码演示了 `Array.filter` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

上述代码的输出如下所示。

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)通过反转现有数组的顺序生成新的数组。 下面的代码演示了 `Array.rev` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

上述代码的输出如下所示。

```console
"Hello world!"
```

您可以通过使用管道运算符 () 轻松地组合数组模块中的函数 `|>` ，如下面的示例中所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

输出为

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>多维数组

可以创建多维数组，但没有用于写入多维数组文本的语法。 使用运算符 [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) 可从数组元素序列序列创建数组。 序列可以是数组或列表文本。 例如，下面的代码创建一个二维数组。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

您还可以使用函数 [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) 初始化两个维度的数组，并且类似的函数可用于三个和四个维度的数组。 这些函数采用用于创建元素的函数。 若要创建一个二维数组，其中包含设置为初始值的元素，而不是指定函数，请使用 [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) 函数，该函数也可用于最多四个维度的数组。 下面的代码示例首先演示如何创建包含所需元素的数组数组，然后使用 `Array2D.init` 生成所需的二维数组。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

秩为4的数组支持数组索引和切片语法。 当在多个维度中指定索引时，可以使用逗号分隔索引，如以下代码示例中所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

二维数组的类型被写出为 `<type>[,]` (例如， `int[,]` `double[,]`) ，而将三维数组的类型编写为 `<type>[,,]` ，依此类推，对于更高维度的数组，也是如此。

对于多维数组，只能使用适用于一维数组的函数子集。 有关详细信息，请参阅 [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d) 、、 [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d) [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d) 和 [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d) 。

### <a name="array-slicing-and-multidimensional-arrays"></a>数组切片和多维数组

在矩阵)  (二维数组中，可以通过指定范围并使用通配符 (`*`) 字符来指定整行或整列来提取子矩阵。

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

从 F # 3.1 可以将多维数组分解为相同或较低维度的子。 例如，您可以通过指定单个行或列从矩阵获取向量。

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

可以将此切片语法用于实现元素访问运算符和重载方法的类型 `GetSlice` 。 例如，下面的代码创建一个矩阵类型，该类型包装 F # 二维二维数组，实现项属性以提供对数组索引的支持，并实现的三个版本 `GetSlice` 。 如果可以将此代码用作矩阵类型的模板，则可以使用本部分所述的所有切片操作。

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>数组上的布尔函数

分别为 [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) 一个或两个数组中的函数和测试元素。 `true`如果满足条件的) 有元素 (或元素对，则这些函数将采用测试函数并返回 `Array.exists2` 。

下面的代码演示如何使用 `Array.exists` 和 `Array.exists2` 。 在这些示例中，通过仅应用一个自变量（在这种情况下为函数参数）来创建新函数。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

上述代码的输出如下所示。

```console
true
false
false
true
```

同样，函数 [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) 测试数组以确定每个元素是否都满足布尔条件。 变体 [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) 通过使用包含长度相等的两个数组的元素的布尔函数来执行相同的操作。 下面的代码阐释了这些函数的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

这些示例的输出如下所示。

```console
false
true
true
false
```

### <a name="search-arrays"></a>搜索数组

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)采用布尔函数并返回函数为其返回的第一个元素 `true` ， <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> 如果找不到满足条件的元素，则引发。 [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)类似于 `Array.find` ，但它返回元素的索引，而不是元素本身。

下面的代码使用 `Array.find` 和 `Array.findIndex` 来查找同时为完全方形和完全相同的多维数据集的数字。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

输出如下所示。

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)类似于 `Array.find` ，只不过其结果是选项类型， `None` 如果未找到元素，则返回。 `Array.tryFind``Array.find`如果你不知道匹配的元素是否在数组中，则应使用而不是。 同样， [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) 类似于， [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) 只不过选项类型是返回值。 如果未找到元素，则选项为 `None` 。

以下代码演示了 `Array.tryFind` 的用法。 此代码依赖于前面的代码。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

输出如下所示。

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

[`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e)除了查找元素外，还需要转换某个元素。 结果是函数为其返回转换后的元素作为选项值的第一个元素; `None` 如果未找到这样的元素，则为。

以下代码显示了 `Array.tryPick` 的用法。 在这种情况下，不是 lambda 表达式，而是定义了若干本地 helper 函数以简化代码。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

输出如下所示。

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a>对数组执行计算

[`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e)函数返回数组中每个元素的平均值。 它限制为支持完全除以整数的元素类型，包括浮点类型，但不支持整数类型。 [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54)函数返回对每个元素调用函数的结果的平均值。 对于整型类型的数组，可以使用 `Array.averageBy` ，并让函数将每个元素转换为浮点类型进行计算。

[`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) 如果元素类型支持，则使用或获取最大或最小元素。 同样， [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) 和 [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) 允许先执行函数，也许是转换为支持比较的类型。

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)添加数组的元素，并对 [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) 每个元素调用一个函数，并将结果添加到一起。

若要对数组中的每个元素执行函数而不存储返回值，请使用 [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516) 。 对于涉及两个相等长度数组的函数，请使用 [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc) 。 如果还需要保留函数结果的数组，请使用 [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) 或 [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c) ，这一次在两个数组上进行操作。

变体 [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) 和 [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) 允许在计算中涉及元素的索引; 对于和，情况也是如此 [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0) 。

函数、、、、 [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09) [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c) [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d) [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9) [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0) 和 [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) 执行的算法涉及数组的所有元素。 同样，在 [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) 两个数组上进行变化并执行计算。

用于执行计算的这些函数对应于[列表模块](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)中具有相同名称的函数。 有关用法示例，请参阅[列表](lists.md)。

### <a name="modify-arrays"></a>修改数组

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)将元素设置为指定值。 [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)将数组中的一系列元素设置为指定值。 下面的代码提供了一个示例 `Array.fill` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

输出如下所示。

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

您可以使用将 [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) 一个数组的子节复制到另一个数组。

### <a name="convert-to-and-from-other-types"></a>与其他类型相互转换

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)从列表创建数组。 [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)从序列创建数组。 [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)并 [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) 从数组类型转换为这些其他集合类型。

### <a name="sort-arrays"></a>数组排序

使用 [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) 可通过泛型比较函数对数组进行排序。 用于 [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) 指定一个函数，该函数生成一个值（称为*密钥*），以便通过对键使用泛型比较函数进行排序。 [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95)如果要提供自定义比较函数，请使用。 `Array.sort`、 `Array.sortBy` 和 `Array.sortWith` 都作为新数组返回已排序的数组。 变体 [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0) 、 [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f) 和 [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) 修改现有数组，而不是返回新数组。

### <a name="arrays-and-tuples"></a>数组和元组

函数 [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) 和 [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) 将元组对的数组转换为数组的元组，反之亦然。 [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)和 [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) 类似，只不过它们适用于三个元素的元组或三个数组的元组。

## <a name="parallel-computations-on-arrays"></a>数组上的并行计算

模块 [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) 包含用于对数组执行并行计算的函数。 此模块在面向版本4之前的 .NET Framework 版本的应用程序中不可用。

## <a name="see-also"></a>另请参阅

- [F# 语言参考](index.md)
- [F# 类型](fsharp-types.md)
