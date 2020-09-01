---
description: abstract - C# 参考
title: abstract - C# 参考
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 095c4dea838aff4f14833d78fb10a2f831cf5173
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127199"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="ce88f-103">abstract（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="ce88f-103">abstract (C# Reference)</span></span>
<span data-ttu-id="ce88f-104">`abstract` 修饰符指示被修改内容的实现已丢失或不完整。</span><span class="sxs-lookup"><span data-stu-id="ce88f-104">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="ce88f-105">abstract 修饰符可用于类、方法、属性、索引和事件。</span><span class="sxs-lookup"><span data-stu-id="ce88f-105">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="ce88f-106">在类声明中使用 `abstract` 修饰符来指示某个类仅用作其他类的基类，而不用于自行进行实例化。</span><span class="sxs-lookup"><span data-stu-id="ce88f-106">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="ce88f-107">标记为抽象的成员必须由派生自抽象类的非抽象类来实现。</span><span class="sxs-lookup"><span data-stu-id="ce88f-107">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="ce88f-108">示例</span><span class="sxs-lookup"><span data-stu-id="ce88f-108">Example</span></span>  
 <span data-ttu-id="ce88f-109">在此示例中，类 `Square` 必须提供 `GetArea` 的实现，因为它派生自 `Shape`：</span><span class="sxs-lookup"><span data-stu-id="ce88f-109">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="ce88f-110">抽象类具有以下功能：</span><span class="sxs-lookup"><span data-stu-id="ce88f-110">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="ce88f-111">抽象类不能实例化。</span><span class="sxs-lookup"><span data-stu-id="ce88f-111">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="ce88f-112">抽象类可能包含抽象方法和访问器。</span><span class="sxs-lookup"><span data-stu-id="ce88f-112">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="ce88f-113">无法使用 [sealed](./sealed.md) 修饰符来修改抽象类，因为两个修饰符的含义相反。</span><span class="sxs-lookup"><span data-stu-id="ce88f-113">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="ce88f-114">`sealed` 修饰符阻止类被继承，而 `abstract` 修饰符要求类被继承。</span><span class="sxs-lookup"><span data-stu-id="ce88f-114">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="ce88f-115">派生自抽象类的非抽象类，必须包含全部已继承的抽象方法和访问器的实际实现。</span><span class="sxs-lookup"><span data-stu-id="ce88f-115">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="ce88f-116">在方法或属性声明中使用 `abstract` 修饰符，以指示该方法或属性不包含实现。</span><span class="sxs-lookup"><span data-stu-id="ce88f-116">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="ce88f-117">抽象方法具有以下功能：</span><span class="sxs-lookup"><span data-stu-id="ce88f-117">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="ce88f-118">抽象方法是隐式的虚拟方法。</span><span class="sxs-lookup"><span data-stu-id="ce88f-118">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="ce88f-119">只有抽象类中才允许抽象方法声明。</span><span class="sxs-lookup"><span data-stu-id="ce88f-119">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="ce88f-120">由于抽象方法声明不提供实际的实现，因此没有方法主体；方法声明仅以分号结尾，且签名后没有大括号 ({ })。</span><span class="sxs-lookup"><span data-stu-id="ce88f-120">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="ce88f-121">例如：</span><span class="sxs-lookup"><span data-stu-id="ce88f-121">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="ce88f-122">实现由方法 [override](./override.md) 提供，它是非抽象类的成员。</span><span class="sxs-lookup"><span data-stu-id="ce88f-122">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="ce88f-123">在抽象方法声明中使用 [static](./static.md) 或 [virtual](./virtual.md) 修饰符是错误的。</span><span class="sxs-lookup"><span data-stu-id="ce88f-123">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="ce88f-124">除了声明和调用语法方面不同外，抽象属性的行为与抽象方法相似。</span><span class="sxs-lookup"><span data-stu-id="ce88f-124">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="ce88f-125">在静态属性上使用 `abstract` 修饰符是错误的。</span><span class="sxs-lookup"><span data-stu-id="ce88f-125">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="ce88f-126">通过包含使用 [override](./override.md) 修饰符的属性声明，可在派生类中重写抽象继承属性。</span><span class="sxs-lookup"><span data-stu-id="ce88f-126">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="ce88f-127">有关抽象类的详细信息，请参阅[抽象类、密封类及类成员](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="ce88f-127">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="ce88f-128">抽象类必须为所有接口成员提供实现。</span><span class="sxs-lookup"><span data-stu-id="ce88f-128">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="ce88f-129">实现接口的抽象类有可能将接口方法映射到抽象方法上。</span><span class="sxs-lookup"><span data-stu-id="ce88f-129">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="ce88f-130">例如：</span><span class="sxs-lookup"><span data-stu-id="ce88f-130">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="ce88f-131">示例</span><span class="sxs-lookup"><span data-stu-id="ce88f-131">Example</span></span>  
 <span data-ttu-id="ce88f-132">在此示例中，类 `DerivedClass` 派生自抽象类 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="ce88f-132">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="ce88f-133">抽象类包含抽象方法 `AbstractMethod`，以及两个抽象属性 `X` 和 `Y`。</span><span class="sxs-lookup"><span data-stu-id="ce88f-133">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="ce88f-134">在前面的示例中，如果你尝试通过使用如下语句来实例化抽象类：</span><span class="sxs-lookup"><span data-stu-id="ce88f-134">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="ce88f-135">将遇到一个错误，告知编译器无法创建抽象类“BaseClass”的实例。</span><span class="sxs-lookup"><span data-stu-id="ce88f-135">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ce88f-136">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="ce88f-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ce88f-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce88f-137">See also</span></span>

- [<span data-ttu-id="ce88f-138">C# 参考</span><span class="sxs-lookup"><span data-stu-id="ce88f-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce88f-139">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="ce88f-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce88f-140">修饰符</span><span class="sxs-lookup"><span data-stu-id="ce88f-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ce88f-141">virtual</span><span class="sxs-lookup"><span data-stu-id="ce88f-141">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="ce88f-142">override</span><span class="sxs-lookup"><span data-stu-id="ce88f-142">override</span></span>](./override.md)
- [<span data-ttu-id="ce88f-143">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="ce88f-143">C# Keywords</span></span>](./index.md)
