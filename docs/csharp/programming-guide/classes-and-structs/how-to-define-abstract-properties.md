---
title: 如何定义抽象属性（C# 编程指南）
description: 了解如何定义 C# 中的 abstract 属性。 声明抽象属性意味着类支持属性。 派生类实现访问器。
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 4db71721495857c634e8090b986704d8a592b4e2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864392"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="e301d-105">如何定义抽象属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="e301d-105">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="e301d-106">以下示例演示如何定义[抽象](../../language-reference/keywords/abstract.md)属性。</span><span class="sxs-lookup"><span data-stu-id="e301d-106">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="e301d-107">抽象属性声明不提供属性访问器的实现，它声明该类支持属性，而将访问器实现留给派生类。</span><span class="sxs-lookup"><span data-stu-id="e301d-107">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="e301d-108">以下示例演示如何实现从基类继承抽象属性。</span><span class="sxs-lookup"><span data-stu-id="e301d-108">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="e301d-109">此示例由三个文件组成，其中每个文件都单独编译，产生的程序集由下一次编译引用：</span><span class="sxs-lookup"><span data-stu-id="e301d-109">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="e301d-110">abstractshape.cs：包含抽象 `Area` 属性的 `Shape` 类。</span><span class="sxs-lookup"><span data-stu-id="e301d-110">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="e301d-111">shapes.cs：`Shape` 类的子类。</span><span class="sxs-lookup"><span data-stu-id="e301d-111">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="e301d-112">shapetest.cs：测试程序，用于显示一些 `Shape` 派生对象的区域。</span><span class="sxs-lookup"><span data-stu-id="e301d-112">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="e301d-113">若要编译该示例，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e301d-113">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="e301d-114">这将创建可执行文件 shapetest.exe。</span><span class="sxs-lookup"><span data-stu-id="e301d-114">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e301d-115">示例</span><span class="sxs-lookup"><span data-stu-id="e301d-115">Example</span></span>  
 <span data-ttu-id="e301d-116">此文件声明 `Shape` 类，该类包含 `double` 类型的 `Area` 属性。</span><span class="sxs-lookup"><span data-stu-id="e301d-116">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="e301d-117">属性的修饰符放置在属性声明中。</span><span class="sxs-lookup"><span data-stu-id="e301d-117">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="e301d-118">例如：</span><span class="sxs-lookup"><span data-stu-id="e301d-118">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="e301d-119">声明抽象属性时（如本示例中的 `Area`），只需指明哪些属性访问器可用即可，不要实现它们。</span><span class="sxs-lookup"><span data-stu-id="e301d-119">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="e301d-120">在此示例中，仅 [get](../../language-reference/keywords/get.md) 访问器可用，因此该属性是只读属性。</span><span class="sxs-lookup"><span data-stu-id="e301d-120">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e301d-121">示例</span><span class="sxs-lookup"><span data-stu-id="e301d-121">Example</span></span>  
 <span data-ttu-id="e301d-122">下面的代码演示 `Shape` 的三个子类，并演示它们如何替代 `Area` 属性来提供自己的实现。</span><span class="sxs-lookup"><span data-stu-id="e301d-122">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="e301d-123">示例</span><span class="sxs-lookup"><span data-stu-id="e301d-123">Example</span></span>  
 <span data-ttu-id="e301d-124">下面的代码演示一个创建若干 `Shape` 派生对象并输出其区域的测试程序。</span><span class="sxs-lookup"><span data-stu-id="e301d-124">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e301d-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="e301d-125">See also</span></span>

- [<span data-ttu-id="e301d-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="e301d-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e301d-127">类和结构</span><span class="sxs-lookup"><span data-stu-id="e301d-127">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e301d-128">抽象类、密封类及类成员</span><span class="sxs-lookup"><span data-stu-id="e301d-128">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="e301d-129">属性</span><span class="sxs-lookup"><span data-stu-id="e301d-129">Properties</span></span>](./properties.md)
