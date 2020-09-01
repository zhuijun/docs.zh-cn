---
description: 可访问性级别的使用限制 - C# 参考
title: 可访问性级别的使用限制 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 542e463e41c70f2e8aed5c20dc1294e296a88518
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136989"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="39dd7-103">可访问性级别的使用限制（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="39dd7-103">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="39dd7-104">在声明中指定类型时，检查类型的可访问性级别是否依赖于成员或其他类型的可访问性级别。</span><span class="sxs-lookup"><span data-stu-id="39dd7-104">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="39dd7-105">例如，直接基类必须至少具有与派生类相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-105">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="39dd7-106">以下声明会导致编译器错误，因为基类 `BaseClass` 的可访问性低于 `MyClass`：</span><span class="sxs-lookup"><span data-stu-id="39dd7-106">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="39dd7-107">下表汇总了对已声明可访问性级别的限制。</span><span class="sxs-lookup"><span data-stu-id="39dd7-107">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="39dd7-108">上下文</span><span class="sxs-lookup"><span data-stu-id="39dd7-108">Context</span></span>|<span data-ttu-id="39dd7-109">备注</span><span class="sxs-lookup"><span data-stu-id="39dd7-109">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="39dd7-110">类</span><span class="sxs-lookup"><span data-stu-id="39dd7-110">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="39dd7-111">类类型的直接基类必须至少具有与类类型本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-111">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="39dd7-112">接口</span><span class="sxs-lookup"><span data-stu-id="39dd7-112">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="39dd7-113">接口类型的显式基接口必须至少具有与接口类型本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-113">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="39dd7-114">委托</span><span class="sxs-lookup"><span data-stu-id="39dd7-114">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="39dd7-115">委托类型的返回类型和参数类型必须至少具有与委托类型本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-115">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="39dd7-116">常量</span><span class="sxs-lookup"><span data-stu-id="39dd7-116">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="39dd7-117">常量的类型必须至少具有与常量本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-117">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="39dd7-118">字段</span><span class="sxs-lookup"><span data-stu-id="39dd7-118">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="39dd7-119">字段的类型必须至少具有与字段本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-119">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="39dd7-120">方法</span><span class="sxs-lookup"><span data-stu-id="39dd7-120">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="39dd7-121">方法的返回类型和参数类型必须至少具有与方法本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-121">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="39dd7-122">属性</span><span class="sxs-lookup"><span data-stu-id="39dd7-122">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="39dd7-123">属性的类型必须至少具有与属性本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-123">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="39dd7-124">事件</span><span class="sxs-lookup"><span data-stu-id="39dd7-124">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="39dd7-125">事件的类型必须至少具有与事件本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-125">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="39dd7-126">索引器</span><span class="sxs-lookup"><span data-stu-id="39dd7-126">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="39dd7-127">索引器的类型和参数类型必须至少具有与索引器本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-127">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="39dd7-128">运算符</span><span class="sxs-lookup"><span data-stu-id="39dd7-128">Operators</span></span>](../operators/index.md)|<span data-ttu-id="39dd7-129">运算符的类型和参数类型必须至少具有与运算符本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-129">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="39dd7-130">构造函数</span><span class="sxs-lookup"><span data-stu-id="39dd7-130">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="39dd7-131">构造函数的参数类型必须至少具有与构造函数本身相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="39dd7-131">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="39dd7-132">示例</span><span class="sxs-lookup"><span data-stu-id="39dd7-132">Example</span></span>

<span data-ttu-id="39dd7-133">下面的示例包含不同类型的错误声明。</span><span class="sxs-lookup"><span data-stu-id="39dd7-133">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="39dd7-134">每个声明后的注释指示预期编译器错误。</span><span class="sxs-lookup"><span data-stu-id="39dd7-134">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="39dd7-135">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="39dd7-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="39dd7-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="39dd7-136">See also</span></span>

- [<span data-ttu-id="39dd7-137">C# 参考</span><span class="sxs-lookup"><span data-stu-id="39dd7-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="39dd7-138">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="39dd7-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="39dd7-139">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="39dd7-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="39dd7-140">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="39dd7-140">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="39dd7-141">可访问性域</span><span class="sxs-lookup"><span data-stu-id="39dd7-141">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="39dd7-142">可访问性级别</span><span class="sxs-lookup"><span data-stu-id="39dd7-142">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="39dd7-143">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="39dd7-143">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="39dd7-144">public</span><span class="sxs-lookup"><span data-stu-id="39dd7-144">public</span></span>](public.md)
- [<span data-ttu-id="39dd7-145">private</span><span class="sxs-lookup"><span data-stu-id="39dd7-145">private</span></span>](private.md)
- [<span data-ttu-id="39dd7-146">受保护</span><span class="sxs-lookup"><span data-stu-id="39dd7-146">protected</span></span>](protected.md)
- [<span data-ttu-id="39dd7-147">internal</span><span class="sxs-lookup"><span data-stu-id="39dd7-147">internal</span></span>](internal.md)
