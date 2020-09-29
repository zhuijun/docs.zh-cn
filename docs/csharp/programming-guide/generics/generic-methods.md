---
title: 泛型方法 - C# 编程指南
description: 了解通过类型参数声明的方法（泛型方法）。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151462"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="3f702-104">泛型方法（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="3f702-104">Generic Methods (C# Programming Guide)</span></span>

<span data-ttu-id="3f702-105">泛型方法是通过类型参数声明的方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f702-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="3f702-106">如下示例演示使用类型参数的 `int` 调用方法的一种方式：</span><span class="sxs-lookup"><span data-stu-id="3f702-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="3f702-107">还可省略类型参数，编译器将推断类型参数。</span><span class="sxs-lookup"><span data-stu-id="3f702-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="3f702-108">如下 `Swap` 调用等效于之前的调用：</span><span class="sxs-lookup"><span data-stu-id="3f702-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="3f702-109">类型推理的相同规则适用于静态方法和实例方法。</span><span class="sxs-lookup"><span data-stu-id="3f702-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="3f702-110">编译器可基于传入的方法参数推断类型参数；而无法仅根据约束或返回值推断类型参数。</span><span class="sxs-lookup"><span data-stu-id="3f702-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="3f702-111">因此，类型推理不适用于不具有参数的方法。</span><span class="sxs-lookup"><span data-stu-id="3f702-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="3f702-112">类型推理发生在编译时，之后编译器尝试解析重载的方法签名。</span><span class="sxs-lookup"><span data-stu-id="3f702-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="3f702-113">编译器将类型推理逻辑应用于共用同一名称的所有泛型方法。</span><span class="sxs-lookup"><span data-stu-id="3f702-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="3f702-114">在重载解决方案步骤中，编译器仅包含在其上类型推理成功的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="3f702-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="3f702-115">在泛型类中，非泛型方法可访问类级别类型参数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f702-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="3f702-116">如果定义一个具有与包含类相同的类型参数的泛型方法，则编译器会生成警告 [CS0693](../../misc/cs0693.md)，因为在该方法范围内，向内 `T` 提供的参数会隐藏向外 `T` 提供的参数。</span><span class="sxs-lookup"><span data-stu-id="3f702-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="3f702-117">如果需要使用类型参数（而不是类实例化时提供的参数）调用泛型类方法所具备的灵活性，请考虑为此方法的类型参数提供另一标识符，如下方示例中 `GenericList2<T>` 所示。</span><span class="sxs-lookup"><span data-stu-id="3f702-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="3f702-118">使用约束在方法中的类型参数上实现更多专用操作。</span><span class="sxs-lookup"><span data-stu-id="3f702-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="3f702-119">此版 `Swap<T>` 现名为 `SwapIfGreater<T>`，仅可用于实现 <xref:System.IComparable%601> 的类型参数。</span><span class="sxs-lookup"><span data-stu-id="3f702-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="3f702-120">泛型方法可重载在数个泛型参数上。</span><span class="sxs-lookup"><span data-stu-id="3f702-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="3f702-121">例如，以下方法可全部位于同一类中：</span><span class="sxs-lookup"><span data-stu-id="3f702-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f702-122">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="3f702-122">C# Language Specification</span></span>  

 <span data-ttu-id="3f702-123">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/classes.md#methods)。</span><span class="sxs-lookup"><span data-stu-id="3f702-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f702-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="3f702-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3f702-125">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="3f702-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3f702-126">泛型介绍</span><span class="sxs-lookup"><span data-stu-id="3f702-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="3f702-127">方法</span><span class="sxs-lookup"><span data-stu-id="3f702-127">Methods</span></span>](../classes-and-structs/methods.md)
