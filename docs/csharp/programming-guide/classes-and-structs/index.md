---
title: 类和结构 - C# 编程指南
description: 介绍了如何在 C# 中使用类和结构。
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 55fc2cdda5b79847266a03800e6c31e6e78a55f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203990"
---
# <a name="classes-and-structs-c-programming-guide"></a><span data-ttu-id="b1f5b-103">类和结构（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="b1f5b-103">Classes and structs (C# programming guide)</span></span>

<span data-ttu-id="b1f5b-104">类和结构是 .NET 通用类型系统的两种基本构造。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-104">Classes and structs are two of the basic constructs of the common type system in .NET.</span></span> <span data-ttu-id="b1f5b-105">每种本质上都是一种数据结构，其中封装了同属一个逻辑单元的一组数据和行为。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-105">Each is essentially a data structure that encapsulates a set of data and behaviors that belong together as a logical unit.</span></span> <span data-ttu-id="b1f5b-106">数据和行为是类或结构的*成员*，包括方法、属性和事件等（此主题稍后将具体列举）。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-106">The data and behaviors are the *members* of the class or struct, and they include its methods, properties, and events, and so on, as listed later in this topic.</span></span>  
  
 <span data-ttu-id="b1f5b-107">类或结构声明类似于一张蓝图，用于在运行时创建实例或对象。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-107">A class or struct declaration is like a blueprint that is used to create instances or objects at run time.</span></span> <span data-ttu-id="b1f5b-108">如果定义 `Person` 类或结构，那么 `Person` 就是类型名称。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-108">If you define a class or struct called `Person`, `Person` is the name of the type.</span></span> <span data-ttu-id="b1f5b-109">如果声明和初始化 `Person` 类型的变量 `p`，那么 `p` 就是所谓的 `Person` 对象或实例。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-109">If you declare and initialize a variable `p` of type `Person`, `p` is said to be an object or instance of `Person`.</span></span> <span data-ttu-id="b1f5b-110">可以创建同一 `Person` 类型的多个实例，每个实例都可以有不同的属性和字段值。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-110">Multiple instances of the same `Person` type can be created, and each instance can have different values in its properties and fields.</span></span>  
  
 <span data-ttu-id="b1f5b-111">类是引用类型。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-111">A class is a reference type.</span></span> <span data-ttu-id="b1f5b-112">创建类的对象后，向其分配对象的变量仅保留对相应内存的引用。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-112">When an object of the class is created, the variable to which the object is assigned holds only a reference to that memory.</span></span> <span data-ttu-id="b1f5b-113">将对象引用分配给新变量后，新变量会引用原始对象。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-113">When the object reference is assigned to a new variable, the new variable refers to the original object.</span></span> <span data-ttu-id="b1f5b-114">通过一个变量所做的更改将反映在另一个变量中，因为它们引用相同的数据。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-114">Changes made through one variable are reflected in the other variable because they both refer to the same data.</span></span>  
  
 <span data-ttu-id="b1f5b-115">结构是值类型。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-115">A struct is a value type.</span></span> <span data-ttu-id="b1f5b-116">创建结构时，向其分配结构的变量保留结构的实际数据。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-116">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="b1f5b-117">将结构分配给新变量时，会复制结构。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-117">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="b1f5b-118">因此，新变量和原始变量包含相同数据的副本（共两个）。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-118">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="b1f5b-119">对一个副本所做的更改不会影响另一个副本。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-119">Changes made to one copy do not affect the other copy.</span></span>  
  
 <span data-ttu-id="b1f5b-120">一般来说，类用于对更复杂的行为或应在类对象创建后进行修改的数据建模。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-120">In general, classes are used to model more complex behavior, or data that is intended to be modified after a class object is created.</span></span> <span data-ttu-id="b1f5b-121">结构最适用于所含大部分数据不得在结构创建后进行修改的小型数据结构。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-121">Structs are best suited for small data structures that contain primarily data that is not intended to be modified after the struct is created.</span></span>  
  
 <span data-ttu-id="b1f5b-122">有关详细信息，请参阅[类](./classes.md)、[对象](./objects.md)和[结构类型](../../language-reference/builtin-types/struct.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-122">For more information, see [Classes](./classes.md), [Objects](./objects.md), and [Structure types](../../language-reference/builtin-types/struct.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f5b-123">示例</span><span class="sxs-lookup"><span data-stu-id="b1f5b-123">Example</span></span>  

 <span data-ttu-id="b1f5b-124">在以下示例中，`ProgrammingGuide` 命名空间中的 `CustomClass` 有以下三个成员：实例构造函数、`Number` 属性和 `Multiply` 方法。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-124">In the following example, `CustomClass` in the `ProgrammingGuide` namespace has three members: an instance constructor, a property named `Number`, and a method named `Multiply`.</span></span> <span data-ttu-id="b1f5b-125">`Program` 类中的 `Main` 方法创建 `CustomClass` 的实例（对象），此对象的方法和属性可使用点表示法进行访问。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-125">The `Main` method in the `Program` class creates an instance (object) of `CustomClass`, and the object's method and property are accessed by using dot notation.</span></span>
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a><span data-ttu-id="b1f5b-126">封装</span><span class="sxs-lookup"><span data-stu-id="b1f5b-126">Encapsulation</span></span>  

 <span data-ttu-id="b1f5b-127">*封装*有时称为面向对象的编程的第一支柱或原则。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-127">*Encapsulation* is sometimes referred to as the first pillar or principle of object-oriented programming.</span></span> <span data-ttu-id="b1f5b-128">根据封装原则，类或结构可以指定自己的每个成员对外部代码的可访问性。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-128">According to the principle of encapsulation, a class or struct can specify how accessible each of its members is to code outside of the class or struct.</span></span> <span data-ttu-id="b1f5b-129">可以隐藏不得在类或程序集外部使用的方法和变量，以限制编码错误或恶意攻击发生的可能性。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-129">Methods and variables that are not intended to be used from outside of the class or assembly can be hidden to limit the potential for coding errors or malicious exploits.</span></span>  
  
 <span data-ttu-id="b1f5b-130">有关类的详细信息，请参阅[类](./classes.md)和[对象](./objects.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-130">For more information about classes, see [Classes](./classes.md) and [Objects](./objects.md).</span></span>  
  
### <a name="members"></a><span data-ttu-id="b1f5b-131">成员</span><span class="sxs-lookup"><span data-stu-id="b1f5b-131">Members</span></span>  

 <span data-ttu-id="b1f5b-132">所有方法、字段、常量、属性和事件都必须在类型中进行声明；这些被称为类型的*成员*。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-132">All methods, fields, constants, properties, and events must be declared within a type; these are called the *members* of the type.</span></span> <span data-ttu-id="b1f5b-133">C# 没有全局变量或方法，这一点其他某些语言不同。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-133">In C#, there are no global variables or methods as there are in some other languages.</span></span> <span data-ttu-id="b1f5b-134">即使是程序的入口点 `Main` 方法，也必须在类或结构中进行声明。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-134">Even a program's entry point, the `Main` method, must be declared within a class or struct.</span></span> <span data-ttu-id="b1f5b-135">下面列出了所有可以在类或结构中声明的各种成员。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-135">The following list includes all the various kinds of members that may be declared in a class or struct.</span></span>  
  
- [<span data-ttu-id="b1f5b-136">字段</span><span class="sxs-lookup"><span data-stu-id="b1f5b-136">Fields</span></span>](./fields.md)  
  
- [<span data-ttu-id="b1f5b-137">常量</span><span class="sxs-lookup"><span data-stu-id="b1f5b-137">Constants</span></span>](./constants.md)  
  
- [<span data-ttu-id="b1f5b-138">属性</span><span class="sxs-lookup"><span data-stu-id="b1f5b-138">Properties</span></span>](./properties.md)  
  
- [<span data-ttu-id="b1f5b-139">方法</span><span class="sxs-lookup"><span data-stu-id="b1f5b-139">Methods</span></span>](./methods.md)  
  
- [<span data-ttu-id="b1f5b-140">构造函数</span><span class="sxs-lookup"><span data-stu-id="b1f5b-140">Constructors</span></span>](./constructors.md)  
  
- [<span data-ttu-id="b1f5b-141">事件</span><span class="sxs-lookup"><span data-stu-id="b1f5b-141">Events</span></span>](../events/index.md)  
  
- [<span data-ttu-id="b1f5b-142">终结器</span><span class="sxs-lookup"><span data-stu-id="b1f5b-142">Finalizers</span></span>](./destructors.md)  
  
- [<span data-ttu-id="b1f5b-143">索引器</span><span class="sxs-lookup"><span data-stu-id="b1f5b-143">Indexers</span></span>](../indexers/index.md)  
  
- [<span data-ttu-id="b1f5b-144">运算符</span><span class="sxs-lookup"><span data-stu-id="b1f5b-144">Operators</span></span>](../../language-reference/operators/index.md)  
  
- [<span data-ttu-id="b1f5b-145">嵌套类型</span><span class="sxs-lookup"><span data-stu-id="b1f5b-145">Nested Types</span></span>](./nested-types.md)  
  
### <a name="accessibility"></a><span data-ttu-id="b1f5b-146">可访问性</span><span class="sxs-lookup"><span data-stu-id="b1f5b-146">Accessibility</span></span>  

 <span data-ttu-id="b1f5b-147">一些方法和属性可供类或结构外部的代码（称为“*客户端代码*”）调用或访问。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-147">Some methods and properties are meant to be called or accessed from code outside your class or struct, known as *client code*.</span></span> <span data-ttu-id="b1f5b-148">另一些方法和属性只能在类或结构本身中使用。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-148">Other methods and properties might be only for use in the class or struct itself.</span></span> <span data-ttu-id="b1f5b-149">请务必限制代码的可访问性，仅供预期的客户端代码进行访问。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-149">It is important to limit the accessibility of your code so that only the intended client code can reach it.</span></span> <span data-ttu-id="b1f5b-150">使用访问修饰符 [public](../../language-reference/keywords/public.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md)、[private](../../language-reference/keywords/private.md) 和 [private protected](../../language-reference/keywords/private-protected.md) 可指定类型及其成员对客户端代码的可访问性。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-150">You specify how accessible your types and their members are to client code by using the access modifiers [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) and [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="b1f5b-151">可访问性的默认值为 `private`。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-151">The default accessibility is `private`.</span></span> <span data-ttu-id="b1f5b-152">有关详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-152">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
### <a name="inheritance"></a><span data-ttu-id="b1f5b-153">继承</span><span class="sxs-lookup"><span data-stu-id="b1f5b-153">Inheritance</span></span>  

 <span data-ttu-id="b1f5b-154">类（而非结构）支持继承的概念。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-154">Classes (but not structs) support the concept of inheritance.</span></span> <span data-ttu-id="b1f5b-155">派生自另一个类（基类）的类自动包含基类的所有公共、受保护和内部成员（其构造函数和终结器除外）。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-155">A class that derives from another class (the *base class*) automatically contains all the public, protected, and internal members of the base class except its constructors and finalizers.</span></span> <span data-ttu-id="b1f5b-156">有关详细信息，请参阅[继承](./inheritance.md)和[多态性](./polymorphism.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-156">For more information, see [Inheritance](./inheritance.md) and [Polymorphism](./polymorphism.md).</span></span>  
  
 <span data-ttu-id="b1f5b-157">可以将类声明为 [abstract](../../language-reference/keywords/abstract.md)，即一个或多个方法没有实现代码。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-157">Classes may be declared as [abstract](../../language-reference/keywords/abstract.md), which means that one or more of their methods have no implementation.</span></span> <span data-ttu-id="b1f5b-158">尽管抽象类无法直接实例化，但可以作为提供缺少实现代码的其他类的基类。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-158">Although abstract classes cannot be instantiated directly, they can serve as base classes for other classes that provide the missing implementation.</span></span> <span data-ttu-id="b1f5b-159">类还可以声明为 [sealed](../../language-reference/keywords/sealed.md)，以阻止其他类继承。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-159">Classes can also be declared as [sealed](../../language-reference/keywords/sealed.md) to prevent other classes from inheriting from them.</span></span> <span data-ttu-id="b1f5b-160">有关详细信息，请参阅[抽象类、密封类及类成员](./abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-160">For more information, see [Abstract and Sealed Classes and Class Members](./abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
### <a name="interfaces"></a><span data-ttu-id="b1f5b-161">接口</span><span class="sxs-lookup"><span data-stu-id="b1f5b-161">Interfaces</span></span>  

 <span data-ttu-id="b1f5b-162">类和结构可以继承多个接口。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-162">Classes and structs can inherit multiple interfaces.</span></span> <span data-ttu-id="b1f5b-163">继承自接口意味着类型实现接口中定义的所有方法。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-163">To inherit from an interface means that the type implements all the methods defined in the interface.</span></span> <span data-ttu-id="b1f5b-164">有关详细信息，请参阅[接口](../interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-164">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
### <a name="generic-types"></a><span data-ttu-id="b1f5b-165">泛型类型</span><span class="sxs-lookup"><span data-stu-id="b1f5b-165">Generic Types</span></span>  

 <span data-ttu-id="b1f5b-166">类和结构可以使用一个或多个类型参数进行定义。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-166">Classes and structs can be defined with one or more type parameters.</span></span> <span data-ttu-id="b1f5b-167">客户端代码在创建类型实例时提供类型。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-167">Client code supplies the type when it creates an instance of the type.</span></span> <span data-ttu-id="b1f5b-168">例如，<xref:System.Collections.Generic> 命名空间中的 <xref:System.Collections.Generic.List%601> 类就是用一个类型参数进行定义的。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-168">For example The <xref:System.Collections.Generic.List%601> class in the <xref:System.Collections.Generic> namespace is defined with one type parameter.</span></span> <span data-ttu-id="b1f5b-169">客户端代码创建 `List<string>` 或 `List<int>` 的实例来指定列表将包含的类型。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-169">Client code creates an instance of a `List<string>` or `List<int>` to specify the type that the list will hold.</span></span> <span data-ttu-id="b1f5b-170">有关详细信息，请参阅[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-170">For more information, see [Generics](../generics/index.md).</span></span>  
  
### <a name="static-types"></a><span data-ttu-id="b1f5b-171">静态类型</span><span class="sxs-lookup"><span data-stu-id="b1f5b-171">Static Types</span></span>  

 <span data-ttu-id="b1f5b-172">类（而非结构）可以声明为 [static](../../language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-172">Classes (but not structs) can be declared as [static](../../language-reference/keywords/static.md).</span></span> <span data-ttu-id="b1f5b-173">静态类只能包含静态成员，不能使用新的关键字进行实例化。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-173">A static class can contain only static members and cannot be instantiated with the new keyword.</span></span> <span data-ttu-id="b1f5b-174">在程序加载时，类的一个副本会加载到内存中，而其成员则可通过类名进行访问。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-174">One copy of the class is loaded into memory when the program loads, and its members are accessed through the class name.</span></span> <span data-ttu-id="b1f5b-175">类和结构都能包含静态成员。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-175">Both classes and structs can contain static members.</span></span> <span data-ttu-id="b1f5b-176">有关详细信息，请参阅[静态类和静态类成员](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-176">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
### <a name="nested-types"></a><span data-ttu-id="b1f5b-177">嵌套类型</span><span class="sxs-lookup"><span data-stu-id="b1f5b-177">Nested Types</span></span>  

 <span data-ttu-id="b1f5b-178">类或结构可以嵌套在另一类或结构中。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-178">A class or struct can be nested within another class or struct.</span></span> <span data-ttu-id="b1f5b-179">有关详细信息，请参阅[嵌套类型](./nested-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-179">For more information, see [Nested Types](./nested-types.md).</span></span>  
  
### <a name="partial-types"></a><span data-ttu-id="b1f5b-180">分部类型</span><span class="sxs-lookup"><span data-stu-id="b1f5b-180">Partial Types</span></span>  

 <span data-ttu-id="b1f5b-181">可以在一个代码文件中定义类、结构或方法的一部分，并在其他代码文件中定义另一部分。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-181">You can define part of a class, struct or method in one code file and another part in a separate code file.</span></span> <span data-ttu-id="b1f5b-182">有关详细信息，请参阅[分部类和方法](./partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-182">For more information, see [Partial Classes and Methods](./partial-classes-and-methods.md).</span></span>  
  
### <a name="object-initializers"></a><span data-ttu-id="b1f5b-183">对象初始值设定项</span><span class="sxs-lookup"><span data-stu-id="b1f5b-183">Object Initializers</span></span>  

 <span data-ttu-id="b1f5b-184">无需显式调用构造函数，即可实例化和初始化类或结构对象和对象集合。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-184">You can instantiate and initialize class or struct objects, and collections of objects, without explicitly calling their constructor.</span></span> <span data-ttu-id="b1f5b-185">有关详细信息，请参阅[对象和集合初始值设定项](./object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-185">For more information, see [Object and Collection Initializers](./object-and-collection-initializers.md).</span></span>  
  
### <a name="anonymous-types"></a><span data-ttu-id="b1f5b-186">匿名类型</span><span class="sxs-lookup"><span data-stu-id="b1f5b-186">Anonymous Types</span></span>  

 <span data-ttu-id="b1f5b-187">如果不方便或没有必要创建已命名的类（例如，使用无需保留或传递给其他方法的数据结构填充列表时），可以使用匿名类型。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-187">In situations where it is not convenient or necessary to create a named class, for example when you are populating a list with data structures that you do not have to persist or pass to another method, you use anonymous types.</span></span> <span data-ttu-id="b1f5b-188">有关详细信息，请参阅[匿名类型](./anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-188">For more information, see [Anonymous Types](./anonymous-types.md).</span></span>  
  
### <a name="extension-methods"></a><span data-ttu-id="b1f5b-189">扩展方法</span><span class="sxs-lookup"><span data-stu-id="b1f5b-189">Extension Methods</span></span>  

 <span data-ttu-id="b1f5b-190">可以单独创建类型（其方法可以调用，就像它们属于原始类型一样）来“扩展”类，而无需创建派生类。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-190">You can "extend" a class without creating a derived class by creating a separate type whose methods can be called as if they belonged to the original type.</span></span> <span data-ttu-id="b1f5b-191">有关详细信息，请参阅[扩展方法](./extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-191">For more information, see [Extension Methods](./extension-methods.md).</span></span>  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="b1f5b-192">隐式类型的局部变量</span><span class="sxs-lookup"><span data-stu-id="b1f5b-192">Implicitly Typed Local Variables</span></span>  

 <span data-ttu-id="b1f5b-193">在类或结构方法中，可以使用隐式类型指示编译器在编译时确定正确的类型。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-193">Within a class or struct method, you can use implicit typing to instruct the compiler to determine the correct type at compile time.</span></span> <span data-ttu-id="b1f5b-194">有关详细信息，请参阅[隐式类型局部变量](./implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f5b-194">For more information, see [Implicitly Typed Local Variables](./implicitly-typed-local-variables.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b1f5b-195">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="b1f5b-195">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1f5b-196">请参阅</span><span class="sxs-lookup"><span data-stu-id="b1f5b-196">See also</span></span>

- [<span data-ttu-id="b1f5b-197">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="b1f5b-197">C# Programming Guide</span></span>](../index.md)
