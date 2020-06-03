---
title: new 修饰符 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 529d77b0a66a8a3cedfe7a400af0fb34dd653322
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795165"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="05451-102">new 修饰符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="05451-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="05451-103">在用作声明修饰符时，`new` 关键字可以显式隐藏从基类继承的成员。</span><span class="sxs-lookup"><span data-stu-id="05451-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="05451-104">隐藏继承的成员时，该成员的派生版本将替换基类版本。</span><span class="sxs-lookup"><span data-stu-id="05451-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="05451-105">虽然可以不使用 `new` 修饰符来隐藏成员，但将收到编译器警告。</span><span class="sxs-lookup"><span data-stu-id="05451-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="05451-106">如果使用 `new` 来显式隐藏成员，将禁止此警告。</span><span class="sxs-lookup"><span data-stu-id="05451-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="05451-107">`new` 关键字还可用于[创建类型的实例](../operators/new-operator.md)或用作[泛型类型约束](./new-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="05451-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="05451-108">若要隐藏继承的成员，请使用相同名称在派生类中声明该成员，并使用 `new` 修饰符对其进行修饰。</span><span class="sxs-lookup"><span data-stu-id="05451-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="05451-109">例如：</span><span class="sxs-lookup"><span data-stu-id="05451-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="05451-110">在此示例中，使用 `DerivedC.Invoke` 隐藏了 `BaseC.Invoke`。</span><span class="sxs-lookup"><span data-stu-id="05451-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="05451-111">字段 `x` 不受影响，因为未使用类似名称将其隐藏。</span><span class="sxs-lookup"><span data-stu-id="05451-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="05451-112">通过继承隐藏名称采用下列形式之一：</span><span class="sxs-lookup"><span data-stu-id="05451-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="05451-113">通常，在类或结构中引入的常数、字段、属性或类型会隐藏与其共享名称的所有基类成员。</span><span class="sxs-lookup"><span data-stu-id="05451-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="05451-114">有三种特殊情况。</span><span class="sxs-lookup"><span data-stu-id="05451-114">There are special cases.</span></span> <span data-ttu-id="05451-115">例如，如果将名称为 `N` 的新字段声明为不可调用的类型，并且基类型将 `N` 声明为一种方法，则新字段在调用语法中不会隐藏基声明。</span><span class="sxs-lookup"><span data-stu-id="05451-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="05451-116">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[成员查找](~/_csharplang/spec/expressions.md#member-lookup)部分。</span><span class="sxs-lookup"><span data-stu-id="05451-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="05451-117">类或结构中引入的方法会隐藏基类中共享该名称的属性、字段和类型。</span><span class="sxs-lookup"><span data-stu-id="05451-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="05451-118">它还会隐藏具有相同签名的所有基类方法。</span><span class="sxs-lookup"><span data-stu-id="05451-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="05451-119">类或结构中引入的索引器会隐藏具有相同签名的所有基类索引器。</span><span class="sxs-lookup"><span data-stu-id="05451-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="05451-120">对同一成员同时使用 `new` 和 [override](override.md) 是错误的做法，因为这两个修饰符的含义互斥。</span><span class="sxs-lookup"><span data-stu-id="05451-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="05451-121">`new` 修饰符会用同样的名称创建一个新成员并使原始成员变为隐藏。</span><span class="sxs-lookup"><span data-stu-id="05451-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="05451-122">`override` 修饰符会扩展继承成员的实现。</span><span class="sxs-lookup"><span data-stu-id="05451-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="05451-123">在不隐藏继承成员的声明中使用 `new` 修饰符将会生成警告。</span><span class="sxs-lookup"><span data-stu-id="05451-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="05451-124">示例</span><span class="sxs-lookup"><span data-stu-id="05451-124">Example</span></span>

<span data-ttu-id="05451-125">在此示例中，基类 `BaseC` 和派生类 `DerivedC` 使用相同的字段名 `x`，从而隐藏了继承字段的值。</span><span class="sxs-lookup"><span data-stu-id="05451-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="05451-126">此示例演示 `new` 修饰符的用法。</span><span class="sxs-lookup"><span data-stu-id="05451-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="05451-127">另外还演示了如何使用完全限定名访问基类的隐藏成员。</span><span class="sxs-lookup"><span data-stu-id="05451-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="05451-128">示例</span><span class="sxs-lookup"><span data-stu-id="05451-128">Example</span></span>

<span data-ttu-id="05451-129">在此示例中，嵌套类隐藏了基类中同名的类。</span><span class="sxs-lookup"><span data-stu-id="05451-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="05451-130">此示例演示如何使用 `new` 修饰符来消除警告消息，以及如何使用完全限定名来访问隐藏的类成员。</span><span class="sxs-lookup"><span data-stu-id="05451-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="05451-131">如果移除 `new` 修饰符，程序仍将编译和运行，但你会收到以下警告：</span><span class="sxs-lookup"><span data-stu-id="05451-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="05451-132">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="05451-132">C# language specification</span></span>

<span data-ttu-id="05451-133">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [new 修饰符](~/_csharplang/spec/classes.md#the-new-modifier)部分。</span><span class="sxs-lookup"><span data-stu-id="05451-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05451-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="05451-134">See also</span></span>

- [<span data-ttu-id="05451-135">C# 参考</span><span class="sxs-lookup"><span data-stu-id="05451-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05451-136">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="05451-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05451-137">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="05451-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="05451-138">修饰符</span><span class="sxs-lookup"><span data-stu-id="05451-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="05451-139">使用 Override 和 New 关键字进行版本控制</span><span class="sxs-lookup"><span data-stu-id="05451-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="05451-140">了解何时使用 Override 和 New 关键字</span><span class="sxs-lookup"><span data-stu-id="05451-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
