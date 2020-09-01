---
description: private 关键字 - C# 参考
title: private 关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139393"
---
# <a name="private-c-reference"></a><span data-ttu-id="47139-103">private（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="47139-103">private (C# Reference)</span></span>

<span data-ttu-id="47139-104">`private` 关键字是一个成员访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="47139-104">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="47139-105">本页涵盖 `private` 访问。</span><span class="sxs-lookup"><span data-stu-id="47139-105">This page covers `private` access.</span></span> <span data-ttu-id="47139-106">`private` 关键字也是 [`private protected`](./private-protected.md) 访问修饰符的一部分。</span><span class="sxs-lookup"><span data-stu-id="47139-106">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="47139-107">私有访问是允许的最低访问级别。</span><span class="sxs-lookup"><span data-stu-id="47139-107">Private access is the least permissive access level.</span></span> <span data-ttu-id="47139-108">私有成员只有在声明它们的类和结构体中才是可访问的，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="47139-108">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="47139-109">同一体中的嵌套类型也可以访问那些私有成员。</span><span class="sxs-lookup"><span data-stu-id="47139-109">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="47139-110">在声明私有成员的类或结构外引用它会导致编译时错误。</span><span class="sxs-lookup"><span data-stu-id="47139-110">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="47139-111">有关 `private` 和其他访问修饰符的比较，请参阅[可访问性级别](accessibility-levels.md)和[访问修饰符](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="47139-111">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="47139-112">示例</span><span class="sxs-lookup"><span data-stu-id="47139-112">Example</span></span>

<span data-ttu-id="47139-113">在此示例中，`Employee` 类包含两个私有数据成员 `name` 和 `salary`。</span><span class="sxs-lookup"><span data-stu-id="47139-113">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="47139-114">作为私有成员，它们只能通过成员方法来访问。</span><span class="sxs-lookup"><span data-stu-id="47139-114">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="47139-115">添加名为 `GetName` 和 `Salary` 的公共方法，以便可以对私有成员进行受控的访问。</span><span class="sxs-lookup"><span data-stu-id="47139-115">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="47139-116">通过公共方法访问 `name` 成员，而通过公共只读属性访问 `salary` 成员。</span><span class="sxs-lookup"><span data-stu-id="47139-116">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="47139-117">（有关详细信息，请参阅[属性](../../programming-guide/classes-and-structs/properties.md)。）</span><span class="sxs-lookup"><span data-stu-id="47139-117">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="47139-118">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="47139-118">C# language specification</span></span>  

<span data-ttu-id="47139-119">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[声明的可访问性](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="47139-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="47139-120">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="47139-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="47139-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="47139-121">See also</span></span>

- [<span data-ttu-id="47139-122">C# 参考</span><span class="sxs-lookup"><span data-stu-id="47139-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47139-123">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="47139-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47139-124">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="47139-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="47139-125">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="47139-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="47139-126">可访问性级别</span><span class="sxs-lookup"><span data-stu-id="47139-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="47139-127">修饰符</span><span class="sxs-lookup"><span data-stu-id="47139-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="47139-128">public</span><span class="sxs-lookup"><span data-stu-id="47139-128">public</span></span>](public.md)
- [<span data-ttu-id="47139-129">受保护</span><span class="sxs-lookup"><span data-stu-id="47139-129">protected</span></span>](protected.md)
- [<span data-ttu-id="47139-130">internal</span><span class="sxs-lookup"><span data-stu-id="47139-130">internal</span></span>](internal.md)
