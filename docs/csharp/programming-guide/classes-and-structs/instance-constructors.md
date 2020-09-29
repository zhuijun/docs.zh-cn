---
title: 实例构造函数 - C# 编程指南
description: 使用 new 表达式创建类的对象时，可使用 C# 中的实例构造函数创建和初始化任意实例成员变量。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: f1845601f2a0237206d05e3cc3cbbca68492020c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186128"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="e15e7-103">实例构造函数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="e15e7-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="e15e7-104">使用 [new](../../language-reference/operators/new-operator.md) 表达式创建[类](../../language-reference/keywords/class.md)的对象时，实例构造函数可用于创建和初始化任意实例成员变量。</span><span class="sxs-lookup"><span data-stu-id="e15e7-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="e15e7-105">若要初始化[静态](../../language-reference/keywords/static.md)类或非静态类中的静态变量，请定义静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="e15e7-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="e15e7-106">有关详细信息，请参阅[静态构造函数](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="e15e7-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="e15e7-107">下面的示例演示了实例构造函数：</span><span class="sxs-lookup"><span data-stu-id="e15e7-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="e15e7-108">为清楚起见，此类包含公共字段。</span><span class="sxs-lookup"><span data-stu-id="e15e7-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="e15e7-109">建议在编程时不要使用公共字段，因为这种做法会使程序中任何位置的任何方法都可以不受限制、不经验证地访问对象的内部组件。</span><span class="sxs-lookup"><span data-stu-id="e15e7-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="e15e7-110">数据成员通常应当为私有的，并且只应通过类方法和属性来访问。</span><span class="sxs-lookup"><span data-stu-id="e15e7-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="e15e7-111">只要创建基于 `Coords` 类的对象，就会调用此实例构造函数。</span><span class="sxs-lookup"><span data-stu-id="e15e7-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="e15e7-112">诸如此类不带参数的构造函数称为“无参数构造函数”。</span><span class="sxs-lookup"><span data-stu-id="e15e7-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="e15e7-113">然而，提供其他构造函数通常十分有用。</span><span class="sxs-lookup"><span data-stu-id="e15e7-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="e15e7-114">例如，可以将构造函数添加到 `Coords` 类，以便可以为数据成员指定初始值：</span><span class="sxs-lookup"><span data-stu-id="e15e7-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="e15e7-115">这样便可以用默认或特定的初始值创建 `Coords` 对象，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e15e7-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="e15e7-116">如果某个类没有构造函数，则会自动生成一个无参数构造函数，并使用默认值来初始化对象字段。</span><span class="sxs-lookup"><span data-stu-id="e15e7-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="e15e7-117">例如，[int](../../language-reference/builtin-types/integral-numeric-types.md) 初始化为 0。</span><span class="sxs-lookup"><span data-stu-id="e15e7-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="e15e7-118">有关类型默认值的信息，请参阅 [C# 类型的默认值](../../language-reference/builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="e15e7-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="e15e7-119">由于 `Coords` 类的无参数构造函数将所有数据成员都初始化为零，因此可以将它完全移除，而不会更改类的工作方式。</span><span class="sxs-lookup"><span data-stu-id="e15e7-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="e15e7-120">本主题稍后部分的示例 1 中提供了使用多个构造函数的完整示例，示例 2 中提供了自动生成的构造函数的示例。</span><span class="sxs-lookup"><span data-stu-id="e15e7-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="e15e7-121">也可以用实例构造函数来调用基类的实例构造函数。</span><span class="sxs-lookup"><span data-stu-id="e15e7-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="e15e7-122">类构造函数可通过初始值设定项来调用基类的构造函数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e15e7-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="e15e7-123">在此示例中，`Circle` 类将半径和高度的值传递给 `Shape`（`Circle` 从它派生而来）提供的构造函数。</span><span class="sxs-lookup"><span data-stu-id="e15e7-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="e15e7-124">使用 `Shape` 和 `Circle` 的完整示例完整示例请见本主题中的示例 3。</span><span class="sxs-lookup"><span data-stu-id="e15e7-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="e15e7-125">示例 1</span><span class="sxs-lookup"><span data-stu-id="e15e7-125">Example 1</span></span>  

 <span data-ttu-id="e15e7-126">下面的示例说明包含两个类构造函数的类：一个类构造函数不带参数，另一个带有两个参数。</span><span class="sxs-lookup"><span data-stu-id="e15e7-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="e15e7-127">示例 2</span><span class="sxs-lookup"><span data-stu-id="e15e7-127">Example 2</span></span>  

 <span data-ttu-id="e15e7-128">在此示例中，`Person` 类没有任何构造函数；在这种情况下，将自动提供无参数构造函数，同时将字段初始化为它们的默认值。</span><span class="sxs-lookup"><span data-stu-id="e15e7-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="e15e7-129">请注意，`age` 的默认值为 `0`，`name` 的默认值为`null`。</span><span class="sxs-lookup"><span data-stu-id="e15e7-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="e15e7-130">示例 3</span><span class="sxs-lookup"><span data-stu-id="e15e7-130">Example 3</span></span>  

 <span data-ttu-id="e15e7-131">下面的示例说明使用基类初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="e15e7-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="e15e7-132">`Circle` 类派生自常规类 `Shape`，`Cylinder` 类派生自 `Circle` 类。</span><span class="sxs-lookup"><span data-stu-id="e15e7-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="e15e7-133">每个派生类的构造函数都使用其基类的初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="e15e7-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="e15e7-134">有关调用基类构造函数的更多示例，请参阅 [virtual](../../language-reference/keywords/virtual.md)、[override](../../language-reference/keywords/override.md) 和 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="e15e7-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15e7-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="e15e7-135">See also</span></span>

- [<span data-ttu-id="e15e7-136">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="e15e7-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e15e7-137">类和结构</span><span class="sxs-lookup"><span data-stu-id="e15e7-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e15e7-138">构造函数</span><span class="sxs-lookup"><span data-stu-id="e15e7-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e15e7-139">终结器</span><span class="sxs-lookup"><span data-stu-id="e15e7-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="e15e7-140">static</span><span class="sxs-lookup"><span data-stu-id="e15e7-140">static</span></span>](../../language-reference/keywords/static.md)
