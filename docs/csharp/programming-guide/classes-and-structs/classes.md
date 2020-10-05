---
title: 类 - C# 编程指南
description: 了解类类型及其创建方式
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 68b41eef0b604b80a9659eddf45d6512eac44fd6
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607728"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="ff453-103">类（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="ff453-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="ff453-104">引用类型</span><span class="sxs-lookup"><span data-stu-id="ff453-104">Reference types</span></span>  

<span data-ttu-id="ff453-105">定义为[类](../../language-reference/keywords/class.md)的一个类型是*引用类型*。</span><span class="sxs-lookup"><span data-stu-id="ff453-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="ff453-106">在运行时，如果声明引用类型的变量，此变量就会一直包含值 [null](../../language-reference/keywords/null.md)，直到使用 [new](../../language-reference/operators/new-operator.md) 运算符显式创建类实例，或直到为此变量分配可能已在其他位置创建的兼容类型的对象，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="ff453-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="ff453-107">创建对象时，在该托管堆上为该特定对象分足够的内存，并且该变量仅保存对所述对象位置的引用。</span><span class="sxs-lookup"><span data-stu-id="ff453-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="ff453-108">当分配托管堆上的类型和由 CLR 的自动内存管理功能对其进行回收（称为*垃圾回收*）时，需要开销。</span><span class="sxs-lookup"><span data-stu-id="ff453-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="ff453-109">但是，垃圾回收已是高度优化，并且在大多数情况下，不会产生性能问题。</span><span class="sxs-lookup"><span data-stu-id="ff453-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="ff453-110">有关垃圾回收的详细信息，请参阅[自动内存管理和垃圾回收](../../../standard/garbage-collection/fundamentals.md)。</span><span class="sxs-lookup"><span data-stu-id="ff453-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/fundamentals.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="ff453-111">声明类</span><span class="sxs-lookup"><span data-stu-id="ff453-111">Declaring Classes</span></span>

 <span data-ttu-id="ff453-112">使用后跟唯一标识符的 [class](../../language-reference/keywords/class.md) 关键字可以声明类，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="ff453-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="ff453-113">`class` 关键字前面是访问级别。</span><span class="sxs-lookup"><span data-stu-id="ff453-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="ff453-114">因为此例中使用的是 [public](../../language-reference/keywords/public.md)，所以任何人都可以创建此类的实例。</span><span class="sxs-lookup"><span data-stu-id="ff453-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="ff453-115">类的名称遵循 `class` 关键字。</span><span class="sxs-lookup"><span data-stu-id="ff453-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="ff453-116">类名称必须是有效的 C# [标识符名称](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="ff453-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="ff453-117">定义的其余部分是类的主体，其中定义了行为和数据。</span><span class="sxs-lookup"><span data-stu-id="ff453-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="ff453-118">类上的字段、属性、方法和事件统称为*类成员*。</span><span class="sxs-lookup"><span data-stu-id="ff453-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="ff453-119">创建对象</span><span class="sxs-lookup"><span data-stu-id="ff453-119">Creating objects</span></span>

<span data-ttu-id="ff453-120">虽然它们有时可以互换使用，但类和对象是不同的概念。</span><span class="sxs-lookup"><span data-stu-id="ff453-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="ff453-121">类定义对象类型，但不是对象本身。</span><span class="sxs-lookup"><span data-stu-id="ff453-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="ff453-122">对象是基于类的具体实体，有时称为类的实例。</span><span class="sxs-lookup"><span data-stu-id="ff453-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="ff453-123">可通过使用 [new](../../language-reference/operators/new-operator.md) 关键字，后跟对象要基于的类的名称，来创建对象，如：</span><span class="sxs-lookup"><span data-stu-id="ff453-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="ff453-124">创建类的实例后，会将一个该对象的引用传递回程序员。</span><span class="sxs-lookup"><span data-stu-id="ff453-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="ff453-125">在上一示例中，`object1` 是对基于 `Customer` 的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="ff453-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="ff453-126">该引用指向新对象，但不包含对象数据本身。</span><span class="sxs-lookup"><span data-stu-id="ff453-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="ff453-127">事实上，可以创建对象引用，而完全无需创建对象本身：</span><span class="sxs-lookup"><span data-stu-id="ff453-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="ff453-128">不建议创建这样一个不引用对象的对象引用，因为尝试通过这类引用访问对象会在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="ff453-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="ff453-129">但实际上可以使用这类引用来引用某个对象，方法是创建新对象，或者将其分配给现有对象，例如：</span><span class="sxs-lookup"><span data-stu-id="ff453-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="ff453-130">此代码创建指向同一对象的两个对象引用。</span><span class="sxs-lookup"><span data-stu-id="ff453-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="ff453-131">因此，通过 `object3` 对对象做出的任何更改都会在后续使用 `object4` 时反映出来。</span><span class="sxs-lookup"><span data-stu-id="ff453-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="ff453-132">由于基于类的对象是通过引用来实现其引用的，因此类被称为引用类型。</span><span class="sxs-lookup"><span data-stu-id="ff453-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="ff453-133">类继承</span><span class="sxs-lookup"><span data-stu-id="ff453-133">Class inheritance</span></span>  

<span data-ttu-id="ff453-134">类完全支持继承，这是面向对象的编程的基本特点。</span><span class="sxs-lookup"><span data-stu-id="ff453-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="ff453-135">创建类时，可以继承自其他任何未定义为 [sealed](../../language-reference/keywords/sealed.md) 的接口或类，而且其他类也可以继承自你的类并重写类虚方法。</span><span class="sxs-lookup"><span data-stu-id="ff453-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="ff453-136">继承是通过使用*派生*来完成的，这意味着类是通过使用其数据和行为所派生自的*基类*来声明的。</span><span class="sxs-lookup"><span data-stu-id="ff453-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="ff453-137">基类通过在派生的类名称后面追加冒号和基类名称来指定，如：</span><span class="sxs-lookup"><span data-stu-id="ff453-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="ff453-138">类声明基类时，会继承基类除构造函数外的所有成员。</span><span class="sxs-lookup"><span data-stu-id="ff453-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="ff453-139">有关详细信息，请参阅[继承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="ff453-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="ff453-140">与 C++ 不同，C# 中的类只能直接从基类继承。</span><span class="sxs-lookup"><span data-stu-id="ff453-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="ff453-141">但是，因为基类本身可能继承自其他类，因此类可能间接继承多个基类。</span><span class="sxs-lookup"><span data-stu-id="ff453-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="ff453-142">此外，类还可以直接实现多个接口。</span><span class="sxs-lookup"><span data-stu-id="ff453-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="ff453-143">有关详细信息，请参阅[接口](../interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ff453-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="ff453-144">类可以声明为 [abstract](../../language-reference/keywords/abstract.md)（抽象）。</span><span class="sxs-lookup"><span data-stu-id="ff453-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="ff453-145">抽象类包含抽象方法，抽象方法包含签名定义但不包含实现。</span><span class="sxs-lookup"><span data-stu-id="ff453-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="ff453-146">抽象类不能实例化。</span><span class="sxs-lookup"><span data-stu-id="ff453-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="ff453-147">只能通过可实现抽象方法的派生类来使用该类。</span><span class="sxs-lookup"><span data-stu-id="ff453-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="ff453-148">与此相反，[sealed](../../language-reference/keywords/sealed.md)（密封）类不允许其他类继承。</span><span class="sxs-lookup"><span data-stu-id="ff453-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="ff453-149">有关详细信息，请参阅[抽象类、密封类和类成员](abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="ff453-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="ff453-150">类定义可以在不同的源文件之间分割。</span><span class="sxs-lookup"><span data-stu-id="ff453-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="ff453-151">有关详细信息，请参阅[分部类和方法](partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="ff453-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff453-152">示例</span><span class="sxs-lookup"><span data-stu-id="ff453-152">Example</span></span>

<span data-ttu-id="ff453-153">以下示例定义了一个公共类，该类包含一个[自动实现的属性](auto-implemented-properties.md)、一个方法和一个名为构造函数的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="ff453-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="ff453-154">有关详细信息，请参阅[属性](properties.md)、[方法](methods.md)和[构造函数](constructors.md)主题。</span><span class="sxs-lookup"><span data-stu-id="ff453-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="ff453-155">然后使用 `new` 关键字实例化类的实例。</span><span class="sxs-lookup"><span data-stu-id="ff453-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="ff453-156">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="ff453-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ff453-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="ff453-157">See also</span></span>

- [<span data-ttu-id="ff453-158">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="ff453-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ff453-159">面向对象的编程</span><span class="sxs-lookup"><span data-stu-id="ff453-159">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="ff453-160">多态性</span><span class="sxs-lookup"><span data-stu-id="ff453-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="ff453-161">标识符名称</span><span class="sxs-lookup"><span data-stu-id="ff453-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="ff453-162">成员</span><span class="sxs-lookup"><span data-stu-id="ff453-162">Members</span></span>](members.md)
- [<span data-ttu-id="ff453-163">方法</span><span class="sxs-lookup"><span data-stu-id="ff453-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="ff453-164">构造函数</span><span class="sxs-lookup"><span data-stu-id="ff453-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="ff453-165">终结器</span><span class="sxs-lookup"><span data-stu-id="ff453-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="ff453-166">对象</span><span class="sxs-lookup"><span data-stu-id="ff453-166">Objects</span></span>](objects.md)
