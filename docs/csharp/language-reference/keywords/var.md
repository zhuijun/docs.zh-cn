---
description: var - C# 参考
title: var - C# 参考
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141707"
---
# <a name="var-c-reference"></a>var（C# 参考）

从 Visual C# 3.0 开始，在方法范围内声明的变量可以具有隐式“类型”`var`。 隐式类型本地变量为强类型，就像用户已经自行声明该类型，但编译器决定类型一样。 `i` 的以下两个声明在功能上是等效的：

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

有关详细信息，请参阅[隐式类型的局部变量](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [LINQ 查询操作中的类型关系](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。

> [!IMPORTANT]
> 在启用可为空引用类型的情况下使用 `var` 时，即使表达式类型不可为空，也始终表示可为空引用类型。

## <a name="example"></a>示例

下面的示例演示两个查询表达式。 在第一个表达式中，`var` 的使用是允许的，但不是必需的，因为查询结果的类型可以明确表述为 `IEnumerable<string>`。 不过，在第二个表达式中，`var` 允许结果是一系列匿名类型，且相应类型的名称只可供编译器本身访问。 如果使用 `var`，便无法为结果新建类。 请注意，在示例 #2 中，`foreach` 迭代变量 `item` 必须也为隐式类型。

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [隐式类型的局部变量](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
