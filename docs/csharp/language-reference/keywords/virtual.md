---
description: virtual - C# 参考
title: virtual - C# 参考
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 67bdfcf27bb108ca85e94ba7fdce208e4cd83b80
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141720"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="f6439-103">virtual（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f6439-103">virtual (C# Reference)</span></span>

<span data-ttu-id="f6439-104">`virtual` 关键字用于修改方法、属性、索引器或事件声明，并使它们可以在派生类中被重写。</span><span class="sxs-lookup"><span data-stu-id="f6439-104">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="f6439-105">例如，此方法可被任何继承它的类替代：</span><span class="sxs-lookup"><span data-stu-id="f6439-105">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="f6439-106">虚拟成员的实现可由派生类中的[替代成员](override.md)更改。</span><span class="sxs-lookup"><span data-stu-id="f6439-106">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="f6439-107">有关如何使用 `virtual` 关键字的详细信息，请参阅[使用 Override 和 New 关键字进行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)和[了解何时使用 Override 和 New 关键字](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="f6439-107">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="f6439-108">备注</span><span class="sxs-lookup"><span data-stu-id="f6439-108">Remarks</span></span>

<span data-ttu-id="f6439-109">调用虚拟方法时，将为替代的成员检查该对象的运行时类型。</span><span class="sxs-lookup"><span data-stu-id="f6439-109">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="f6439-110">将调用大部分派生类中的该替代成员，如果没有派生类替代该成员，则它可能是原始成员。</span><span class="sxs-lookup"><span data-stu-id="f6439-110">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="f6439-111">默认情况下，方法是非虚拟的。</span><span class="sxs-lookup"><span data-stu-id="f6439-111">By default, methods are non-virtual.</span></span> <span data-ttu-id="f6439-112">不能替代非虚方法。</span><span class="sxs-lookup"><span data-stu-id="f6439-112">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="f6439-113">`virtual` 修饰符不能与 `static`、`abstract``private` 或 `override` 修饰符一起使用。</span><span class="sxs-lookup"><span data-stu-id="f6439-113">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="f6439-114">以下示例显示了虚拟属性：</span><span class="sxs-lookup"><span data-stu-id="f6439-114">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="f6439-115">除声明和调用语法不同外，虚拟属性的行为与虚拟方法相似。</span><span class="sxs-lookup"><span data-stu-id="f6439-115">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="f6439-116">在静态属性上使用 `virtual` 修饰符是错误的。</span><span class="sxs-lookup"><span data-stu-id="f6439-116">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="f6439-117">通过包括使用 `override` 修饰符的属性声明，可在派生类中替代虚拟继承属性。</span><span class="sxs-lookup"><span data-stu-id="f6439-117">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="f6439-118">示例</span><span class="sxs-lookup"><span data-stu-id="f6439-118">Example</span></span>

<span data-ttu-id="f6439-119">在该示例中，`Shape` 类包含 `x`、`y` 两个坐标和 `Area()` 虚拟方法。</span><span class="sxs-lookup"><span data-stu-id="f6439-119">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="f6439-120">不同的形状类（如 `Circle`、`Cylinder` 和 `Sphere`）继承 `Shape` 类，并为每个图形计算表面积。</span><span class="sxs-lookup"><span data-stu-id="f6439-120">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="f6439-121">每个派生类都有各自的 `Area()` 替代实现。</span><span class="sxs-lookup"><span data-stu-id="f6439-121">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="f6439-122">请注意，继承的类 `Circle``Sphere` 和 `Cylinder` 均使用初始化基类的构造函数，如下面的声明中所示。</span><span class="sxs-lookup"><span data-stu-id="f6439-122">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="f6439-123">根据与方法关联的对象，下面的程序通过调用 `Area()` 方法的相应实现来计算并显示每个对象的相应区域。</span><span class="sxs-lookup"><span data-stu-id="f6439-123">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="f6439-124">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="f6439-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6439-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="f6439-125">See also</span></span>

- [<span data-ttu-id="f6439-126">多态性</span><span class="sxs-lookup"><span data-stu-id="f6439-126">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="f6439-127">abstract</span><span class="sxs-lookup"><span data-stu-id="f6439-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="f6439-128">override</span><span class="sxs-lookup"><span data-stu-id="f6439-128">override</span></span>](override.md)
- [<span data-ttu-id="f6439-129">new（修饰符）</span><span class="sxs-lookup"><span data-stu-id="f6439-129">new (modifier)</span></span>](new-modifier.md)
