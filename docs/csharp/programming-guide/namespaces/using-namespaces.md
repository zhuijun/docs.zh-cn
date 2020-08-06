---
title: using 命名空间 - C# 编程指南
description: 了解如何在 C# 编程中使用命名空间，例如访问命名空间、命名空间别名，以及使用命名空间控制范围。
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 86892f50e059c16ee9c133d7ba9f2716e11a8e56
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381692"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="8c13e-103">using 命名空间（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8c13e-103">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="8c13e-104">在 C# 编程中，命名空间在两个方面被大量使用。</span><span class="sxs-lookup"><span data-stu-id="8c13e-104">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="8c13e-105">首先，.NET 类使用命名空间来组织它的众多类。</span><span class="sxs-lookup"><span data-stu-id="8c13e-105">Firstly, the .NET classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="8c13e-106">其次，在较大的编程项目中，声明自己的命名空间可以帮助控制类名称和方法名称的范围。</span><span class="sxs-lookup"><span data-stu-id="8c13e-106">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="8c13e-107">访问命名空间</span><span class="sxs-lookup"><span data-stu-id="8c13e-107">Accessing namespaces</span></span>

 <span data-ttu-id="8c13e-108">大多数 C# 应用程序以 `using` 指令开头。</span><span class="sxs-lookup"><span data-stu-id="8c13e-108">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="8c13e-109">本部分列出了应用程序将频繁使用的命名空间，使程序员避免在每次使用包含在命名空间中的方法时都要指定完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="8c13e-109">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="8c13e-110">例如，通过包括行：</span><span class="sxs-lookup"><span data-stu-id="8c13e-110">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="8c13e-111">在程序的开始，程序员可以使用代码：</span><span class="sxs-lookup"><span data-stu-id="8c13e-111">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="8c13e-112">而不是：</span><span class="sxs-lookup"><span data-stu-id="8c13e-112">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="8c13e-113">命名空间别名</span><span class="sxs-lookup"><span data-stu-id="8c13e-113">Namespace aliases</span></span>

 <span data-ttu-id="8c13e-114">还可以使用 [`using` 指令](../../language-reference/keywords/using-directive.md)为命名空间创建别名。</span><span class="sxs-lookup"><span data-stu-id="8c13e-114">You can also use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="8c13e-115">使用[命名空间别名限定符 `::`](../../language-reference/operators/namespace-alias-qualifier.md) 访问已设置别名的命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="8c13e-115">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="8c13e-116">下面的示例演示如何创建和使用命名空间别名：</span><span class="sxs-lookup"><span data-stu-id="8c13e-116">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="8c13e-117">使用命名空间控制范围</span><span class="sxs-lookup"><span data-stu-id="8c13e-117">Using namespaces to control scope</span></span>

 <span data-ttu-id="8c13e-118">`namespace` 关键字用于声明范围。</span><span class="sxs-lookup"><span data-stu-id="8c13e-118">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="8c13e-119">在项目内创建范围有助于整理代码，并允许创建全局唯一类型。</span><span class="sxs-lookup"><span data-stu-id="8c13e-119">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="8c13e-120">在下面的示例中，名为 `SampleClass` 的类在两个命名空间中定义，其中一个嵌套在另一个之中。</span><span class="sxs-lookup"><span data-stu-id="8c13e-120">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="8c13e-121">[`.` 令牌](../../language-reference/operators/member-access-operators.md#member-access-expression-)用于区分调用的方法。</span><span class="sxs-lookup"><span data-stu-id="8c13e-121">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="8c13e-122">完全限定的名称</span><span class="sxs-lookup"><span data-stu-id="8c13e-122">Fully qualified names</span></span>

 <span data-ttu-id="8c13e-123">命名空间和类型具有指示逻辑层次结构的完全限定名称所描述的唯一标题。</span><span class="sxs-lookup"><span data-stu-id="8c13e-123">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="8c13e-124">例如，语句 `A.B` 意味着 `A` 是命名空间或类型的名称，而 `B` 嵌套在其中。</span><span class="sxs-lookup"><span data-stu-id="8c13e-124">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="8c13e-125">以下示例中具有嵌套的类和命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c13e-125">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="8c13e-126">完全限定名称表示为跟随每个实体的注释。</span><span class="sxs-lookup"><span data-stu-id="8c13e-126">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="8c13e-127">在前面的代码片段中：</span><span class="sxs-lookup"><span data-stu-id="8c13e-127">In the previous code segment:</span></span>  
  
- <span data-ttu-id="8c13e-128">命名空间 `N1` 是全局命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="8c13e-128">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="8c13e-129">其完全限定名称为 `N1`。</span><span class="sxs-lookup"><span data-stu-id="8c13e-129">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="8c13e-130">命名空间 `N2` 是 `N1` 的成员。</span><span class="sxs-lookup"><span data-stu-id="8c13e-130">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="8c13e-131">其完全限定名称为 `N1.N2`。</span><span class="sxs-lookup"><span data-stu-id="8c13e-131">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="8c13e-132">类 `C1` 是 `N1` 的成员。</span><span class="sxs-lookup"><span data-stu-id="8c13e-132">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="8c13e-133">其完全限定名称为 `N1.C1`。</span><span class="sxs-lookup"><span data-stu-id="8c13e-133">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="8c13e-134">类名 `C2` 在此代码中使用了两次。</span><span class="sxs-lookup"><span data-stu-id="8c13e-134">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="8c13e-135">但完全限定名称是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8c13e-135">However, the fully qualified names are unique.</span></span> <span data-ttu-id="8c13e-136">`C2` 的第一个实例在 `C1` 中声明；因此，其完全限定名称是：`N1.C1.C2`。</span><span class="sxs-lookup"><span data-stu-id="8c13e-136">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="8c13e-137">`C2` 的第二个实例在命名空间 `N2` 中声明；因此，其完全限定名称是 `N1.N2.C2`。</span><span class="sxs-lookup"><span data-stu-id="8c13e-137">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="8c13e-138">使用前面的代码段，可向命名空间 `N1.N2` 添加新的类成员 `C3`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c13e-138">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="8c13e-139">一般情况下，使用[命名空间别名限定符 `::`](../../language-reference/operators/namespace-alias-qualifier.md) 来引用命名空间别名，或使用 `global::` 来引用全局命名空间，以及使用 `.` 来限定类型或成员。</span><span class="sxs-lookup"><span data-stu-id="8c13e-139">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="8c13e-140">将 `::` 与引用类型而非引用命名空间的别名一起使用是错误的。</span><span class="sxs-lookup"><span data-stu-id="8c13e-140">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="8c13e-141">例如：</span><span class="sxs-lookup"><span data-stu-id="8c13e-141">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="8c13e-142">请记住，单词 `global` 不是预定义的别名；因此，`global.X` 不具有任何特殊含义。</span><span class="sxs-lookup"><span data-stu-id="8c13e-142">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="8c13e-143">仅当将其与 `::` 一起使用时，它才具有特殊意义。</span><span class="sxs-lookup"><span data-stu-id="8c13e-143">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="8c13e-144">定义名为 global 的别名时将生成编译器警告 CS0440，因为 `global::` 始终引用全局命名空间而非别名。</span><span class="sxs-lookup"><span data-stu-id="8c13e-144">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="8c13e-145">例如，以下行将生成该警告：</span><span class="sxs-lookup"><span data-stu-id="8c13e-145">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="8c13e-146">将 `::` 与别名一起使用是一个不错的主意，可防止意外引入其他类型。</span><span class="sxs-lookup"><span data-stu-id="8c13e-146">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="8c13e-147">例如，请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="8c13e-147">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="8c13e-148">这是可行的，但如果随后要引入名为 `Alias` 的类型，`Alias.` 将改为绑定到该类型。</span><span class="sxs-lookup"><span data-stu-id="8c13e-148">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="8c13e-149">使用 `Alias::Exception` 确保 `Alias` 被视为命名空间别名，而不被误解为类型。</span><span class="sxs-lookup"><span data-stu-id="8c13e-149">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="8c13e-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="8c13e-150">See also</span></span>

- [<span data-ttu-id="8c13e-151">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8c13e-151">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8c13e-152">命名空间</span><span class="sxs-lookup"><span data-stu-id="8c13e-152">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="8c13e-153">成员访问表达式</span><span class="sxs-lookup"><span data-stu-id="8c13e-153">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="8c13e-154">:: 运算符</span><span class="sxs-lookup"><span data-stu-id="8c13e-154">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="8c13e-155">外部别名</span><span class="sxs-lookup"><span data-stu-id="8c13e-155">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
