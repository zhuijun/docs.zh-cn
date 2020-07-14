---
title: C# 类型和变量 - C# 语言介绍
description: 了解如何在 C# 中定义类型和声明变量
ms.date: 04/24/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: a14291d1eec4d090b0275875326c5a580e5abe9d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174122"
---
# <a name="types-and-variables"></a>类型和变量

C# 有两种类型：*值类型*和*引用类型*。 值类型的变量直接包含数据，而引用类型的变量则存储对数据（称为“对象”）的引用。 对于引用类型，两个变量可以引用同一对象；因此，对一个变量执行的运算可能会影响另一个变量引用的对象。 借助值类型，每个变量都有自己的数据副本；因此，对一个变量执行的运算不会影响另一个变量（`ref` 和 `out` 参数变量除外）。

C# 值类型又细分为简单类型、枚举类型、结构类型和可以为 null 的值类型。     C# 引用类型又细分为类类型、接口类型、数组类型和委托类型。    

以下大纲概述了 C# 的类型系统。

- [值类型][ValueTypes]
  - [简单类型][SimpleTypes]
    - 有符号的整型：`sbyte`、`short`、`int`、`long`
    - 无符号的整型：`byte`、`ushort`、`uint`、`ulong`
    - Unicode 字符：`char`
    - IEEE 二进制浮点：`float`、`double`
    - 高精度十进制浮点数：`decimal`
    - 布尔：`bool`
  - [枚举类型][EnumTypes]
    - 格式为 `enum E {...}` 的用户定义类型
  - [结构类型][StructTypes]
    - 格式为 `struct S {...}` 的用户定义类型
  - [可以为 null 的值类型][NullableTypes]
    - 值为 `null` 的其他所有值类型的扩展
  - [元组值类型][TupleTypes]
    - 格式为 `(T1, T2, ...)` 的用户定义类型
- [引用类型][ReferenceTypes]
  - [类类型][ClassTypes]
    - 其他所有类型的最终基类：`object`
    - Unicode 字符串：`string`
    - 格式为 `class C {...}` 的用户定义类型
  - [接口类型][InterfaceTypes]
    - 格式为 `interface I {...}` 的用户定义类型
  - [数组类型][ArrayTypes]
    - 一维和多维，例如 `int[]` 和 `int[,]`
  - [委托类型][DelegateTypes]
    - 格式为 `delegate int D(...)` 的用户定义类型

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[TupleTypes]: ../language-reference/builtin-types/value-tuples.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

有关数值类型的详细信息，请参阅[整型类型](../language-reference/builtin-types/integral-numeric-types.md)和[浮点类型表](../language-reference/builtin-types/floating-point-numeric-types.md)。

C# 的 `bool` 类型用于表示布尔值（`true` 或 `false`）。

C# 使用 Unicode 编码处理字符和字符串。 `char` 类型表示 UTF-16 代码单元，`string` 类型表示一系列 UTF-16 代码单元。

C# 程序使用*类型声明*创建新类型。 类型声明指定新类型的名称和成员。 用户可定义以下五种 C# 类型：类类型、结构类型、接口类型、枚举类型和委托类型。

`class` 类型定义包含数据成员（字段）和函数成员（方法、属性及其他）的数据结构。 类类型支持单一继承和多形性，即派生类可以扩展和专门针对基类的机制。

`struct` 类型定义包含数据成员和函数成员的结构，这一点与类类型相似。 不过，与类不同的是，结构是值类型，通常不需要进行堆分配。 结构类型不支持用户指定的继承，并且所有结构类型均隐式继承自类型 `object`。

`interface` 类型将协定定义为一组已命名的公共函数成员。 实现 `interface` 的 `class` 或 `struct` 必须提供接口函数成员的实现代码。 `interface` 可以继承自多个基接口，`class` 和 `struct` 可以实现多个接口。

`delegate` 类型表示引用包含特定参数列表和返回类型的方法。 通过委托，可以将方法视为可分配给变量并可作为参数传递的实体。 委托类同于函数式语言提供的函数类型。 它们还类似于其他一些语言中存在的“函数指针”概念。 与函数指针不同，委托是面向对象且类型安全的。

`class`、`struct`、`interface` 和 `delegate` 类型全部都支持泛型，因此可以使用其他类型对它们进行参数化。

`enum` 类型是一种包含已命名常量的独特类型。 每个 `enum` 类型都有一个基础类型（必须是八种整型类型之一）。 `enum` 类型的值集与基础类型的值集相同。

C# 支持任意类型的一维和多维数组。 与上述类型不同，数组类型无需先声明即可使用。 相反，数组类型是通过在类型名称后面添加方括号构造而成。 例如，`int[]` 是 `int` 类型的一维数组，`int[,]` 是 `int` 类型的二维数组，`int[][]` 是由 `int` 类型的一维数组构成的一维数组。

可以为 null 的值类型也无需先声明即可使用。 对于所有不可以为 null 的值类型 `T`，都有对应的可以为 null 的值类型 `T?`，后者可以包含附加值 `null`。 例如，`int?` 是可以包含任何 32 位整数或值 `null` 的类型。

C# 采用统一的类型系统，因此任意类型的值都可视为 `object`。 每种 C# 类型都直接或间接地派生自 `object` 类类型，而 `object` 是所有类型的最终基类。 只需将值视为类型 `object`，即可将引用类型的值视为对象。 通过执行*装箱*和*取消装箱操作*，可以将值类型的值视为对象。 在以下示例中，`int` 值被转换成 `object`，然后又恢复成 `int`。

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

将值类型的值分配给 `object` 对象引用时，会分配一个“箱”来保存此值。 该箱是引用类型的实例，此值会被复制到该箱。 相反，当 `object` 引用被显式转换成值类型时，将检查引用的 `object` 是否是具有正确值类型的箱。 如果检查成功，则会将箱中的值复制到值类型。

C# 的统一类型系统实际上意味着“按需”将值类型视为 `object` 引用。 鉴于这种统一性，使用类型 `object` 的常规用途库可以与派生自 `object` 的所有类型结合使用，包括引用类型和值类型。

C# 有多种*变量*，其中包括字段、数组元素、局部变量和参数。 变量表示存储位置，每个变量都具有一种类型，用于确定可以在变量中存储哪些值，如下文所述。

- 不可以为 null 的值类型
  - 具有精确类型的值
- 可以为 null 的值类型
  - `null` 值或具有精确类型的值
- object
  - `null` 引用、对任意引用类型的对象的引用，或对任意值类型的装箱值的引用
- 类类型
  - `null` 引用、对类类型实例的引用，或对派生自类类型的类实例的引用
- 接口类型
  - `null` 引用、对实现接口类型的类类型实例的引用，或对实现接口类型的值类型的装箱值的引用
- 数组类型
  - `null` 引用、对数组类型实例的引用，或对兼容的数组类型实例的引用
- 委托类型
  - `null` 引用或对兼容的委托类型实例的引用

> [!div class="step-by-step"]
> [上一页](program-structure.md)
> [下一页](expressions.md)
