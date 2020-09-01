---
description: static 修饰符 - C# 参考
title: static 修饰符 - C# 参考
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f42636d1bbdf4342297f46f50ec6dfc2a70eacad
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142058"
---
# <a name="static-c-reference"></a><span data-ttu-id="43f17-103">static（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="43f17-103">static (C# Reference)</span></span>

<span data-ttu-id="43f17-104">本页介绍 `static` 修饰符关键字。</span><span class="sxs-lookup"><span data-stu-id="43f17-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="43f17-105">`static` 关键字也是 [`using static`](using-static.md) 指令的一部分。</span><span class="sxs-lookup"><span data-stu-id="43f17-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="43f17-106">使用 `static` 修饰符可声明属于类型本身而不是属于特定对象的静态成员。</span><span class="sxs-lookup"><span data-stu-id="43f17-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="43f17-107">`static` 修饰符可用于声明 `static` 类。</span><span class="sxs-lookup"><span data-stu-id="43f17-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="43f17-108">在类、接口和结构中，可以将 `static` 修饰符添加到字段、方法、属性、运算符、事件和构造函数。</span><span class="sxs-lookup"><span data-stu-id="43f17-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="43f17-109">`static` 修饰符不能用于索引器或终结器。</span><span class="sxs-lookup"><span data-stu-id="43f17-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="43f17-110">有关详细信息，请参阅[静态类和静态类成员](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="43f17-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="43f17-111">示例 - 静态类</span><span class="sxs-lookup"><span data-stu-id="43f17-111">Example - static class</span></span>

<span data-ttu-id="43f17-112">下面的类声明为 `static` 并且只含 `static` 方法：</span><span class="sxs-lookup"><span data-stu-id="43f17-112">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="43f17-113">常数或类型声明是隐式的 `static` 成员。</span><span class="sxs-lookup"><span data-stu-id="43f17-113">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="43f17-114">不能通过实例引用 `static` 成员。</span><span class="sxs-lookup"><span data-stu-id="43f17-114">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="43f17-115">然而，可以通过类型名称引用它。</span><span class="sxs-lookup"><span data-stu-id="43f17-115">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="43f17-116">例如，请考虑以下类：</span><span class="sxs-lookup"><span data-stu-id="43f17-116">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="43f17-117">若要引用 `static` 成员 `x`，除非可从相同范围访问该成员，否则请使用完全限定的名称 `MyBaseC.MyStruct.x`：</span><span class="sxs-lookup"><span data-stu-id="43f17-117">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="43f17-118">尽管类的实例包含该类的所有实例字段的单独副本，但每个 `static` 字段只有一个副本。</span><span class="sxs-lookup"><span data-stu-id="43f17-118">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="43f17-119">不可以使用 [`this`](this.md) 引用 `static` 方法或属性访问器。</span><span class="sxs-lookup"><span data-stu-id="43f17-119">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="43f17-120">如果 `static` 关键字应用于类，则类的所有成员都必须为 `static`。</span><span class="sxs-lookup"><span data-stu-id="43f17-120">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="43f17-121">类、接口和 `static` 类可以具有 `static` 构造函数。</span><span class="sxs-lookup"><span data-stu-id="43f17-121">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="43f17-122">在程序开始和实例化类之间的某个时刻调用 `static` 构造函数。</span><span class="sxs-lookup"><span data-stu-id="43f17-122">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="43f17-123">`static` 关键字比用于 C++ 中时受到的限制更多。</span><span class="sxs-lookup"><span data-stu-id="43f17-123">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="43f17-124">若要与 C++ 关键字进行比较，请参阅 [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static)（存储类 (C++)）。</span><span class="sxs-lookup"><span data-stu-id="43f17-124">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="43f17-125">若要演示 `static` 成员，请考虑表示公司员工的类。</span><span class="sxs-lookup"><span data-stu-id="43f17-125">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="43f17-126">假定此类包含计数员工的方法和存储员工人数的字段。</span><span class="sxs-lookup"><span data-stu-id="43f17-126">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="43f17-127">方法和字段均不属于任何一个员工实例。</span><span class="sxs-lookup"><span data-stu-id="43f17-127">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="43f17-128">相反，它们属于全体员工这个类。</span><span class="sxs-lookup"><span data-stu-id="43f17-128">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="43f17-129">应将其声明为该类的 `static` 成员。</span><span class="sxs-lookup"><span data-stu-id="43f17-129">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="43f17-130">示例 - 静态字段和方法</span><span class="sxs-lookup"><span data-stu-id="43f17-130">Example - static field and method</span></span>

<span data-ttu-id="43f17-131">此示例读取新员工的姓名和 ID，员工计数器按 1 递增，并显示新员工信息和新员工人数。</span><span class="sxs-lookup"><span data-stu-id="43f17-131">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="43f17-132">此程序从键盘读取员工的当前人数。</span><span class="sxs-lookup"><span data-stu-id="43f17-132">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="43f17-133">示例 - 静态初始化</span><span class="sxs-lookup"><span data-stu-id="43f17-133">Example - static initialization</span></span>

<span data-ttu-id="43f17-134">此示例演示了如何使用尚未声明的 `static` 字段来初始化另一个 `static` 字段。</span><span class="sxs-lookup"><span data-stu-id="43f17-134">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="43f17-135">在向 `static` 字段显式赋值之后才会定义结果。</span><span class="sxs-lookup"><span data-stu-id="43f17-135">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="43f17-136">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="43f17-136">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="43f17-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="43f17-137">See also</span></span>

- [<span data-ttu-id="43f17-138">C# 参考</span><span class="sxs-lookup"><span data-stu-id="43f17-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43f17-139">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="43f17-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43f17-140">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="43f17-140">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="43f17-141">修饰符</span><span class="sxs-lookup"><span data-stu-id="43f17-141">Modifiers</span></span>](index.md)
- [<span data-ttu-id="43f17-142">using static 指令</span><span class="sxs-lookup"><span data-stu-id="43f17-142">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="43f17-143">静态类和静态类成员</span><span class="sxs-lookup"><span data-stu-id="43f17-143">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
