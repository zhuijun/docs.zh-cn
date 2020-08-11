---
title: delegate 运算符 - C# 参考
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: f7cd7caf11d9f076a5d6e82aae696c914bd60e44
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916836"
---
# <a name="delegate-operator-c-reference"></a>delegate 运算符 -（C# 参考）

`delegate` 运算符创建一个可以转换为委托类型的匿名方法：

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> 从 C# 3 开始，lambda 表达式提供了一种更简洁和富有表现力的方式来创建匿名函数。 使用 [=> 运算符](lambda-operator.md)构造 lambda 表达式：
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> 有关 lambda 表达式功能的更多信息（例如，如何捕获外部变量），请参阅 [lambda 表达式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。

使用 `delegate` 运算符时，可以省略参数列表。 如果这样做，可以将创建的匿名方法转换为具有任何参数列表的委托类型，如以下示例所示：

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

这是 lambda 表达式不支持的匿名方法的唯一功能。 在所有其他情况下，lambda 表达式是编写内联代码的首选方法。

还可以使用 `delegate` 关键字声明[委托类型](../builtin-types/reference-types.md#the-delegate-type)。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [匿名函数表达式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。

## <a name="see-also"></a>另请参阅

- [C# 参考](../index.md)
- [C# 运算符和表达式](index.md)
- [=> 运算符](lambda-operator.md)
