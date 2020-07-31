---
title: 隐式类型数组 - C# 编程指南
description: C# 中隐式类型数组中的类型通过数组初始值设定项中的元素来推断。 在查询表达式中使用隐式类型数组。
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 1f14f68207dfb79c92eaa01ac2a8ffaa08facc03
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474704"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="2dee8-104">隐式类型的数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2dee8-104">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2dee8-105">可以创建隐式类型化的数组，其中数组实例的类型通过数组初始值设定项中指定的元素来推断。</span><span class="sxs-lookup"><span data-stu-id="2dee8-105">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="2dee8-106">针对隐式类型化变量的任何规则也适用于隐式类型化数组。</span><span class="sxs-lookup"><span data-stu-id="2dee8-106">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="2dee8-107">有关详细信息，请参阅[隐式类型局部变量](../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="2dee8-107">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="2dee8-108">隐式类型化数组通常用于查询表达式、匿名类型、对象和集合初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="2dee8-108">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="2dee8-109">下列示例演示如何创建隐式类型化数组：</span><span class="sxs-lookup"><span data-stu-id="2dee8-109">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="2dee8-110">在上个示例中，请注意对于隐式类型化数组，初始化语句的左侧没有使用方括号。</span><span class="sxs-lookup"><span data-stu-id="2dee8-110">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="2dee8-111">另请注意，和一维数组一样，通过使用 `new []` 来初始化交错数组。</span><span class="sxs-lookup"><span data-stu-id="2dee8-111">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="2dee8-112">对象初始值设定项中隐式类型化数组</span><span class="sxs-lookup"><span data-stu-id="2dee8-112">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="2dee8-113">创建包含数组的匿名类型时，必须在类型的对象初始值设定项中隐式类型化数组。</span><span class="sxs-lookup"><span data-stu-id="2dee8-113">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="2dee8-114">在下列示例中，`contacts` 是匿名类型的隐式类型化数组，每个类型都包含名为 `PhoneNumbers` 的数组。</span><span class="sxs-lookup"><span data-stu-id="2dee8-114">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="2dee8-115">请注意，不可在对象初始值设定项中使用 `var` 关键字。</span><span class="sxs-lookup"><span data-stu-id="2dee8-115">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="2dee8-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="2dee8-116">See also</span></span>

- [<span data-ttu-id="2dee8-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2dee8-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2dee8-118">隐式类型的局部变量</span><span class="sxs-lookup"><span data-stu-id="2dee8-118">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="2dee8-119">数组</span><span class="sxs-lookup"><span data-stu-id="2dee8-119">Arrays</span></span>](./index.md)
- [<span data-ttu-id="2dee8-120">匿名类型</span><span class="sxs-lookup"><span data-stu-id="2dee8-120">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="2dee8-121">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="2dee8-121">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="2dee8-122">var</span><span class="sxs-lookup"><span data-stu-id="2dee8-122">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="2dee8-123">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="2dee8-123">LINQ in C#</span></span>](../../linq/index.md)
