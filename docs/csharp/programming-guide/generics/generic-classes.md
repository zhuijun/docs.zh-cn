---
title: 泛型类 - C# 编程指南
description: 了解在集合中使用的泛型类，如链接列表、哈希表、堆栈、队列和树。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 62e6e7afe0e795819b82c6c7a4f99260a8080efb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157416"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="de819-103">泛型类（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="de819-103">Generic Classes (C# Programming Guide)</span></span>

<span data-ttu-id="de819-104">泛型类封装不特定于特定数据类型的操作。</span><span class="sxs-lookup"><span data-stu-id="de819-104">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="de819-105">泛型类最常见用法是用于链接列表、哈希表、堆栈、队列和树等集合。</span><span class="sxs-lookup"><span data-stu-id="de819-105">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="de819-106">无论存储数据的类型如何，添加项和从集合删除项等操作的执行方式基本相同。</span><span class="sxs-lookup"><span data-stu-id="de819-106">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="de819-107">对于大多数需要集合类的方案，推荐做法是使用 .NET 类库中提供的集合类。</span><span class="sxs-lookup"><span data-stu-id="de819-107">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="de819-108">有关使用这些类的详细信息，请参阅 [.NET 中的泛型集合](../../../standard/generics/collections.md)。</span><span class="sxs-lookup"><span data-stu-id="de819-108">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="de819-109">通常，创建泛型类是从现有具体类开始，然后每次逐个将类型更改为类型参数，直到泛化和可用性达到最佳平衡。</span><span class="sxs-lookup"><span data-stu-id="de819-109">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="de819-110">创建自己的泛型类时，需要考虑以下重要注意事项：</span><span class="sxs-lookup"><span data-stu-id="de819-110">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="de819-111">要将哪些类型泛化为类型参数。</span><span class="sxs-lookup"><span data-stu-id="de819-111">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="de819-112">通常，可参数化的类型越多，代码就越灵活、其可重用性就越高。</span><span class="sxs-lookup"><span data-stu-id="de819-112">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="de819-113">但过度泛化会造成其他开发人员难以阅读或理解代码。</span><span class="sxs-lookup"><span data-stu-id="de819-113">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="de819-114">要将何种约束（如有）应用到类型参数（请参阅[类型参数的约束](./constraints-on-type-parameters.md)）。</span><span class="sxs-lookup"><span data-stu-id="de819-114">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="de819-115">其中一个有用的规则是，应用最大程度的约束，同时仍可处理必须处理的类型。</span><span class="sxs-lookup"><span data-stu-id="de819-115">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="de819-116">例如，如果知道泛型类仅用于引用类型，则请应用类约束。</span><span class="sxs-lookup"><span data-stu-id="de819-116">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="de819-117">这可防止将类意外用于值类型，并使你可在 `T` 上使用 `as` 运算符和检查 null 值。</span><span class="sxs-lookup"><span data-stu-id="de819-117">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="de819-118">是否将泛型行为分解为基类和子类。</span><span class="sxs-lookup"><span data-stu-id="de819-118">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="de819-119">因为泛型类可用作基类，所以非泛型类的相同设计注意事项在此也适用。</span><span class="sxs-lookup"><span data-stu-id="de819-119">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="de819-120">请参阅本主题后文有关从泛型基类继承的规则。</span><span class="sxs-lookup"><span data-stu-id="de819-120">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="de819-121">实现一个泛型接口还是多个泛型接口。</span><span class="sxs-lookup"><span data-stu-id="de819-121">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="de819-122">例如，如果要设计用于在基于泛型的集合中创建项的类，则可能必须实现一个接口，例如 <xref:System.IComparable%601>，其中 `T` 为类的类型。</span><span class="sxs-lookup"><span data-stu-id="de819-122">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="de819-123">有关简单泛型类的示例，请参阅[泛型介绍](./index.md)。</span><span class="sxs-lookup"><span data-stu-id="de819-123">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="de819-124">类型参数和约束的规则对于泛型类行为具有多种含义，尤其是在继承性和成员可访问性方面。</span><span class="sxs-lookup"><span data-stu-id="de819-124">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="de819-125">应当了解一些术语，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="de819-125">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="de819-126">对于泛型类 `Node<T>,`客户端代码可通过指定类型参数来引用类，创建封闭式构造类型 (`Node<int>`)。</span><span class="sxs-lookup"><span data-stu-id="de819-126">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="de819-127">或者，可以不指定类型参数（例如指定泛型基类时），创建开放式构造类型 (`Node<T>`)。</span><span class="sxs-lookup"><span data-stu-id="de819-127">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="de819-128">泛型类可继承自具体的封闭式构造或开放式构造基类：</span><span class="sxs-lookup"><span data-stu-id="de819-128">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="de819-129">非泛型类（即，具体类）可继承自封闭式构造基类，但不可继承自开放式构造类或类型参数，因为运行时客户端代码无法提供实例化基类所需的类型参数。</span><span class="sxs-lookup"><span data-stu-id="de819-129">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="de819-130">继承自开放式构造类型的泛型类必须对非此继承类共享的任何基类类型参数提供类型参数，如下方代码所示：</span><span class="sxs-lookup"><span data-stu-id="de819-130">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="de819-131">继承自开放式构造类型的泛型类必须指定作为基类型上约束超集或表示这些约束的约束：</span><span class="sxs-lookup"><span data-stu-id="de819-131">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="de819-132">泛型类型可使用多个类型参数和约束，如下所示：</span><span class="sxs-lookup"><span data-stu-id="de819-132">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="de819-133">开放式构造和封闭式构造类型可用作方法参数：</span><span class="sxs-lookup"><span data-stu-id="de819-133">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="de819-134">如果一个泛型类实现一个接口，则该类的所有实例均可强制转换为该接口。</span><span class="sxs-lookup"><span data-stu-id="de819-134">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="de819-135">泛型类是不变量。</span><span class="sxs-lookup"><span data-stu-id="de819-135">Generic classes are invariant.</span></span> <span data-ttu-id="de819-136">换而言之，如果一个输入参数指定 `List<BaseClass>`，且你尝试提供 `List<DerivedClass>`，则会出现编译时错误。</span><span class="sxs-lookup"><span data-stu-id="de819-136">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de819-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de819-137">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="de819-138">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="de819-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="de819-139">泛型</span><span class="sxs-lookup"><span data-stu-id="de819-139">Generics</span></span>](./index.md)
- <span data-ttu-id="de819-140">[Saving the State of Enumerators](/archive/blogs/wesdyer/saving-the-state-of-enumerators)（保存枚举器状态）</span><span class="sxs-lookup"><span data-stu-id="de819-140">[Saving the State of Enumerators](/archive/blogs/wesdyer/saving-the-state-of-enumerators)</span></span>
- <span data-ttu-id="de819-141">[An Inheritance Puzzle, Part One](/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)（继承测验，第一部分）</span><span class="sxs-lookup"><span data-stu-id="de819-141">[An Inheritance Puzzle, Part One](/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)</span></span>
