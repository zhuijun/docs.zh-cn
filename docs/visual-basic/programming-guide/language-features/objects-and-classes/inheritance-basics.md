---
title: 继承基础知识
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 3bf1847f618a642d26df4aa1c5247a4ba2bd3b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411774"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="2f105-102">继承的基础知识 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f105-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="2f105-103">`Inherits`语句用于声明新类（称为*派生类*），该类基于现有类（称为*基类*）。</span><span class="sxs-lookup"><span data-stu-id="2f105-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="2f105-104">派生类继承和可以扩展基类中定义的属性、方法、事件、字段和常量。</span><span class="sxs-lookup"><span data-stu-id="2f105-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="2f105-105">以下部分介绍了一些继承规则，以及可用于更改类继承或继承方式的修饰符：</span><span class="sxs-lookup"><span data-stu-id="2f105-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="2f105-106">默认情况下，所有类都是可继承的，除非使用关键字进行标记 `NotInheritable` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="2f105-107">类可以继承自你的项目中的其他类，也可以来自你的项目引用的其他程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="2f105-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="2f105-108">与允许多重继承的语言不同，Visual Basic 只允许在类中进行单一继承;也就是说，派生类只能有一个基类。</span><span class="sxs-lookup"><span data-stu-id="2f105-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="2f105-109">尽管类中不允许使用多个继承，但类可实现多个接口，这些接口可以有效地实现相同的结束。</span><span class="sxs-lookup"><span data-stu-id="2f105-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="2f105-110">若要防止公开基类中的受限制项，派生类的访问类型必须等于或大于其基类的限制。</span><span class="sxs-lookup"><span data-stu-id="2f105-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="2f105-111">例如， `Public` 类不能继承 `Friend` 或 `Private` 类，并且 `Friend` 类不能继承 `Private` 类。</span><span class="sxs-lookup"><span data-stu-id="2f105-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="2f105-112">继承修饰符</span><span class="sxs-lookup"><span data-stu-id="2f105-112">Inheritance Modifiers</span></span>

<span data-ttu-id="2f105-113">Visual Basic 引入了以下类级语句和修饰符来支持继承：</span><span class="sxs-lookup"><span data-stu-id="2f105-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="2f105-114">`Inherits`语句—指定基类。</span><span class="sxs-lookup"><span data-stu-id="2f105-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="2f105-115">`NotInheritable`修饰符-阻止程序员使用类作为基类。</span><span class="sxs-lookup"><span data-stu-id="2f105-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="2f105-116">`MustInherit`修饰符-指定此类仅用作基类。</span><span class="sxs-lookup"><span data-stu-id="2f105-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="2f105-117">`MustInherit`不能直接创建类的实例，它们只能作为派生类的基类实例来创建。</span><span class="sxs-lookup"><span data-stu-id="2f105-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="2f105-118">（其他编程语言，如 c + + 和 c #，请使用字词*抽象类*来描述此类。）</span><span class="sxs-lookup"><span data-stu-id="2f105-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="2f105-119">重写派生类中的属性和方法</span><span class="sxs-lookup"><span data-stu-id="2f105-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="2f105-120">默认情况下，派生类继承其基类的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="2f105-121">如果继承的属性或方法在派生类中具有不同的行为，则可以将其*重写*。</span><span class="sxs-lookup"><span data-stu-id="2f105-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="2f105-122">也就是说，您可以在派生类中定义方法的新实现。</span><span class="sxs-lookup"><span data-stu-id="2f105-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="2f105-123">下列修饰符用于控制如何重写属性和方法：</span><span class="sxs-lookup"><span data-stu-id="2f105-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="2f105-124">`Overridable`-允许在派生类中重写类中的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="2f105-125">`Overrides`-重写 `Overridable` 基类中定义的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="2f105-126">`NotOverridable`-防止在继承类中重写属性或方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="2f105-127">默认情况下， `Public` 方法为 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="2f105-128">`MustOverride`-要求派生类重写属性或方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="2f105-129">`MustOverride`使用关键字时，方法定义只包含 `Sub` 、 `Function` 或 `Property` 语句。</span><span class="sxs-lookup"><span data-stu-id="2f105-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="2f105-130">不允许使用其他语句，特别是没有 `End Sub` 或 `End Function` 语句。</span><span class="sxs-lookup"><span data-stu-id="2f105-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="2f105-131">`MustOverride`方法必须在类中声明 `MustInherit` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="2f105-132">假设您要定义用于处理工资单的类。</span><span class="sxs-lookup"><span data-stu-id="2f105-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="2f105-133">您可以定义一个泛型 `Payroll` 类，该类包含 `RunPayroll` 计算典型周工资单的方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="2f105-134">然后，你可以将 `Payroll` 用作更专业化类的基类 `BonusPayroll` ，这些类可在分发员工奖金时使用。</span><span class="sxs-lookup"><span data-stu-id="2f105-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="2f105-135">`BonusPayroll`类可以继承和重写 `PayEmployee` 基类中定义的方法 `Payroll` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="2f105-136">下面的示例定义一个基类 `Payroll,` 和一个派生类， `BonusPayroll` 后者重写继承的方法 `PayEmployee` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="2f105-137">过程将 `RunPayroll` 创建一个对象并将其传递 `Payroll` `BonusPayroll` 给一个函数，该函数 `Pay` 执行 `PayEmployee` 两个对象的方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="2f105-138">MyBase 关键字</span><span class="sxs-lookup"><span data-stu-id="2f105-138">The MyBase Keyword</span></span>

<span data-ttu-id="2f105-139">`MyBase`关键字的行为类似于引用类的当前实例的基类的对象变量。</span><span class="sxs-lookup"><span data-stu-id="2f105-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="2f105-140">`MyBase`经常用于访问派生类中被重写或隐藏的基类成员。</span><span class="sxs-lookup"><span data-stu-id="2f105-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="2f105-141">具体而言， `MyBase.New` 用于从派生类构造函数中显式调用基类构造函数。</span><span class="sxs-lookup"><span data-stu-id="2f105-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="2f105-142">例如，假设您正在设计一个派生类，该派生类重写从基类继承的方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="2f105-143">重写的方法可以调用基类中的方法并修改返回值，如下面的代码段所示：</span><span class="sxs-lookup"><span data-stu-id="2f105-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="2f105-144">以下列表描述了对使用的限制 `MyBase` ：</span><span class="sxs-lookup"><span data-stu-id="2f105-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="2f105-145">`MyBase`引用直接基类及其继承的成员。</span><span class="sxs-lookup"><span data-stu-id="2f105-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="2f105-146">它不能用于访问 `Private` 类中的成员。</span><span class="sxs-lookup"><span data-stu-id="2f105-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="2f105-147">`MyBase`是一个关键字，而不是实际的对象。</span><span class="sxs-lookup"><span data-stu-id="2f105-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="2f105-148">`MyBase`不能分配给变量、传递给过程或用于 `Is` 比较。</span><span class="sxs-lookup"><span data-stu-id="2f105-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="2f105-149">限定的方法不必 `MyBase` 在直接基类中定义，而是可以在间接继承基类中定义。</span><span class="sxs-lookup"><span data-stu-id="2f105-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="2f105-150">为了使由限定的引用 `MyBase` 正确编译，某些基类必须包含与调用中显示的参数的名称和类型匹配的方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="2f105-151">不能使用 `MyBase` 来调用 `MustOverride` 基类方法。</span><span class="sxs-lookup"><span data-stu-id="2f105-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="2f105-152">`MyBase`不能用于限定自身。</span><span class="sxs-lookup"><span data-stu-id="2f105-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="2f105-153">因此，以下代码无效：</span><span class="sxs-lookup"><span data-stu-id="2f105-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="2f105-154">`MyBase`不能用在模块中。</span><span class="sxs-lookup"><span data-stu-id="2f105-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="2f105-155">`MyBase`不能用于访问标记为的基类成员，前提是 `Friend` 基类在不同的程序集中。</span><span class="sxs-lookup"><span data-stu-id="2f105-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="2f105-156">有关详细信息和其他示例，请参阅[如何：访问被派生类隐藏的变量](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="2f105-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="2f105-157">MyClass 关键字</span><span class="sxs-lookup"><span data-stu-id="2f105-157">The MyClass Keyword</span></span>

<span data-ttu-id="2f105-158">`MyClass`关键字的行为类似于引用最初实现的类的当前实例的对象变量。</span><span class="sxs-lookup"><span data-stu-id="2f105-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="2f105-159">`MyClass`类似于 `Me` ，但中的每个方法和属性调用 `MyClass` 都被视为[NotOverridable](../../../language-reference/modifiers/notoverridable.md)方法或属性。</span><span class="sxs-lookup"><span data-stu-id="2f105-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="2f105-160">因此，方法或属性不受派生类中重写的影响。</span><span class="sxs-lookup"><span data-stu-id="2f105-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="2f105-161">`MyClass`是一个关键字，而不是实际的对象。</span><span class="sxs-lookup"><span data-stu-id="2f105-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="2f105-162">`MyClass`不能分配给变量、传递给过程或用于 `Is` 比较。</span><span class="sxs-lookup"><span data-stu-id="2f105-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="2f105-163">`MyClass`引用包含类及其继承的成员。</span><span class="sxs-lookup"><span data-stu-id="2f105-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="2f105-164">`MyClass`可用作成员的限定符 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="2f105-165">`MyClass`不能在方法中使用 `Shared` ，但可以在实例方法内部使用以访问类的共享成员。</span><span class="sxs-lookup"><span data-stu-id="2f105-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="2f105-166">`MyClass`不能用于标准模块。</span><span class="sxs-lookup"><span data-stu-id="2f105-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="2f105-167">`MyClass`可用于限定在基类中定义的方法，该方法没有该类中提供的方法的实现。</span><span class="sxs-lookup"><span data-stu-id="2f105-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="2f105-168">此类引用与方法具有相同的含义 `MyBase.` *Method*。</span><span class="sxs-lookup"><span data-stu-id="2f105-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="2f105-169">下面的示例比较 `Me` 和 `MyClass` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-169">The following example compares `Me` and `MyClass`.</span></span>

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

<span data-ttu-id="2f105-170">即使 `derivedClass` 重写 `testMethod` ， `MyClass` 中的关键字 `useMyClass` nullifies 重写的效果和编译器解析对基类版本的调用 `testMethod` 。</span><span class="sxs-lookup"><span data-stu-id="2f105-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f105-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f105-171">See also</span></span>

- [<span data-ttu-id="2f105-172">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="2f105-172">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="2f105-173">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="2f105-173">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
