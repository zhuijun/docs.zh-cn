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
# <a name="object-oriented-programming-c"></a>面向对象的编程 (C#)

C# 提供针对面向对象的编程（包括抽象、封装、继承和多态性）的完整支持。

- “抽象”意味着对类型使用者隐藏不必要的详细信息。
- “封装”意味着将一组相关属性、方法和其他成员视为一个单元或对象。
- “继承”描述基于现有类创建新类的能力。
- 多态性意味着可以有多个可互换使用的类，即使每个类以不同方式实现相同属性或方法。

## <a name="classes-and-objects"></a>类和对象

“类”和“对象”分别描述对象的类型和类的实例   。 因此，创建对象的操作称为“实例化”。 如果使用蓝图类比，类是蓝图，对象就是基于该蓝图的建筑。

定义类：

```csharp
class SampleClass
{
}
```

C# 还提供被称为“结构”的类型，在不需要支持继承或多形性时非常有用。 有关详细信息，请参阅[在类和结构之间选择](../../../standard/design-guidelines/choosing-between-class-and-struct.md)。

定义结构：

```csharp
struct SampleStruct
{
}
```

有关详细信息，请参阅有关 [class](../../language-reference/keywords/class.md) 和 [struct](../../language-reference/builtin-types/struct.md) 关键字的文章。

### <a name="class-members"></a>类成员

每个类都可以具有不同的“类成员”。类成员包括属性（用于描述类数据）、方法（用于定义类行为）和事件（用于在不同的类和对象之间提供通信）。

#### <a name="properties-and-fields"></a>属性和字段

字段和属性表示对象包含的信息。 字段类似于变量，因为可以直接读取或设置它们，不过要考虑适用的访问修饰符。

定义可从类的实例中访问的字段：

```csharp
public class SampleClass
{
    string sampleField;
}
```

属性具有 `get` 和 `set` 访问器，它们对设置或返回值的方式提供更多控制。

C# 允许创建私有字段来存储属性值，或者使用自动实现的属性，这些属性自动在后台创建此字段，并为属性过程提供基本逻辑。

定义自动实现的属性：

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

如果你需要执行一些其他操作来读取和写入属性值，请定义一个用于存储属性值的字段，并提供用于存储和检索该字段的基本逻辑：

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

大多数属性的方法或过程都是既可以设置也可以获取属性值。 但你可以创建只读或只写属性来限制对它们的修改或读取。 在 C# 中，可以忽略 `get` 或 `set` 属性方法。 但是，自动实现的属性不能是只写的。 可以在包含类的构造函数中设置只读自动实现的属性。

有关详情，请参阅：

- [get](../../language-reference/keywords/get.md)
- [set](../../language-reference/keywords/set.md)

#### <a name="methods"></a>方法

“方法”是对象可以执行的操作。

定义类的方法：

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

对于同一方法，一个类可以有多个实现，也叫“重载”，这些实现的区别在于参数个数或参数类型的不同。

重载方法：

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

大多数情况下，方法是在类定义中声明的。 但是，C# 还支持“扩展方法”，这种方法允许你将方法添加到实际类定义之外的现有类中。

有关详情，请参阅：

- [方法](../classes-and-structs/methods.md)
- [扩展方法](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>构造函数

构造函数一种类方法，它们在创建给定类型的对象时自动执行。 构造函数通常用于初始化新对象的数据成员。 构造函数只能在创建类时运行一次。 此外，构造函数中的代码始终在类中所有其他代码之前运行。 但是，你可以按照为任何其他方法创建重载的方式，创建多个构造函数重载。

定义类的构造函数：

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

有关详细信息，请参阅[构造函数](../classes-and-structs/constructors.md)。

#### <a name="finalizers"></a>终结器

终结器用于析构类的实例。 在 .NET 中，垃圾回收器自动管理应用程序中托管对象的内存分配和释放。 但是，你可能仍会需要终结器来清理应用程序创建的所有非托管资源。 一个类只能有一个终结器。

有关终结器和 .NET 垃圾回收的详细信息，请参阅[垃圾回收](../../../standard/garbage-collection/index.md)。

#### <a name="events"></a>事件

类或对象可以通过事件向其他类或对象通知发生的相关事情。 发送（或引发）事件的类称为“发行者”，接收（或处理）事件的类称为“订户”。 有关事件以及如何引发和处理事件的详细信息，请参阅[事件](../../../standard/events/index.md)。

- 若要在类中声明事件，请使用 [event](../../language-reference/keywords/event.md) 关键字。
- 若要引发事件，请调用事件委托。
- 若要订阅事件，请使用 `+=` 运算符；若要取消订阅事件，请使用 `-=` 运算符。

#### <a name="nested-classes"></a>嵌套类

在另一个类中定义的类称为“嵌套”。 默认情况下，嵌套类是私有类。

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

若要创建嵌套类的实例，请使用容器类的名称，后接一个点，再接嵌套类的名称：

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>访问修饰符和访问级别

所有类和类方法都可以使用“访问修饰符”指定自己为其他类提供的访问级别。

可用的访问修饰符有以下这些：

| C# 修饰符 | 定义 |
|--|--|
| [public](../../language-reference/keywords/public.md) | 同一程序集中的任何其他代码或引用该程序集的其他程序集都可以访问该类型或成员。 |
| [private](../../language-reference/keywords/private.md) | 只有同一类中的代码可以访问该类型或成员。 |
| [受保护](../../language-reference/keywords/protected.md) | 只有同一类或派生类中的代码可以访问该类型或成员。 |
| [internal](../../language-reference/keywords/internal.md) | 同一程序集中的任何代码都可以访问该类型或成员，但其他程序集中的代码不可以。 |
| [protected internal](../../language-reference/keywords/protected-internal.md) | 同一程序集中的任何代码或其他程序集中的任何派生类都可以访问该类型或成员。 |
| [private protected](../../language-reference/keywords/private-protected.md) | 同一类或基类程序集内派生类中的代码可以访问该类型或成员。 |

有关详细信息，请参阅[访问修饰符](../classes-and-structs/access-modifiers.md)。

### <a name="instantiating-classes"></a>实例化类

若要创建对象，你需要实例化类，即创建类实例。

```csharp
SampleClass sampleObject = new SampleClass();
```

实例化类之后，可以为该实例的属性和字段赋值，还可以调用类方法。

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

若要在类的实例化过程中为属性赋值，请使用对象初始值设定项：

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

有关详细信息，请参见:

- [new 运算符](../../language-reference/operators/new-operator.md)
- [对象和集合初始值设定项](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>静态类和成员

类的静态成员是指由该类的所有实例共享的属性、过程或字段。

定义静态成员：

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

若要访问静态成员，请使用类的名称，但不要创建此类的对象：

```csharp
Console.WriteLine(SampleClass.SampleString);
```

C# 中的静态类只有静态成员，无法进行实例化。 静态成员也无法访问非静态属性、字段或方法

有关详细信息，请参阅：[static](../../language-reference/keywords/static.md)。

### <a name="anonymous-types"></a>匿名类型

匿名类型使你无需为数据类型编写类定义即可创建对象。 此时，编译器将为你生成类。 该类没有可使用的名称，且包含在声明对象时指定的属性。

创建匿名类型的实例：

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

有关详情，请参阅：[匿名类型](../classes-and-structs/anonymous-types.md)。

## <a name="inheritance"></a>继承

通过继承，可以创建一个新类，它重用、扩展和修改另一个类中定义的行为。 其成员被继承的类称为“基类”，继承这些成员的类称为“派生类”。 但是，C# 中的所有类都隐式继承自 <xref:System.Object> 类，该类支持 .NET 类层次结构，并为所有类提供低级别服务。

> [!NOTE]
> C# 不支持多重继承。 即，只能为一个派生类指定一个基类。

从基类继承：

```csharp
class DerivedClass:BaseClass { }
```

默认情况下，可以继承所有类。 但你可以指定不得将某个类用作基类，也可以创建只能用作基类的类。

指定不得将某个类用作基类：

```csharp
public sealed class A { }
```

指定只能用作基类且无法实例化的类：

```csharp
public abstract class B { }
```

有关详情，请参阅：

- [sealed](../../language-reference/keywords/sealed.md)
- [abstract](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>重写成员

默认情况下，派生类继承其基类的所有成员。 若希望更改继承成员的行为，则需要重写该成员。 即，可以在派生类中定义方法、属性或事件的新实现。

下列修饰符用于控制如何重写属性和方法：

| C# 修饰符 | 定义 |
|--|--|
| [virtual](../../language-reference/keywords/virtual.md) | 允许在派生类中重写类成员。 |
| [override](../../language-reference/keywords/override.md) | 重写基类中定义的虚拟（可重写）成员。 |
| [abstract](../../language-reference/keywords/abstract.md) | 要求在派生类中重写类成员。 |
| [new 修饰符](../../language-reference/keywords/new-modifier.md) | 隐藏继承自基类的成员 |

## <a name="interfaces"></a>接口

和类一样，接口也定义了一系列属性、方法和事件。 但与类不同的是，接口并不提供实现。 它们由类来实现，并从类中被定义为单独的实体。 接口表示一种约定，实现接口的类必须严格按其定义来实现接口的每个方面。

定义接口：

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

在类中实现接口：

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

有关详细信息，请参阅关于[接口](../interfaces/index.md)的编程指南，以及关于 [interface](../../language-reference/keywords/interface.md) 关键字的语言参考。

## <a name="generics"></a>泛型

.NET 中的类、结构、接口和方法可以包括“类型参数”，类型参数定义它们可以存储或使用的对象的类型。 最常见的泛型示例是集合，从中可以指定要存储在集合中的对象的类型。

定义泛型类：

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

创建泛型类的实例：

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

有关详细信息，请参见:

- [.NET 中的泛型](../../../standard/generics/index.md)
- [泛型 - C# 编程指南](../generics/index.md)

## <a name="delegates"></a>委托

“委托”是一种类型，它定义方法签名，可以提供对具有兼容签名的任何方法的引用。 你可以通过委托调用方法。 委托用于将方法作为参数传递给其他方法。

> [!NOTE]
> 事件处理程序就是通过委托调用的方法。 有关在事件处理中使用委托的详细信息，请参阅[事件](../../../standard/events/index.md)。

创建委托：

```csharp
public delegate void SampleDelegate(string str);
```

创建对与委托指定的签名相匹配的方法的引用：

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

有关详细信息，请参阅关于[委托](../delegates/index.md)的编程指南，以及关于 [delegate](../../language-reference/builtin-types/reference-types.md) 关键字的语言参考。

## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
