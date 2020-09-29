---
title: 如何实现和调用自定义扩展方法 - C# 编程指南
description: 了解如何为任意 .NET 类型实现扩展方法。 客户端代码可通过添加对 DLL 的引用并添加 using 指令来使用方法。
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: de4cc423e1823351305a23f331b082aa66add1a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190431"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="729ab-104">如何实现和调用自定义扩展方法（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="729ab-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="729ab-105">本主题将介绍如何为任意 .NET 类型实现自定义扩展方法。</span><span class="sxs-lookup"><span data-stu-id="729ab-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="729ab-106">客户端代码可以通过以下方法使用扩展方法，添加包含这些扩展方法的 DLL 的引用，以及添加 [using](../../language-reference/keywords/using-directive.md) 指令，该指令指定在其中定义扩展方法的命名空间。</span><span class="sxs-lookup"><span data-stu-id="729ab-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="729ab-107">定义和调用扩展方法</span><span class="sxs-lookup"><span data-stu-id="729ab-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="729ab-108">定义包含扩展方法的静态[类](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="729ab-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="729ab-109">此类必须对客户端代码可见。</span><span class="sxs-lookup"><span data-stu-id="729ab-109">The class must be visible to client code.</span></span> <span data-ttu-id="729ab-110">有关可访问性规则的详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="729ab-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="729ab-111">将扩展方法实现为静态方法，并且使其可见性至少与所在类的可见性相同。</span><span class="sxs-lookup"><span data-stu-id="729ab-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="729ab-112">此方法的第一个参数指定方法所操作的类型；此参数前面必须加上 [this](../../language-reference/keywords/this.md) 修饰符。</span><span class="sxs-lookup"><span data-stu-id="729ab-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="729ab-113">在调用代码中，添加 `using` 指令，用于指定包含扩展方法类的[命名空间](../../language-reference/keywords/namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="729ab-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="729ab-114">和调用类型的实例方法那样调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="729ab-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="729ab-115">请注意，第一个参数并不是由调用代码指定，因为它表示要在其上应用运算符的类型，并且编译器已经知道对象的类型。</span><span class="sxs-lookup"><span data-stu-id="729ab-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="729ab-116">你只需通过 `n` 提供形参 2 的实参。</span><span class="sxs-lookup"><span data-stu-id="729ab-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="729ab-117">示例</span><span class="sxs-lookup"><span data-stu-id="729ab-117">Example</span></span>  

 <span data-ttu-id="729ab-118">以下示例实现 `CustomExtensions.StringExtension` 类中名为 `WordCount` 的扩展方法。</span><span class="sxs-lookup"><span data-stu-id="729ab-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="729ab-119">此方法对 <xref:System.String> 类进行操作，该类指定为第一个方法参数。</span><span class="sxs-lookup"><span data-stu-id="729ab-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="729ab-120">将 `CustomExtensions` 命名空间导入应用程序命名空间，并在 `Main` 方法内部调用此方法。</span><span class="sxs-lookup"><span data-stu-id="729ab-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="729ab-121">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="729ab-121">.NET Security</span></span>  

 <span data-ttu-id="729ab-122">扩展方法不存在特定的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="729ab-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="729ab-123">始终不会将扩展方法用于模拟类型的现有方法，因为为了支持类型本身定义的实例或静态方法，已解决所有名称冲突。</span><span class="sxs-lookup"><span data-stu-id="729ab-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="729ab-124">扩展方法无法访问扩展类中的任何隐私数据。</span><span class="sxs-lookup"><span data-stu-id="729ab-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729ab-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="729ab-125">See also</span></span>

- [<span data-ttu-id="729ab-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="729ab-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="729ab-127">扩展方法</span><span class="sxs-lookup"><span data-stu-id="729ab-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="729ab-128">LINQ（语言集成查询）</span><span class="sxs-lookup"><span data-stu-id="729ab-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="729ab-129">静态类和静态类成员</span><span class="sxs-lookup"><span data-stu-id="729ab-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="729ab-130">受保护</span><span class="sxs-lookup"><span data-stu-id="729ab-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="729ab-131">internal</span><span class="sxs-lookup"><span data-stu-id="729ab-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="729ab-132">public</span><span class="sxs-lookup"><span data-stu-id="729ab-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="729ab-133">this</span><span class="sxs-lookup"><span data-stu-id="729ab-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="729ab-134">namespace</span><span class="sxs-lookup"><span data-stu-id="729ab-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
