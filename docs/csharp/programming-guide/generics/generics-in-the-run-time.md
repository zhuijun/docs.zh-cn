---
title: 运行时中的泛型 - C# 编程指南
description: 了解运行时中的泛型类型。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: 8e072e7aa53177929dda0be931beb85863b6a12e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299222"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a><span data-ttu-id="000ce-104">运行时中的泛型（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="000ce-104">Generics in the Run Time (C# Programming Guide)</span></span>
<span data-ttu-id="000ce-105">泛型类型或方法编译为 Microsoft 中间语言 (MSIL) 时，它包含将其标识为具有类型参数的元数据。</span><span class="sxs-lookup"><span data-stu-id="000ce-105">When a generic type or method is compiled into Microsoft intermediate language (MSIL), it contains metadata that identifies it as having type parameters.</span></span> <span data-ttu-id="000ce-106">如何使用泛型类型的 MSIL 根据所提供的类型参数是值类型还是引用类型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="000ce-106">How the MSIL for a generic type is used differs based on whether the supplied type parameter is a value type or reference type.</span></span>  
  
 <span data-ttu-id="000ce-107">使用值类型作为参数首次构造泛型类型时，运行时创建专用的泛型类型，MSIL 内的适当位置替换提供的一个或多个参数。</span><span class="sxs-lookup"><span data-stu-id="000ce-107">When a generic type is first constructed with a value type as a parameter, the runtime creates a specialized generic type with the supplied parameter or parameters substituted in the appropriate locations in the MSIL.</span></span> <span data-ttu-id="000ce-108">为每个用作参数的唯一值类型一次创建专用化泛型类型。</span><span class="sxs-lookup"><span data-stu-id="000ce-108">Specialized generic types are created one time for each unique value type that is used as a parameter.</span></span>  
  
 <span data-ttu-id="000ce-109">例如，假定程序代码声明了一个由整数构造的堆栈：</span><span class="sxs-lookup"><span data-stu-id="000ce-109">For example, suppose your program code declared a stack that is constructed of integers:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 <span data-ttu-id="000ce-110">此时，运行时生成一个专用版 <xref:System.Collections.Generic.Stack%601> 类，其中用整数相应地替换其参数。</span><span class="sxs-lookup"><span data-stu-id="000ce-110">At this point, the runtime generates a specialized version of the <xref:System.Collections.Generic.Stack%601> class that has the integer substituted appropriately for its parameter.</span></span> <span data-ttu-id="000ce-111">现在，每当程序代码使用整数堆栈时，运行时都重新使用已生成的专用 <xref:System.Collections.Generic.Stack%601> 类。</span><span class="sxs-lookup"><span data-stu-id="000ce-111">Now, whenever your program code uses a stack of integers, the runtime reuses the generated specialized <xref:System.Collections.Generic.Stack%601> class.</span></span> <span data-ttu-id="000ce-112">在下面的示例中创建了两个整数堆栈实例，且它们共用 `Stack<int>` 代码的一个实例：</span><span class="sxs-lookup"><span data-stu-id="000ce-112">In the following example, two instances of a stack of integers are created, and they share a single instance of the `Stack<int>` code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 <span data-ttu-id="000ce-113">但是，假定在代码中另一点上再创建一个将不同值类型（例如 `long` 或用户定义结构）作为参数的 <xref:System.Collections.Generic.Stack%601> 类。</span><span class="sxs-lookup"><span data-stu-id="000ce-113">However, suppose that another <xref:System.Collections.Generic.Stack%601> class with a different value type such as a `long` or a user-defined structure as its parameter is created at another point in your code.</span></span> <span data-ttu-id="000ce-114">其结果是，运行时在 MSIL 中生成另一个版本的泛型类型并在适当位置替换 `long`。</span><span class="sxs-lookup"><span data-stu-id="000ce-114">As a result, the runtime generates another version of the generic type and substitutes a `long` in the appropriate locations in MSIL.</span></span> <span data-ttu-id="000ce-115">转换已不再必要，因为每个专用化泛型类本机包含值类型。</span><span class="sxs-lookup"><span data-stu-id="000ce-115">Conversions are no longer necessary because each specialized generic class natively contains the value type.</span></span>  
  
 <span data-ttu-id="000ce-116">对于引用类型，泛型的作用方式略有不同。</span><span class="sxs-lookup"><span data-stu-id="000ce-116">Generics work somewhat differently for reference types.</span></span> <span data-ttu-id="000ce-117">首次使用任意引用类型构造泛型类型时，运行时创建一个专用化泛型类型，用对象引用替换 MSIL 中的参数。</span><span class="sxs-lookup"><span data-stu-id="000ce-117">The first time a generic type is constructed with any reference type, the runtime creates a specialized generic type with object references substituted for the parameters in the MSIL.</span></span> <span data-ttu-id="000ce-118">之后，每次使用引用类型作为参数实例化已构造的类型时，无论何种类型，运行时皆重新使用先前创建的专用版泛型类型。</span><span class="sxs-lookup"><span data-stu-id="000ce-118">Then, every time that a constructed type is instantiated with a reference type as its parameter, regardless of what type it is, the runtime reuses the previously created specialized version of the generic type.</span></span> <span data-ttu-id="000ce-119">原因可能在于所有引用大小相同。</span><span class="sxs-lookup"><span data-stu-id="000ce-119">This is possible because all references are the same size.</span></span>  
  
 <span data-ttu-id="000ce-120">例如，假定有两个引用类型、一个 `Customer` 类和一个 `Order` 类，并假定已创建 `Customer` 类型的堆栈：</span><span class="sxs-lookup"><span data-stu-id="000ce-120">For example, suppose you had two reference types, a `Customer` class and an `Order` class, and also suppose that you created a stack of `Customer` types:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 <span data-ttu-id="000ce-121">此时，运行时生成一个专用版 <xref:System.Collections.Generic.Stack%601> 类，此类存储之后会被填写的引用类型，而不是存储数据。</span><span class="sxs-lookup"><span data-stu-id="000ce-121">At this point, the runtime generates a specialized version of the <xref:System.Collections.Generic.Stack%601> class that stores object references that will be filled in later instead of storing data.</span></span> <span data-ttu-id="000ce-122">假定下一行代码创建另一引用类型的堆栈，其名为 `Order`：</span><span class="sxs-lookup"><span data-stu-id="000ce-122">Suppose the next line of code creates a stack of another reference type, which is named `Order`:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 <span data-ttu-id="000ce-123">不同于值类型，不会为 `Order` 类型创建 <xref:System.Collections.Generic.Stack%601> 类的另一专用版。</span><span class="sxs-lookup"><span data-stu-id="000ce-123">Unlike with value types, another specialized version of the <xref:System.Collections.Generic.Stack%601> class is not created for the `Order` type.</span></span> <span data-ttu-id="000ce-124">相反，创建专用版 <xref:System.Collections.Generic.Stack%601> 类的实例并将 `orders` 变量设置为引用此实例。</span><span class="sxs-lookup"><span data-stu-id="000ce-124">Instead, an instance of the specialized version of the <xref:System.Collections.Generic.Stack%601> class is created and the `orders` variable is set to reference it.</span></span> <span data-ttu-id="000ce-125">假定之后遇到一行创建 `Customer` 类型堆栈的代码：</span><span class="sxs-lookup"><span data-stu-id="000ce-125">Suppose that you then encountered a line of code to create a stack of a `Customer` type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 <span data-ttu-id="000ce-126">与之前使用通过 `Order` 类型创建的 <xref:System.Collections.Generic.Stack%601> 类一样，会创建专用 <xref:System.Collections.Generic.Stack%601> 类的另一个实例。</span><span class="sxs-lookup"><span data-stu-id="000ce-126">As with the previous use of the <xref:System.Collections.Generic.Stack%601> class created by using the `Order` type, another instance of the specialized <xref:System.Collections.Generic.Stack%601> class is created.</span></span> <span data-ttu-id="000ce-127">其中包含的指针设置为引用 `Customer` 类型大小的内存区。</span><span class="sxs-lookup"><span data-stu-id="000ce-127">The pointers that are contained therein are set to reference an area of memory the size of a `Customer` type.</span></span> <span data-ttu-id="000ce-128">由于引用类型的数量因程序不同而有较大差异，因此通过将编译器为引用类型的泛型类创建的专用类的数量减少至 1，泛型的 C# 实现可极大减少代码量。</span><span class="sxs-lookup"><span data-stu-id="000ce-128">Because the number of reference types can vary wildly from program to program, the C# implementation of generics greatly reduces the amount of code by reducing to one the number of specialized classes created by the compiler for generic classes of reference types.</span></span>  
  
 <span data-ttu-id="000ce-129">此外，使用值类型或引用类型参数实例化泛型 C# 类时，反射可在运行时对其进行查询，且其实际类型和类型参数皆可被确定。</span><span class="sxs-lookup"><span data-stu-id="000ce-129">Moreover, when a generic C# class is instantiated by using a value type or reference type parameter, reflection can query it at runtime and both its actual type and its type parameter can be ascertained.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000ce-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="000ce-130">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="000ce-131">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="000ce-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="000ce-132">泛型介绍</span><span class="sxs-lookup"><span data-stu-id="000ce-132">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="000ce-133">泛型</span><span class="sxs-lookup"><span data-stu-id="000ce-133">Generics</span></span>](../../../standard/generics/index.md)
