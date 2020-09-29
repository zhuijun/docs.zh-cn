---
title: 常量 - C# 编程指南
description: C# 中的常量是编译时文本值，这些值在程序编译后不会更改。 仅 C# 内置类型可为常量。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 9eff44f3260f0f50fef956ba60b01e2497d7d2dd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199206"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="1c4bc-104">常量（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="1c4bc-104">Constants (C# Programming Guide)</span></span>

<span data-ttu-id="1c4bc-105">常量是不可变的值，在编译时是已知的，在程序的生命周期内不会改变。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-105">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="1c4bc-106">常量使用 [const](../../language-reference/keywords/const.md) 修饰符声明。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-106">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="1c4bc-107">仅 C# [内置类型](../../language-reference/builtin-types/built-in-types.md)（不包括 <xref:System.Object?displayProperty=nameWithType>）可声明为 `const`。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-107">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="1c4bc-108">用户定义的类型（包括类、结构和数组）不能为 `const`。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-108">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="1c4bc-109">使用 [readonly](../../language-reference/keywords/readonly.md) 修饰符创建在运行时一次性（例如在构造函数中）初始化的类、结构或数组，此后不能更改。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-109">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="1c4bc-110">C# 不支持 `const` 方法、属性或事件。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-110">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="1c4bc-111">枚举类型使你能够为整数内置类型定义命名常量（例如 `int`、`uint`、`long` 等）。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-111">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="1c4bc-112">有关详细信息，请参阅[枚举](../../language-reference/builtin-types/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-112">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="1c4bc-113">常量在声明时必须初始化。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-113">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="1c4bc-114">例如：</span><span class="sxs-lookup"><span data-stu-id="1c4bc-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 <span data-ttu-id="1c4bc-115">在此示例中，常量 `Months` 始终为 12，即使类本身也无法更改它。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-115">In this example, the constant `Months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="1c4bc-116">实际上，当编译器遇到 C# 源代码中的常量标识符（例如，`Months`）时，它直接将文本值替换到它生成的中间语言 (IL) 代码中。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `Months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="1c4bc-117">因为运行时没有与常量相关联的变量地址，所以 `const` 字段不能通过引用传递，并且不能在表达式中显示为左值。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c4bc-118">引用其他代码（如 DLL）中定义的常量值时要格外小心。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="1c4bc-119">如果新版本的 DLL 定义了新的常量值，则程序仍将保留旧的文本值，直到根据新版本重新编译。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="1c4bc-120">可以同时声明多个同一类型的常量，例如：</span><span class="sxs-lookup"><span data-stu-id="1c4bc-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 <span data-ttu-id="1c4bc-121">如果不创建循环引用，则用于初始化常量的表达式可以引用另一个常量。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-121">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="1c4bc-122">例如：</span><span class="sxs-lookup"><span data-stu-id="1c4bc-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 <span data-ttu-id="1c4bc-123">可以将常量标记为[public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-123">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="1c4bc-124">这些访问修饰符定义该类的用户访问该常量的方式。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-124">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="1c4bc-125">有关详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-125">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="1c4bc-126">常量是作为[静态](../../language-reference/keywords/static.md)字段访问的，因为常量的值对于该类型的所有实例都是相同的。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-126">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="1c4bc-127">不使用 `static` 关键字来声明这些常量。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-127">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="1c4bc-128">不在定义常量的类中的表达式必须使用类名、句点和常量名称来访问该常量。</span><span class="sxs-lookup"><span data-stu-id="1c4bc-128">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="1c4bc-129">例如：</span><span class="sxs-lookup"><span data-stu-id="1c4bc-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1c4bc-130">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="1c4bc-130">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c4bc-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="1c4bc-131">See also</span></span>

- [<span data-ttu-id="1c4bc-132">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="1c4bc-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1c4bc-133">类和结构</span><span class="sxs-lookup"><span data-stu-id="1c4bc-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="1c4bc-134">属性</span><span class="sxs-lookup"><span data-stu-id="1c4bc-134">Properties</span></span>](./properties.md)
- [<span data-ttu-id="1c4bc-135">类型</span><span class="sxs-lookup"><span data-stu-id="1c4bc-135">Types</span></span>](../types/index.md)
- [<span data-ttu-id="1c4bc-136">readonly</span><span class="sxs-lookup"><span data-stu-id="1c4bc-136">readonly</span></span>](../../language-reference/keywords/readonly.md)
- [<span data-ttu-id="1c4bc-137">C# 不可变性（第一部分）：不可变性种类</span><span class="sxs-lookup"><span data-stu-id="1c4bc-137">Immutability in C# Part One: Kinds of Immutability</span></span>](/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
