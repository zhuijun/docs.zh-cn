---
description: nameof 表达式 - C# 参考
title: nameof 表达式 - C# 参考
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04109cde2a1f9146bf9bb44f301272808797ded0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118307"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="70d65-103">nameof 表达式（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="70d65-103">nameof expression (C# reference)</span></span>

<span data-ttu-id="70d65-104">`nameof` 表达式可生成变量、类型或成员的名称作为字符串常量：</span><span class="sxs-lookup"><span data-stu-id="70d65-104">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="70d65-105">如前面的示例所示，对于类型和命名空间，生成的名称通常不是[完全限定的](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)名称。</span><span class="sxs-lookup"><span data-stu-id="70d65-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="70d65-106">在[逐字标识符](../tokens/verbatim.md)的情况下，`@` 字符不是名称的一部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="70d65-106">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="70d65-107">`nameof` 表达式在编译时进行求值，在运行时无效。</span><span class="sxs-lookup"><span data-stu-id="70d65-107">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="70d65-108">可以使用 `nameof` 表达式使参数检查代码更易于维护：</span><span class="sxs-lookup"><span data-stu-id="70d65-108">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="70d65-109">`nameof` 表达式在 C# 6 及更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="70d65-109">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="70d65-110">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="70d65-110">C# language specification</span></span>

<span data-ttu-id="70d65-111">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [Nameof 表达式](~/_csharplang/spec/expressions.md#nameof-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="70d65-111">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70d65-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="70d65-112">See also</span></span>

- [<span data-ttu-id="70d65-113">C# 参考</span><span class="sxs-lookup"><span data-stu-id="70d65-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="70d65-114">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="70d65-114">C# operators and expressions</span></span>](index.md)
