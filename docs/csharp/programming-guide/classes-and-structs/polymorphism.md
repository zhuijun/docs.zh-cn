---
title: 多形性 - C# 编程指南
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 65f5c882ec4d7f8cbcc7ec7bf535091febfba64d
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662649"
---
# <a name="polymorphism-c-programming-guide"></a><span data-ttu-id="5f5a8-102">多态性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="5f5a8-102">Polymorphism (C# Programming Guide)</span></span>

<span data-ttu-id="5f5a8-103">多态性常被视为自封装和继承之后，面向对象的编程的第三个支柱。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-103">Polymorphism is often referred to as the third pillar of object-oriented programming, after encapsulation and inheritance.</span></span> <span data-ttu-id="5f5a8-104">Polymorphism（多态性）是一个希腊词，指“多种形态”，多态性具有两个截然不同的方面：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-104">Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:</span></span>
  
- <span data-ttu-id="5f5a8-105">在运行时，在方法参数和集合或数组等位置，派生类的对象可以作为基类的对象处理。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-105">At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays.</span></span> <span data-ttu-id="5f5a8-106">在出现此多形性时，该对象的声明类型不再与运行时类型相同。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-106">When this polymorphism occurs, the object's declared type is no longer identical to its run-time type.</span></span>
- <span data-ttu-id="5f5a8-107">基类可以定义并实现[虚](../../language-reference/keywords/virtual.md)方法，派生类可以[重写](../../language-reference/keywords/override.md)这些方法，即派生类提供自己的定义和实现  。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-107">Base classes may define and implement [virtual](../../language-reference/keywords/virtual.md) *methods*, and derived classes can [override](../../language-reference/keywords/override.md) them, which means they provide their own definition and implementation.</span></span> <span data-ttu-id="5f5a8-108">在运行时，客户端代码调用该方法，CLR 查找对象的运行时类型，并调用虚方法的重写方法。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-108">At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method.</span></span> <span data-ttu-id="5f5a8-109">你可以在源代码中调用基类的方法，执行该方法的派生类版本。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-109">In your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.</span></span>

<span data-ttu-id="5f5a8-110">虚方法允许你以统一方式处理多组相关的对象。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-110">Virtual methods enable you to work with groups of related objects in a uniform way.</span></span> <span data-ttu-id="5f5a8-111">例如，假定你有一个绘图应用程序，允许用户在绘图图面上创建各种形状。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-111">For example, suppose you have a drawing application that enables a user to create various kinds of shapes on a drawing surface.</span></span> <span data-ttu-id="5f5a8-112">你在编译时不知道用户将创建哪些特定类型的形状。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-112">You do not know at compile time which specific types of shapes the user will create.</span></span> <span data-ttu-id="5f5a8-113">但应用程序必须跟踪创建的所有类型的形状，并且必须更新这些形状以响应用户鼠标操作。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-113">However, the application has to keep track of all the various types of shapes that are created, and it has to update them in response to user mouse actions.</span></span> <span data-ttu-id="5f5a8-114">你可以使用多态性通过两个基本步骤解决这一问题：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-114">You can use polymorphism to solve this problem in two basic steps:</span></span>

1. <span data-ttu-id="5f5a8-115">创建一个类层次结构，其中每个特定形状类均派生自一个公共基类。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-115">Create a class hierarchy in which each specific shape class derives from a common base class.</span></span>
1. <span data-ttu-id="5f5a8-116">使用虚方法通过对基类方法的单个调用来调用任何派生类上的相应方法。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-116">Use a virtual method to invoke the appropriate method on any derived class through a single call to the base class method.</span></span>

<span data-ttu-id="5f5a8-117">首先，创建一个名为 `Rectangle``Shape` 的基类，并创建一些派生类，例如 `Triangle``Circle`、 和 。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-117">First, create a base class called `Shape`, and derived classes such as `Rectangle`, `Circle`, and `Triangle`.</span></span> <span data-ttu-id="5f5a8-118">为 `Shape` 类提供一个名为 `Draw` 的虚拟方法，并在每个派生类中重写该方法以绘制该类表示的特定形状。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-118">Give the `Shape` class a virtual method called `Draw`, and override it in each derived class to draw the particular shape that the class represents.</span></span> <span data-ttu-id="5f5a8-119">创建 `List<Shape>` 对象，并向其添加 `Circle`、`Triangle` 和 `Rectangle`。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-119">Create a `List<Shape>` object and add a `Circle`, `Triangle`, and `Rectangle` to it.</span></span>

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

<span data-ttu-id="5f5a8-120">若要更新绘图图面，请使用 [foreach](../../language-reference/keywords/foreach-in.md) 循环对该列表进行循环访问，并对其中的每个 `Shape` 对象调用 `Draw` 方法。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-120">To update the drawing surface, use a [foreach](../../language-reference/keywords/foreach-in.md) loop to iterate through the list and call the `Draw` method on each `Shape` object in the list.</span></span> <span data-ttu-id="5f5a8-121">虽然列表中的每个对象都具有声明类型 `Shape`，但调用的将是运行时类型（该方法在每个派生类中的重写版本）。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-121">Even though each object in the list has a declared type of `Shape`, it's the run-time type (the overridden version of the method in each derived class) that will be invoked.</span></span>

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

<span data-ttu-id="5f5a8-122">在 C# 中，每个类型都是多态的，因为包括用户定义类型在内的所有类型都继承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-122">In C#, every type is polymorphic because all types, including user-defined types, inherit from <xref:System.Object>.</span></span>  

## <a name="polymorphism-overview"></a><span data-ttu-id="5f5a8-123">多形性概述</span><span class="sxs-lookup"><span data-stu-id="5f5a8-123">Polymorphism overview</span></span>

### <a name="virtual-members"></a><span data-ttu-id="5f5a8-124">虚拟成员</span><span class="sxs-lookup"><span data-stu-id="5f5a8-124">Virtual members</span></span>

<span data-ttu-id="5f5a8-125">当派生类从基类继承时，它会获得基类的所有方法、字段、属性和事件。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-125">When a derived class inherits from a base class, it gains all the methods, fields, properties, and events of the base class.</span></span> <span data-ttu-id="5f5a8-126">派生类的设计器可以针对虚拟方法的行为做出不同的选择：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-126">The designer of the derived class can different choices for the behavior of virtual methods:</span></span>

- <span data-ttu-id="5f5a8-127">派生类可以重写基类中的虚拟成员，并定义新行为。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-127">The derived class may override virtual members in the base class, defining new behavior.</span></span>
- <span data-ttu-id="5f5a8-128">派生类继承最接近的基类方法而不重写方法，同时保留现有的行为，但允许进一步派生的类重写方法。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-128">The derived class inherit the closest base class method without overriding it, preserving the existing behavior but enabling further derived classes to override the method.</span></span>
- <span data-ttu-id="5f5a8-129">派生类可以定义隐藏基类实现的成员的新非虚实现。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-129">The derived class may define new non-virtual implementation of those members that hide the base class implementations.</span></span>

<span data-ttu-id="5f5a8-130">仅当基类成员声明为 [virtual](../../language-reference/keywords/virtual.md) 或 [abstract](../../language-reference/keywords/abstract.md) 时，派生类才能重写基类成员。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-130">A derived class can override a base class member only if the base class member is declared as [virtual](../../language-reference/keywords/virtual.md) or [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="5f5a8-131">派生成员必须使用 [override](../../language-reference/keywords/override.md) 关键字显式指示该方法将参与虚调用。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-131">The derived member must use the [override](../../language-reference/keywords/override.md) keyword to explicitly indicate that the method is intended to participate in virtual invocation.</span></span> <span data-ttu-id="5f5a8-132">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-132">The following code provides an example:</span></span>

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

<span data-ttu-id="5f5a8-133">字段不能是虚拟的，只有方法、属性、事件和索引器才可以是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-133">Fields cannot be virtual; only methods, properties, events, and indexers can be virtual.</span></span> <span data-ttu-id="5f5a8-134">当派生类重写某个虚拟成员时，即使该派生类的实例被当作基类的实例访问，也会调用该成员。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-134">When a derived class overrides a virtual member, that member is called even when an instance of that class is being accessed as an instance of the base class.</span></span> <span data-ttu-id="5f5a8-135">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-135">The following code provides an example:</span></span>

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#SnippetTestVirtualMethods)]

<span data-ttu-id="5f5a8-136">虚方法和属性允许派生类扩展基类，而无需使用方法的基类实现。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-136">Virtual methods and properties enable derived classes to extend a base class without needing to use the base class implementation of a method.</span></span> <span data-ttu-id="5f5a8-137">有关详细信息，请参阅[使用 Override 和 New 关键字进行版本控制](./versioning-with-the-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-137">For more information, see [Versioning with the Override and New Keywords](./versioning-with-the-override-and-new-keywords.md).</span></span> <span data-ttu-id="5f5a8-138">接口提供另一种方式来定义将实现留给派生类的方法或方法集。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-138">An interface provides another way to define a method or set of methods whose implementation is left to derived classes.</span></span> <span data-ttu-id="5f5a8-139">有关详细信息，请参阅[接口](../interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-139">For more information, see [Interfaces](../interfaces/index.md).</span></span>

### <a name="hide-base-class-members-with-new-members"></a><span data-ttu-id="5f5a8-140">使用新成员隐藏基类成员</span><span class="sxs-lookup"><span data-stu-id="5f5a8-140">Hide base class members with new members</span></span>

<span data-ttu-id="5f5a8-141">如果希望派生类具有与基类中的成员同名的成员，则可以使用 [new](../../language-reference/keywords/new-modifier.md) 关键字隐藏基类成员。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-141">If you want your derived class to have a member with the same name as a member in a base class, you can use the [new](../../language-reference/keywords/new-modifier.md) keyword to hide the base class member.</span></span> <span data-ttu-id="5f5a8-142">`new` 关键字放置在要替换的类成员的返回类型之前。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-142">The `new` keyword is put before the return type of a class member that is being replaced.</span></span> <span data-ttu-id="5f5a8-143">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-143">The following code provides an example:</span></span>

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

<span data-ttu-id="5f5a8-144">通过将派生类的实例强制转换为基类的实例，可以从客户端代码访问隐藏的基类成员。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-144">Hidden base class members may be accessed from client code by casting the instance of the derived class to an instance of the base class.</span></span> <span data-ttu-id="5f5a8-145">例如：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-145">For example:</span></span>

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a><span data-ttu-id="5f5a8-146">阻止派生类重写虚拟成员</span><span class="sxs-lookup"><span data-stu-id="5f5a8-146">Prevent derived classes from overriding virtual members</span></span>  

<span data-ttu-id="5f5a8-147">无论在虚拟成员和最初声明虚拟成员的类之间已声明了多少个类，虚拟成员都是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-147">Virtual members remain virtual, regardless of how many classes have been declared between the virtual member and the class that originally declared it.</span></span> <span data-ttu-id="5f5a8-148">如果类 `A` 声明了一个虚拟成员，类 `B` 从 `A` 派生，类 `C` 从类 `B` 派生，则不管类 `B` 是否为虚拟成员声明了重写，类 `C` 都会继承该虚拟成员，并可以重写它。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-148">If class `A` declares a virtual member, and class `B` derives from `A`, and class `C` derives from `B`, class `C` inherits the virtual member, and may override it, regardless of whether class `B` declared an override for that member.</span></span> <span data-ttu-id="5f5a8-149">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-149">The following code provides an example:</span></span>

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

<span data-ttu-id="5f5a8-150">派生类可以通过将重写声明为 [sealed](../../language-reference/keywords/sealed.md) 来停止虚拟继承。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-150">A derived class can stop virtual inheritance by declaring an override as [sealed](../../language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="5f5a8-151">停止继承需要在类成员声明中的 `override` 关键字前面放置 `sealed` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-151">Stopping inheritance requires putting the `sealed` keyword before the `override` keyword in the class member declaration.</span></span> <span data-ttu-id="5f5a8-152">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-152">The following code provides an example:</span></span>

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

<span data-ttu-id="5f5a8-153">在上一个示例中，方法 `DoWork` 对从 `C` 派生的任何类都不再是虚拟方法。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-153">In the previous example, the method `DoWork` is no longer virtual to any class derived from `C`.</span></span> <span data-ttu-id="5f5a8-154">即使它们转换为类型 `B` 或类型 `A`，它对于 `C` 的实例仍然是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-154">It's still virtual for instances of `C`, even if they're cast to type `B` or type `A`.</span></span> <span data-ttu-id="5f5a8-155">通过使用 `new` 关键字，密封的方法可以由派生类替换，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-155">Sealed methods can be replaced by derived classes by using the `new` keyword, as the following example shows:</span></span>

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

<span data-ttu-id="5f5a8-156">在此情况下，如果在 `D` 中使用类型为 `D` 的变量调用 `DoWork`，被调用的将是新的 `DoWork`。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-156">In this case, if `DoWork` is called on `D` using a variable of type `D`, the new `DoWork` is called.</span></span> <span data-ttu-id="5f5a8-157">如果使用类型为 `C`、`B` 或 `A` 的变量访问 `D` 的实例，对 `DoWork` 的调用将遵循虚拟继承的规则，即把这些调用传送到类 `C` 的 `DoWork` 实现。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-157">If a variable of type `C`, `B`, or `A` is used to access an instance of `D`, a call to `DoWork` will follow the rules of virtual inheritance, routing those calls to the implementation of `DoWork` on class `C`.</span></span>

### <a name="access-base-class-virtual-members-from-derived-classes"></a><span data-ttu-id="5f5a8-158">从派生类访问基类虚拟成员</span><span class="sxs-lookup"><span data-stu-id="5f5a8-158">Access base class virtual members from derived classes</span></span>

<span data-ttu-id="5f5a8-159">已替换或重写某个方法或属性的派生类仍然可以使用 `base` 关键字访问基类的该方法或属性。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-159">A derived class that has replaced or overridden a method or property can still access the method or property on the base class using the `base` keyword.</span></span> <span data-ttu-id="5f5a8-160">以下代码提供了一个示例：</span><span class="sxs-lookup"><span data-stu-id="5f5a8-160">The following code provides an example:</span></span>

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

<span data-ttu-id="5f5a8-161">有关详细信息，请参阅 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-161">For more information, see [base](../../language-reference/keywords/base.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a8-162">建议虚拟成员在它们自己的实现中使用 `base` 来调用该成员的基类实现。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-162">It is recommended that virtual members use `base` to call the base class implementation of that member in their own implementation.</span></span> <span data-ttu-id="5f5a8-163">允许基类行为发生使得派生类能够集中精力实现特定于派生类的行为。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-163">Letting the base class behavior occur enables the derived class to concentrate on implementing behavior specific to the derived class.</span></span> <span data-ttu-id="5f5a8-164">未调用基类实现时，由派生类负责使它们的行为与基类的行为兼容。</span><span class="sxs-lookup"><span data-stu-id="5f5a8-164">If the base class implementation is not called, it is up to the derived class to make their behavior compatible with the behavior of the base class.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5f5a8-165">本节内容</span><span class="sxs-lookup"><span data-stu-id="5f5a8-165">In this section</span></span>

- [<span data-ttu-id="5f5a8-166">使用 Override 和 New 关键字进行版本控制</span><span class="sxs-lookup"><span data-stu-id="5f5a8-166">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="5f5a8-167">了解何时使用 Override 和 New 关键字</span><span class="sxs-lookup"><span data-stu-id="5f5a8-167">Knowing When to Use Override and New Keywords</span></span>](./knowing-when-to-use-override-and-new-keywords.md)
- [<span data-ttu-id="5f5a8-168">如何替代 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="5f5a8-168">How to override the ToString method</span></span>](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a><span data-ttu-id="5f5a8-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f5a8-169">See also</span></span>

- [<span data-ttu-id="5f5a8-170">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="5f5a8-170">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5f5a8-171">继承</span><span class="sxs-lookup"><span data-stu-id="5f5a8-171">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="5f5a8-172">抽象类、密封类及类成员</span><span class="sxs-lookup"><span data-stu-id="5f5a8-172">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="5f5a8-173">方法</span><span class="sxs-lookup"><span data-stu-id="5f5a8-173">Methods</span></span>](./methods.md)
- [<span data-ttu-id="5f5a8-174">事件</span><span class="sxs-lookup"><span data-stu-id="5f5a8-174">Events</span></span>](../events/index.md)
- [<span data-ttu-id="5f5a8-175">属性</span><span class="sxs-lookup"><span data-stu-id="5f5a8-175">Properties</span></span>](./properties.md)
- [<span data-ttu-id="5f5a8-176">索引器</span><span class="sxs-lookup"><span data-stu-id="5f5a8-176">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="5f5a8-177">类型</span><span class="sxs-lookup"><span data-stu-id="5f5a8-177">Types</span></span>](../types/index.md)
