---
title: 面向对象的编程 (C#)
description: C# 提供针对面向对象的编程（包括抽象、封装、继承和多态性）的完整支持。
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0c5495aefad73a2916ad6e2bd2bf3701d0868f24
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302810"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="08e9b-103">面向对象的编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="08e9b-103">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="08e9b-104">C# 提供针对面向对象的编程（包括抽象、封装、继承和多态性）的完整支持。</span><span class="sxs-lookup"><span data-stu-id="08e9b-104">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="08e9b-105">“抽象”意味着对类型使用者隐藏不必要的详细信息。</span><span class="sxs-lookup"><span data-stu-id="08e9b-105">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="08e9b-106">“封装”意味着将一组相关属性、方法和其他成员视为一个单元或对象。</span><span class="sxs-lookup"><span data-stu-id="08e9b-106">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="08e9b-107">“继承”描述基于现有类创建新类的能力。</span><span class="sxs-lookup"><span data-stu-id="08e9b-107">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="08e9b-108">多态性意味着可以有多个可互换使用的类，即使每个类以不同方式实现相同属性或方法。</span><span class="sxs-lookup"><span data-stu-id="08e9b-108">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="08e9b-109">类和对象</span><span class="sxs-lookup"><span data-stu-id="08e9b-109">Classes and objects</span></span>

<span data-ttu-id="08e9b-110">“类”和“对象”分别描述对象的类型和类的实例   。</span><span class="sxs-lookup"><span data-stu-id="08e9b-110">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="08e9b-111">因此，创建对象的操作称为“实例化”。</span><span class="sxs-lookup"><span data-stu-id="08e9b-111">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="08e9b-112">如果使用蓝图类比，类是蓝图，对象就是基于该蓝图的建筑。</span><span class="sxs-lookup"><span data-stu-id="08e9b-112">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="08e9b-113">定义类：</span><span class="sxs-lookup"><span data-stu-id="08e9b-113">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="08e9b-114">C# 还提供被称为“结构”的类型，在不需要支持继承或多形性时非常有用。</span><span class="sxs-lookup"><span data-stu-id="08e9b-114">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="08e9b-115">有关详细信息，请参阅[在类和结构之间选择](../../../standard/design-guidelines/choosing-between-class-and-struct.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-115">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="08e9b-116">定义结构：</span><span class="sxs-lookup"><span data-stu-id="08e9b-116">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="08e9b-117">有关详细信息，请参阅有关 [class](../../language-reference/keywords/class.md) 和 [struct](../../language-reference/builtin-types/struct.md) 关键字的文章。</span><span class="sxs-lookup"><span data-stu-id="08e9b-117">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="08e9b-118">类成员</span><span class="sxs-lookup"><span data-stu-id="08e9b-118">Class members</span></span>

<span data-ttu-id="08e9b-119">每个类都可以具有不同的“类成员”。类成员包括属性（用于描述类数据）、方法（用于定义类行为）和事件（用于在不同的类和对象之间提供通信）。</span><span class="sxs-lookup"><span data-stu-id="08e9b-119">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="08e9b-120">属性和字段</span><span class="sxs-lookup"><span data-stu-id="08e9b-120">Properties and fields</span></span>

<span data-ttu-id="08e9b-121">字段和属性表示对象包含的信息。</span><span class="sxs-lookup"><span data-stu-id="08e9b-121">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="08e9b-122">字段类似于变量，因为可以直接读取或设置它们，不过要考虑适用的访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="08e9b-122">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="08e9b-123">定义可从类的实例中访问的字段：</span><span class="sxs-lookup"><span data-stu-id="08e9b-123">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="08e9b-124">属性具有 `get` 和 `set` 访问器，它们对设置或返回值的方式提供更多控制。</span><span class="sxs-lookup"><span data-stu-id="08e9b-124">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="08e9b-125">C# 允许创建私有字段来存储属性值，或者使用自动实现的属性，这些属性自动在后台创建此字段，并为属性过程提供基本逻辑。</span><span class="sxs-lookup"><span data-stu-id="08e9b-125">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="08e9b-126">定义自动实现的属性：</span><span class="sxs-lookup"><span data-stu-id="08e9b-126">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="08e9b-127">如果你需要执行一些其他操作来读取和写入属性值，请定义一个用于存储属性值的字段，并提供用于存储和检索该字段的基本逻辑：</span><span class="sxs-lookup"><span data-stu-id="08e9b-127">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="08e9b-128">大多数属性的方法或过程都是既可以设置也可以获取属性值。</span><span class="sxs-lookup"><span data-stu-id="08e9b-128">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="08e9b-129">但你可以创建只读或只写属性来限制对它们的修改或读取。</span><span class="sxs-lookup"><span data-stu-id="08e9b-129">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="08e9b-130">在 C# 中，可以忽略 `get` 或 `set` 属性方法。</span><span class="sxs-lookup"><span data-stu-id="08e9b-130">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="08e9b-131">但是，自动实现的属性不能是只写的。</span><span class="sxs-lookup"><span data-stu-id="08e9b-131">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="08e9b-132">可以在包含类的构造函数中设置只读自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="08e9b-132">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="08e9b-133">有关详情，请参阅：</span><span class="sxs-lookup"><span data-stu-id="08e9b-133">For more information, see:</span></span>

- [<span data-ttu-id="08e9b-134">get</span><span class="sxs-lookup"><span data-stu-id="08e9b-134">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="08e9b-135">set</span><span class="sxs-lookup"><span data-stu-id="08e9b-135">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="08e9b-136">方法</span><span class="sxs-lookup"><span data-stu-id="08e9b-136">Methods</span></span>

<span data-ttu-id="08e9b-137">“方法”是对象可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="08e9b-137">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="08e9b-138">定义类的方法：</span><span class="sxs-lookup"><span data-stu-id="08e9b-138">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="08e9b-139">对于同一方法，一个类可以有多个实现，也叫“重载”，这些实现的区别在于参数个数或参数类型的不同。</span><span class="sxs-lookup"><span data-stu-id="08e9b-139">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="08e9b-140">重载方法：</span><span class="sxs-lookup"><span data-stu-id="08e9b-140">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="08e9b-141">大多数情况下，方法是在类定义中声明的。</span><span class="sxs-lookup"><span data-stu-id="08e9b-141">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="08e9b-142">但是，C# 还支持“扩展方法”，这种方法允许你将方法添加到实际类定义之外的现有类中。</span><span class="sxs-lookup"><span data-stu-id="08e9b-142">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="08e9b-143">有关详情，请参阅：</span><span class="sxs-lookup"><span data-stu-id="08e9b-143">For more information, see:</span></span>

- [<span data-ttu-id="08e9b-144">方法</span><span class="sxs-lookup"><span data-stu-id="08e9b-144">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="08e9b-145">扩展方法</span><span class="sxs-lookup"><span data-stu-id="08e9b-145">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="08e9b-146">构造函数</span><span class="sxs-lookup"><span data-stu-id="08e9b-146">Constructors</span></span>

<span data-ttu-id="08e9b-147">构造函数一种类方法，它们在创建给定类型的对象时自动执行。</span><span class="sxs-lookup"><span data-stu-id="08e9b-147">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="08e9b-148">构造函数通常用于初始化新对象的数据成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-148">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="08e9b-149">构造函数只能在创建类时运行一次。</span><span class="sxs-lookup"><span data-stu-id="08e9b-149">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="08e9b-150">此外，构造函数中的代码始终在类中所有其他代码之前运行。</span><span class="sxs-lookup"><span data-stu-id="08e9b-150">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="08e9b-151">但是，你可以按照为任何其他方法创建重载的方式，创建多个构造函数重载。</span><span class="sxs-lookup"><span data-stu-id="08e9b-151">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="08e9b-152">定义类的构造函数：</span><span class="sxs-lookup"><span data-stu-id="08e9b-152">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="08e9b-153">有关详细信息，请参阅[构造函数](../classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-153">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="08e9b-154">终结器</span><span class="sxs-lookup"><span data-stu-id="08e9b-154">Finalizers</span></span>

<span data-ttu-id="08e9b-155">终结器用于析构类的实例。</span><span class="sxs-lookup"><span data-stu-id="08e9b-155">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="08e9b-156">在 .NET 中，垃圾回收器自动管理应用程序中托管对象的内存分配和释放。</span><span class="sxs-lookup"><span data-stu-id="08e9b-156">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="08e9b-157">但是，你可能仍会需要终结器来清理应用程序创建的所有非托管资源。</span><span class="sxs-lookup"><span data-stu-id="08e9b-157">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="08e9b-158">一个类只能有一个终结器。</span><span class="sxs-lookup"><span data-stu-id="08e9b-158">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="08e9b-159">有关终结器和 .NET 垃圾回收的详细信息，请参阅[垃圾回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-159">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="08e9b-160">事件</span><span class="sxs-lookup"><span data-stu-id="08e9b-160">Events</span></span>

<span data-ttu-id="08e9b-161">类或对象可以通过事件向其他类或对象通知发生的相关事情。</span><span class="sxs-lookup"><span data-stu-id="08e9b-161">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="08e9b-162">发送（或引发）事件的类称为“发行者”，接收（或处理）事件的类称为“订户”。</span><span class="sxs-lookup"><span data-stu-id="08e9b-162">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="08e9b-163">有关事件以及如何引发和处理事件的详细信息，请参阅[事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-163">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="08e9b-164">若要在类中声明事件，请使用 [event](../../language-reference/keywords/event.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="08e9b-164">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="08e9b-165">若要引发事件，请调用事件委托。</span><span class="sxs-lookup"><span data-stu-id="08e9b-165">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="08e9b-166">若要订阅事件，请使用 `+=` 运算符；若要取消订阅事件，请使用 `-=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="08e9b-166">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="08e9b-167">嵌套类</span><span class="sxs-lookup"><span data-stu-id="08e9b-167">Nested classes</span></span>

<span data-ttu-id="08e9b-168">在另一个类中定义的类称为“嵌套”。</span><span class="sxs-lookup"><span data-stu-id="08e9b-168">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="08e9b-169">默认情况下，嵌套类是私有类。</span><span class="sxs-lookup"><span data-stu-id="08e9b-169">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="08e9b-170">若要创建嵌套类的实例，请使用容器类的名称，后接一个点，再接嵌套类的名称：</span><span class="sxs-lookup"><span data-stu-id="08e9b-170">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="08e9b-171">访问修饰符和访问级别</span><span class="sxs-lookup"><span data-stu-id="08e9b-171">Access modifiers and access levels</span></span>

<span data-ttu-id="08e9b-172">所有类和类方法都可以使用“访问修饰符”指定自己为其他类提供的访问级别。</span><span class="sxs-lookup"><span data-stu-id="08e9b-172">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="08e9b-173">可用的访问修饰符有以下这些：</span><span class="sxs-lookup"><span data-stu-id="08e9b-173">The following access modifiers are available:</span></span>

| <span data-ttu-id="08e9b-174">C# 修饰符</span><span class="sxs-lookup"><span data-stu-id="08e9b-174">C# Modifier</span></span> | <span data-ttu-id="08e9b-175">定义</span><span class="sxs-lookup"><span data-stu-id="08e9b-175">Definition</span></span> |
|--|--|
| [<span data-ttu-id="08e9b-176">public</span><span class="sxs-lookup"><span data-stu-id="08e9b-176">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="08e9b-177">同一程序集中的任何其他代码或引用该程序集的其他程序集都可以访问该类型或成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-177">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="08e9b-178">private</span><span class="sxs-lookup"><span data-stu-id="08e9b-178">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="08e9b-179">只有同一类中的代码可以访问该类型或成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-179">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="08e9b-180">受保护</span><span class="sxs-lookup"><span data-stu-id="08e9b-180">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="08e9b-181">只有同一类或派生类中的代码可以访问该类型或成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-181">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="08e9b-182">internal</span><span class="sxs-lookup"><span data-stu-id="08e9b-182">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="08e9b-183">同一程序集中的任何代码都可以访问该类型或成员，但其他程序集中的代码不可以。</span><span class="sxs-lookup"><span data-stu-id="08e9b-183">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="08e9b-184">protected internal</span><span class="sxs-lookup"><span data-stu-id="08e9b-184">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="08e9b-185">同一程序集中的任何代码或其他程序集中的任何派生类都可以访问该类型或成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-185">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="08e9b-186">private protected</span><span class="sxs-lookup"><span data-stu-id="08e9b-186">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="08e9b-187">同一类或基类程序集内派生类中的代码可以访问该类型或成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-187">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="08e9b-188">有关详细信息，请参阅[访问修饰符](../classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-188">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="08e9b-189">实例化类</span><span class="sxs-lookup"><span data-stu-id="08e9b-189">Instantiating classes</span></span>

<span data-ttu-id="08e9b-190">若要创建对象，你需要实例化类，即创建类实例。</span><span class="sxs-lookup"><span data-stu-id="08e9b-190">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="08e9b-191">实例化类之后，可以为该实例的属性和字段赋值，还可以调用类方法。</span><span class="sxs-lookup"><span data-stu-id="08e9b-191">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="08e9b-192">若要在类的实例化过程中为属性赋值，请使用对象初始值设定项：</span><span class="sxs-lookup"><span data-stu-id="08e9b-192">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="08e9b-193">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="08e9b-193">For more information, see:</span></span>

- [<span data-ttu-id="08e9b-194">new 运算符</span><span class="sxs-lookup"><span data-stu-id="08e9b-194">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="08e9b-195">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="08e9b-195">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="08e9b-196">静态类和成员</span><span class="sxs-lookup"><span data-stu-id="08e9b-196">Static Classes and Members</span></span>

<span data-ttu-id="08e9b-197">类的静态成员是指由该类的所有实例共享的属性、过程或字段。</span><span class="sxs-lookup"><span data-stu-id="08e9b-197">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="08e9b-198">定义静态成员：</span><span class="sxs-lookup"><span data-stu-id="08e9b-198">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="08e9b-199">若要访问静态成员，请使用类的名称，但不要创建此类的对象：</span><span class="sxs-lookup"><span data-stu-id="08e9b-199">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="08e9b-200">C# 中的静态类只有静态成员，无法进行实例化。</span><span class="sxs-lookup"><span data-stu-id="08e9b-200">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="08e9b-201">静态成员也无法访问非静态属性、字段或方法</span><span class="sxs-lookup"><span data-stu-id="08e9b-201">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="08e9b-202">有关详细信息，请参阅：[static](../../language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-202">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="08e9b-203">匿名类型</span><span class="sxs-lookup"><span data-stu-id="08e9b-203">Anonymous types</span></span>

<span data-ttu-id="08e9b-204">匿名类型使你无需为数据类型编写类定义即可创建对象。</span><span class="sxs-lookup"><span data-stu-id="08e9b-204">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="08e9b-205">此时，编译器将为你生成类。</span><span class="sxs-lookup"><span data-stu-id="08e9b-205">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="08e9b-206">该类没有可使用的名称，且包含在声明对象时指定的属性。</span><span class="sxs-lookup"><span data-stu-id="08e9b-206">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="08e9b-207">创建匿名类型的实例：</span><span class="sxs-lookup"><span data-stu-id="08e9b-207">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="08e9b-208">有关详情，请参阅：[匿名类型](../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-208">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="08e9b-209">继承</span><span class="sxs-lookup"><span data-stu-id="08e9b-209">Inheritance</span></span>

<span data-ttu-id="08e9b-210">通过继承，可以创建一个新类，它重用、扩展和修改另一个类中定义的行为。</span><span class="sxs-lookup"><span data-stu-id="08e9b-210">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="08e9b-211">其成员被继承的类称为“基类”，继承这些成员的类称为“派生类”。</span><span class="sxs-lookup"><span data-stu-id="08e9b-211">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="08e9b-212">但是，C# 中的所有类都隐式继承自 <xref:System.Object> 类，该类支持 .NET 类层次结构，并为所有类提供低级别服务。</span><span class="sxs-lookup"><span data-stu-id="08e9b-212">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="08e9b-213">C# 不支持多重继承。</span><span class="sxs-lookup"><span data-stu-id="08e9b-213">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="08e9b-214">即，只能为一个派生类指定一个基类。</span><span class="sxs-lookup"><span data-stu-id="08e9b-214">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="08e9b-215">从基类继承：</span><span class="sxs-lookup"><span data-stu-id="08e9b-215">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="08e9b-216">默认情况下，可以继承所有类。</span><span class="sxs-lookup"><span data-stu-id="08e9b-216">By default all classes can be inherited.</span></span> <span data-ttu-id="08e9b-217">但你可以指定不得将某个类用作基类，也可以创建只能用作基类的类。</span><span class="sxs-lookup"><span data-stu-id="08e9b-217">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="08e9b-218">指定不得将某个类用作基类：</span><span class="sxs-lookup"><span data-stu-id="08e9b-218">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="08e9b-219">指定只能用作基类且无法实例化的类：</span><span class="sxs-lookup"><span data-stu-id="08e9b-219">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="08e9b-220">有关详情，请参阅：</span><span class="sxs-lookup"><span data-stu-id="08e9b-220">For more information, see:</span></span>

- [<span data-ttu-id="08e9b-221">sealed</span><span class="sxs-lookup"><span data-stu-id="08e9b-221">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="08e9b-222">abstract</span><span class="sxs-lookup"><span data-stu-id="08e9b-222">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="08e9b-223">重写成员</span><span class="sxs-lookup"><span data-stu-id="08e9b-223">Overriding Members</span></span>

<span data-ttu-id="08e9b-224">默认情况下，派生类继承其基类的所有成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-224">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="08e9b-225">若希望更改继承成员的行为，则需要重写该成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-225">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="08e9b-226">即，可以在派生类中定义方法、属性或事件的新实现。</span><span class="sxs-lookup"><span data-stu-id="08e9b-226">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="08e9b-227">下列修饰符用于控制如何重写属性和方法：</span><span class="sxs-lookup"><span data-stu-id="08e9b-227">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="08e9b-228">C# 修饰符</span><span class="sxs-lookup"><span data-stu-id="08e9b-228">C# Modifier</span></span> | <span data-ttu-id="08e9b-229">定义</span><span class="sxs-lookup"><span data-stu-id="08e9b-229">Definition</span></span> |
|--|--|
| [<span data-ttu-id="08e9b-230">virtual</span><span class="sxs-lookup"><span data-stu-id="08e9b-230">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="08e9b-231">允许在派生类中重写类成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-231">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="08e9b-232">override</span><span class="sxs-lookup"><span data-stu-id="08e9b-232">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="08e9b-233">重写基类中定义的虚拟（可重写）成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-233">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="08e9b-234">abstract</span><span class="sxs-lookup"><span data-stu-id="08e9b-234">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="08e9b-235">要求在派生类中重写类成员。</span><span class="sxs-lookup"><span data-stu-id="08e9b-235">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="08e9b-236">new 修饰符</span><span class="sxs-lookup"><span data-stu-id="08e9b-236">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="08e9b-237">隐藏继承自基类的成员</span><span class="sxs-lookup"><span data-stu-id="08e9b-237">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="08e9b-238">接口</span><span class="sxs-lookup"><span data-stu-id="08e9b-238">Interfaces</span></span>

<span data-ttu-id="08e9b-239">和类一样，接口也定义了一系列属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="08e9b-239">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="08e9b-240">但与类不同的是，接口并不提供实现。</span><span class="sxs-lookup"><span data-stu-id="08e9b-240">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="08e9b-241">它们由类来实现，并从类中被定义为单独的实体。</span><span class="sxs-lookup"><span data-stu-id="08e9b-241">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="08e9b-242">接口表示一种约定，实现接口的类必须严格按其定义来实现接口的每个方面。</span><span class="sxs-lookup"><span data-stu-id="08e9b-242">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="08e9b-243">定义接口：</span><span class="sxs-lookup"><span data-stu-id="08e9b-243">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="08e9b-244">在类中实现接口：</span><span class="sxs-lookup"><span data-stu-id="08e9b-244">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="08e9b-245">有关详细信息，请参阅关于[接口](../interfaces/index.md)的编程指南，以及关于 [interface](../../language-reference/keywords/interface.md) 关键字的语言参考。</span><span class="sxs-lookup"><span data-stu-id="08e9b-245">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="08e9b-246">泛型</span><span class="sxs-lookup"><span data-stu-id="08e9b-246">Generics</span></span>

<span data-ttu-id="08e9b-247">.NET 中的类、结构、接口和方法可以包括“类型参数”，类型参数定义它们可以存储或使用的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="08e9b-247">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="08e9b-248">最常见的泛型示例是集合，从中可以指定要存储在集合中的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="08e9b-248">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="08e9b-249">定义泛型类：</span><span class="sxs-lookup"><span data-stu-id="08e9b-249">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="08e9b-250">创建泛型类的实例：</span><span class="sxs-lookup"><span data-stu-id="08e9b-250">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="08e9b-251">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="08e9b-251">For more information, see:</span></span>

- [<span data-ttu-id="08e9b-252">.NET 中的泛型</span><span class="sxs-lookup"><span data-stu-id="08e9b-252">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="08e9b-253">泛型 - C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="08e9b-253">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="08e9b-254">委托</span><span class="sxs-lookup"><span data-stu-id="08e9b-254">Delegates</span></span>

<span data-ttu-id="08e9b-255">“委托”是一种类型，它定义方法签名，可以提供对具有兼容签名的任何方法的引用。</span><span class="sxs-lookup"><span data-stu-id="08e9b-255">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="08e9b-256">你可以通过委托调用方法。</span><span class="sxs-lookup"><span data-stu-id="08e9b-256">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="08e9b-257">委托用于将方法作为参数传递给其他方法。</span><span class="sxs-lookup"><span data-stu-id="08e9b-257">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="08e9b-258">事件处理程序就是通过委托调用的方法。</span><span class="sxs-lookup"><span data-stu-id="08e9b-258">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="08e9b-259">有关在事件处理中使用委托的详细信息，请参阅[事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="08e9b-259">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="08e9b-260">创建委托：</span><span class="sxs-lookup"><span data-stu-id="08e9b-260">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="08e9b-261">创建对与委托指定的签名相匹配的方法的引用：</span><span class="sxs-lookup"><span data-stu-id="08e9b-261">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
    {
        // Add code here.
    }

    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="08e9b-262">有关详细信息，请参阅关于[委托](../delegates/index.md)的编程指南，以及关于 [delegate](../../language-reference/builtin-types/reference-types.md) 关键字的语言参考。</span><span class="sxs-lookup"><span data-stu-id="08e9b-262">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="08e9b-263">请参阅</span><span class="sxs-lookup"><span data-stu-id="08e9b-263">See also</span></span>

- [<span data-ttu-id="08e9b-264">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="08e9b-264">C# Programming Guide</span></span>](../index.md)
