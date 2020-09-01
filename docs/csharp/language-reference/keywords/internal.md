---
description: internal - C# 参考
title: internal - C# 参考
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 14722d66a65eb5f96118acf017dc877e657b2dd9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134570"
---
# <a name="internal-c-reference"></a><span data-ttu-id="13796-103">internal（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="13796-103">internal (C# Reference)</span></span>
<span data-ttu-id="13796-104">`internal` 关键字是类型和类型成员的[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="13796-104">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="13796-105">本页涵盖 `internal` 访问。</span><span class="sxs-lookup"><span data-stu-id="13796-105">This page covers `internal` access.</span></span> <span data-ttu-id="13796-106">`internal` 关键字也是 [`protected internal`](./protected-internal.md) 访问修饰符的一部分。</span><span class="sxs-lookup"><span data-stu-id="13796-106">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="13796-107">只有在同一程序集的文件中，内部类型或成员才可访问，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="13796-107">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="13796-108">有关 `internal` 和其他访问修饰符的比较，请参阅[可访问性级别](./accessibility-levels.md)和[访问修饰符](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="13796-108">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="13796-109">有关程序集的详细信息，请参阅 [.NET 中的程序集](../../../standard/assembly/index.md)。</span><span class="sxs-lookup"><span data-stu-id="13796-109">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="13796-110">内部访问通常用于基于组件的开发，因为它可使一组组件以私有方式进行协作，而不必向应用程序代码的其余部分公开。</span><span class="sxs-lookup"><span data-stu-id="13796-110">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="13796-111">例如，用于生成图形用户界面的框架可以提供 `Control` 和 `Form` 类，这两个类通过使用具有内部访问权限的成员进行协作。</span><span class="sxs-lookup"><span data-stu-id="13796-111">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="13796-112">由于这些成员是内部的，因此不会向正在使用框架的代码公开。</span><span class="sxs-lookup"><span data-stu-id="13796-112">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="13796-113">从定义具有内部访问权限的类型或成员的程序集外部引用该类型或成员是错误的。</span><span class="sxs-lookup"><span data-stu-id="13796-113">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13796-114">示例</span><span class="sxs-lookup"><span data-stu-id="13796-114">Example</span></span>  
 <span data-ttu-id="13796-115">此示例包含两个文件，即 `Assembly1.cs` 和 `Assembly1_a.cs`。</span><span class="sxs-lookup"><span data-stu-id="13796-115">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="13796-116">第一个文件包含内部基类 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="13796-116">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="13796-117">在第二个文件中，尝试实例化 `BaseClass` 会产生错误。</span><span class="sxs-lookup"><span data-stu-id="13796-117">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="13796-118">示例</span><span class="sxs-lookup"><span data-stu-id="13796-118">Example</span></span>  
 <span data-ttu-id="13796-119">在此示例中，使用在示例 1 中所用的相同文件，并将 `BaseClass` 的可访问性级别更改为 `public`。</span><span class="sxs-lookup"><span data-stu-id="13796-119">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="13796-120">另将成员 `intM` 的可访问性级别更改为 `internal`。</span><span class="sxs-lookup"><span data-stu-id="13796-120">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="13796-121">在此例中，可以实例化类，但不能访问内部成员。</span><span class="sxs-lookup"><span data-stu-id="13796-121">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="13796-122">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="13796-122">C# Language Specification</span></span>  

<span data-ttu-id="13796-123">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[声明的可访问性](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="13796-123">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="13796-124">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="13796-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13796-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="13796-125">See also</span></span>

- [<span data-ttu-id="13796-126">C# 参考</span><span class="sxs-lookup"><span data-stu-id="13796-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13796-127">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="13796-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13796-128">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="13796-128">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="13796-129">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="13796-129">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="13796-130">可访问性级别</span><span class="sxs-lookup"><span data-stu-id="13796-130">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="13796-131">修饰符</span><span class="sxs-lookup"><span data-stu-id="13796-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="13796-132">public</span><span class="sxs-lookup"><span data-stu-id="13796-132">public</span></span>](./public.md)
- [<span data-ttu-id="13796-133">private</span><span class="sxs-lookup"><span data-stu-id="13796-133">private</span></span>](./private.md)
- [<span data-ttu-id="13796-134">protected</span><span class="sxs-lookup"><span data-stu-id="13796-134">protected</span></span>](./protected.md)
