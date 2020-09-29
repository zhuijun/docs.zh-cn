---
title: 泛型和反射 - C# 编程指南
description: 了解如何使用反射获取有关泛型类型的信息。 查看泛型反射的条款和条件的列表。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 5439412231ab1bf9ed523d6786af67984ab2d0c3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172965"
---
# <a name="generics-and-reflection-c-programming-guide"></a><span data-ttu-id="05586-104">泛型和反射（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="05586-104">Generics and Reflection (C# Programming Guide)</span></span>

<span data-ttu-id="05586-105">因为公共语言运行时 (CLR) 能够在运行时访问泛型类型信息，所以可以使用反射获取关于泛型类型的信息，方法与用于非泛型类型的方法相同。</span><span class="sxs-lookup"><span data-stu-id="05586-105">Because the Common Language Runtime (CLR) has access to generic type information at run time, you can use reflection to obtain information about generic types in the same way as for non-generic types.</span></span> <span data-ttu-id="05586-106">有关详细信息，请参阅[运行时中的泛型](./generics-in-the-run-time.md)。</span><span class="sxs-lookup"><span data-stu-id="05586-106">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="05586-107">在 .NET Framework 2.0 中，向 <xref:System.Type> 类添加了多个新成员来启用泛型类型的运行时信息。</span><span class="sxs-lookup"><span data-stu-id="05586-107">In .NET Framework 2.0, several new members were added to the <xref:System.Type> class to enable run-time information for generic types.</span></span> <span data-ttu-id="05586-108">有关如何使用这些方法和属性的详细信息，请参阅这些类的文档。</span><span class="sxs-lookup"><span data-stu-id="05586-108">See the documentation on these classes for more information on how to use these methods and properties.</span></span> <span data-ttu-id="05586-109"><xref:System.Reflection.Emit> 命名空间还包含支持泛型的新成员。</span><span class="sxs-lookup"><span data-stu-id="05586-109">The <xref:System.Reflection.Emit> namespace also contains new members that support generics.</span></span> <span data-ttu-id="05586-110">请参阅[如何：使用反射发出定义泛型类型](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)。</span><span class="sxs-lookup"><span data-stu-id="05586-110">See [How to: Define a Generic Type with Reflection Emit](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).</span></span>  
  
 <span data-ttu-id="05586-111">有关泛型反射中使用的术语的固定条件列表，请参阅 <xref:System.Type.IsGenericType%2A> 属性注解。</span><span class="sxs-lookup"><span data-stu-id="05586-111">For a list of the invariant conditions for terms used in generic reflection, see the <xref:System.Type.IsGenericType%2A> property remarks.</span></span>  
  
|<span data-ttu-id="05586-112">System.Type 成员名称</span><span class="sxs-lookup"><span data-stu-id="05586-112">System.Type Member Name</span></span>|<span data-ttu-id="05586-113">描述</span><span class="sxs-lookup"><span data-stu-id="05586-113">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|<span data-ttu-id="05586-114">如果类型是泛型，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="05586-114">Returns true if a type is generic.</span></span>|  
|<xref:System.Type.GetGenericArguments%2A>|<span data-ttu-id="05586-115">返回 `Type` 对象的数组，这些对象表示为构造类型提供的类型实参或泛型类型定义的类型形参。</span><span class="sxs-lookup"><span data-stu-id="05586-115">Returns an array of `Type` objects that represent the type arguments supplied for a constructed type, or the type parameters of a generic type definition.</span></span>|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|<span data-ttu-id="05586-116">返回当前构造类型的基础泛型类型定义。</span><span class="sxs-lookup"><span data-stu-id="05586-116">Returns the underlying generic type definition for the current constructed type.</span></span>|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|<span data-ttu-id="05586-117">返回表示当前泛型类型参数约束的 `Type` 对象的数组。</span><span class="sxs-lookup"><span data-stu-id="05586-117">Returns an array of `Type` objects that represent the constraints on the current generic type parameter.</span></span>|  
|<xref:System.Type.ContainsGenericParameters%2A>|<span data-ttu-id="05586-118">如果类型或任何其封闭类型或方法包含未提供特定类型的类型参数，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="05586-118">Returns true if the type or any of its enclosing types or methods contain type parameters for which specific types have not been supplied.</span></span>|  
|<xref:System.Type.GenericParameterAttributes%2A>|<span data-ttu-id="05586-119">获取描述当前泛型类型参数的特殊约束的 `GenericParameterAttributes` 标志组合。</span><span class="sxs-lookup"><span data-stu-id="05586-119">Gets a combination of `GenericParameterAttributes` flags that describe the special constraints of the current generic type parameter.</span></span>|  
|<xref:System.Type.GenericParameterPosition%2A>|<span data-ttu-id="05586-120">对于表示类型参数的 `Type` 对象，获取类型参数在声明其类型参数的泛型类型定义或泛型方法定义的类型参数列表中的位置。</span><span class="sxs-lookup"><span data-stu-id="05586-120">For a `Type` object that represents a type parameter, gets the position of the type parameter in the type parameter list of the generic type definition or generic method definition that declared the type parameter.</span></span>|  
|<xref:System.Type.IsGenericParameter%2A>|<span data-ttu-id="05586-121">获取一个值，该值指示当前 `Type` 是否表示泛型类型或方法定义中的类型参数。</span><span class="sxs-lookup"><span data-stu-id="05586-121">Gets a value that indicates whether the current `Type` represents a type parameter of a generic type or method definition.</span></span>|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|<span data-ttu-id="05586-122">获取一个值，该值指示当前 <xref:System.Type> 是否表示可以用来构造其他泛型类型的泛型类型定义。</span><span class="sxs-lookup"><span data-stu-id="05586-122">Gets a value that indicates whether the current <xref:System.Type> represents a generic type definition, from which other generic types can be constructed.</span></span> <span data-ttu-id="05586-123">如果该类型表示泛型类型的定义，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="05586-123">Returns true if the type represents the definition of a generic type.</span></span>|  
|<xref:System.Type.DeclaringMethod%2A>|<span data-ttu-id="05586-124">返回定义当前泛型类型参数的泛型方法，如果类型参数未由泛型方法定义，则返回 null。</span><span class="sxs-lookup"><span data-stu-id="05586-124">Returns the generic method that defined the current generic type parameter, or null if the type parameter was not defined by a generic method.</span></span>|  
|<xref:System.Type.MakeGenericType%2A>|<span data-ttu-id="05586-125">替代由当前泛型类型定义的类型参数组成的类型数组的元素，并返回表示结果构造类型的 <xref:System.Type> 对象。</span><span class="sxs-lookup"><span data-stu-id="05586-125">Substitutes the elements of an array of types for the type parameters of the current generic type definition, and returns a <xref:System.Type> object representing the resulting constructed type.</span></span>|  
  
 <span data-ttu-id="05586-126">此外，<xref:System.Reflection.MethodInfo> 类的成员还为泛型方法启用运行时信息。</span><span class="sxs-lookup"><span data-stu-id="05586-126">In addition, members of the <xref:System.Reflection.MethodInfo> class enable run-time information for generic methods.</span></span> <span data-ttu-id="05586-127">有关用于反射泛型方法的术语的固定条件列表，请参阅 <xref:System.Reflection.MethodBase.IsGenericMethod%2A> 属性注解。</span><span class="sxs-lookup"><span data-stu-id="05586-127">See the <xref:System.Reflection.MethodBase.IsGenericMethod%2A> property remarks for a list of invariant conditions for terms used to reflect on generic methods.</span></span>  
  
|<span data-ttu-id="05586-128">System.Reflection.MemberInfo 成员名称</span><span class="sxs-lookup"><span data-stu-id="05586-128">System.Reflection.MemberInfo Member Name</span></span>|<span data-ttu-id="05586-129">描述</span><span class="sxs-lookup"><span data-stu-id="05586-129">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|<span data-ttu-id="05586-130">如果方法是泛型，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="05586-130">Returns true if a method is generic.</span></span>|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|<span data-ttu-id="05586-131">返回类型对象的数组，这些对象表示构造泛型方法的类型实参或泛型方法定义的类型形参。</span><span class="sxs-lookup"><span data-stu-id="05586-131">Returns an array of Type objects that represent the type arguments of a constructed generic method or the type parameters of a generic method definition.</span></span>|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|<span data-ttu-id="05586-132">返回当前构造方法的基础泛型方法定义。</span><span class="sxs-lookup"><span data-stu-id="05586-132">Returns the underlying generic method definition for the current constructed method.</span></span>|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|<span data-ttu-id="05586-133">如果方法或任何其封闭类型包含未提供特定类型的任何类型参数，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="05586-133">Returns true if the method or any of its enclosing types contain any type parameters for which specific types have not been supplied.</span></span>|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|<span data-ttu-id="05586-134">如果当前 <xref:System.Reflection.MethodInfo> 表示泛型方法的定义，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="05586-134">Returns true if the current <xref:System.Reflection.MethodInfo> represents the definition of a generic method.</span></span>|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|<span data-ttu-id="05586-135">用类型数组的元素替代当前泛型方法定义的类型参数，并返回表示结果构造方法的 <xref:System.Reflection.MethodInfo> 对象。</span><span class="sxs-lookup"><span data-stu-id="05586-135">Substitutes the elements of an array of types for the type parameters of the current generic method definition, and returns a <xref:System.Reflection.MethodInfo> object representing the resulting constructed method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05586-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="05586-136">See also</span></span>

- [<span data-ttu-id="05586-137">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="05586-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="05586-138">泛型</span><span class="sxs-lookup"><span data-stu-id="05586-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="05586-139">反射类型和泛型类型</span><span class="sxs-lookup"><span data-stu-id="05586-139">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [<span data-ttu-id="05586-140">泛型</span><span class="sxs-lookup"><span data-stu-id="05586-140">Generics</span></span>](../../../standard/generics/index.md)
