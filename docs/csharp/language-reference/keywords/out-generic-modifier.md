---
description: out 关键字（泛型修饰符） - C# 参考
title: out 关键字（泛型修饰符） - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 84f3647309c0772f6ae61d3614f8649fe277f153
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142331"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="666dd-103">out（泛型修饰符）（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="666dd-103">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="666dd-104">对于泛型类型参数，`out` 关键字可指定类型参数是协变的。</span><span class="sxs-lookup"><span data-stu-id="666dd-104">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="666dd-105">可以在泛型接口和委托中使用 `out` 关键字。</span><span class="sxs-lookup"><span data-stu-id="666dd-105">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="666dd-106">协变使你使用的类型可以比泛型参数指定的类型派生程度更大。</span><span class="sxs-lookup"><span data-stu-id="666dd-106">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="666dd-107">这样可以隐式转换实现协变接口的类以及隐式转换委托类型。</span><span class="sxs-lookup"><span data-stu-id="666dd-107">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="666dd-108">引用类型支持协变和逆变，但值类型不支持它们。</span><span class="sxs-lookup"><span data-stu-id="666dd-108">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="666dd-109">具有协变类型参数的接口使其方法返回的类型可以比类型参数指定的类型派生程度更大。</span><span class="sxs-lookup"><span data-stu-id="666dd-109">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="666dd-110">例如，因为在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，类型 T 是协变的，所以可以将 `IEnumerable(Of String)` 类型的对象分配给 `IEnumerable(Of Object)` 类型的对象，而无需使用任何特殊转换方法。</span><span class="sxs-lookup"><span data-stu-id="666dd-110">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="666dd-111">可以向协变委托分配相同类型的其他委托，不过要使用派生程度更大的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="666dd-111">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="666dd-112">有关详细信息，请参阅[协变和逆变](../../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="666dd-112">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="666dd-113">示例 - 协变泛型接口</span><span class="sxs-lookup"><span data-stu-id="666dd-113">Example - covariant generic interface</span></span>

<span data-ttu-id="666dd-114">下面的示例演示如何声明、扩展和实现协变泛型接口。</span><span class="sxs-lookup"><span data-stu-id="666dd-114">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="666dd-115">它还演示如何对实现协变接口的类使用隐式转换。</span><span class="sxs-lookup"><span data-stu-id="666dd-115">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="666dd-116">在泛型接口中，如果类型参数满足以下条件，则可以声明为协变：</span><span class="sxs-lookup"><span data-stu-id="666dd-116">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="666dd-117">类型参数只用作接口方法的返回类型，而不用作方法参数的类型。</span><span class="sxs-lookup"><span data-stu-id="666dd-117">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="666dd-118">此规则有一个例外。</span><span class="sxs-lookup"><span data-stu-id="666dd-118">There is one exception to this rule.</span></span> <span data-ttu-id="666dd-119">如果在协变接口中将逆变泛型委托用作方法参数，则可以将协变类型用作此委托的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="666dd-119">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="666dd-120">有关协变和逆变泛型委托的详细信息，请参阅[委托中的变体](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)和[对 Func 和 Action 泛型委托使用变体](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="666dd-120">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="666dd-121">类型参数不用作接口方法的泛型约束。</span><span class="sxs-lookup"><span data-stu-id="666dd-121">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="666dd-122">示例 - 协变泛型委托</span><span class="sxs-lookup"><span data-stu-id="666dd-122">Example - covariant generic delegate</span></span>

<span data-ttu-id="666dd-123">以下示例演示如何声明、实例化和调用协变泛型委托。</span><span class="sxs-lookup"><span data-stu-id="666dd-123">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="666dd-124">它还演示如何隐式转换委托类型。</span><span class="sxs-lookup"><span data-stu-id="666dd-124">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="666dd-125">在泛型委托中，如果类型仅用作方法返回类型，而不用于方法参数，则可以声明为协变。</span><span class="sxs-lookup"><span data-stu-id="666dd-125">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="666dd-126">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="666dd-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="666dd-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="666dd-127">See also</span></span>

- [<span data-ttu-id="666dd-128">泛型接口中的变体</span><span class="sxs-lookup"><span data-stu-id="666dd-128">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="666dd-129">in</span><span class="sxs-lookup"><span data-stu-id="666dd-129">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="666dd-130">修饰符</span><span class="sxs-lookup"><span data-stu-id="666dd-130">Modifiers</span></span>](index.md)
