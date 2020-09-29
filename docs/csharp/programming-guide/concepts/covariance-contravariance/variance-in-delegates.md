---
title: 委托中的变体 (C#)
description: 了解如何通过 .NET 中的变体支持将方法签名与所有委托中的委托类型进行匹配。
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 359f7051aa2eeb5d2dc9fef3d9ccb1e4aaebfb5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167738"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="94f58-103">委托中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="94f58-103">Variance in Delegates (C#)</span></span>

<span data-ttu-id="94f58-104">.NET Framework 3.5 引入了变体支持，用于在 C# 中匹配所有委托的方法签名和委托类型。</span><span class="sxs-lookup"><span data-stu-id="94f58-104">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="94f58-105">这表明不仅可以将具有匹配签名的方法分配给委托，还可以将返回派生程度较大的派生类型的方法分配给委托（协变），或者如果方法所接受参数的派生类型所具有的派生程度小于委托类型指定的程度（逆变），也可将其分配给委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-105">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="94f58-106">这包括泛型委托和非泛型委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-106">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="94f58-107">例如，思考以下代码，该代码具有两个类和两个委托：泛型和非泛型。</span><span class="sxs-lookup"><span data-stu-id="94f58-107">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="94f58-108">创建 `SampleDelegate` 或 `SampleGenericDelegate<A, R>` 类型的委托时，可以将以下任一方法分配给这些委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-108">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="94f58-109">以下代码示例说明了方法签名与委托类型之间的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="94f58-109">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="94f58-110">有关更多示例，请参阅[在委托中使用变体 (C#)](./using-variance-in-delegates.md) 和[对 Func 和 Action 泛型委托使用变体 (C#)](./using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="94f58-110">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="94f58-111">泛型类型参数中的变体</span><span class="sxs-lookup"><span data-stu-id="94f58-111">Variance in Generic Type Parameters</span></span>  

 <span data-ttu-id="94f58-112">在 .NET Framework 4 或更高版本中，可以启用委托之间的隐式转换，以便在具有泛型类型参数所指定的不同类型按变体的要求继承自对方时，可以将这些类型的泛型委托分配给对方。</span><span class="sxs-lookup"><span data-stu-id="94f58-112">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="94f58-113">若要启用隐式转换，必须使用 `in` 或 `out` 关键字将委托中的泛型参数显式声明为协变或逆变。</span><span class="sxs-lookup"><span data-stu-id="94f58-113">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="94f58-114">以下代码示例演示了如何创建一个具有协变泛型类型参数的委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-114">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 <span data-ttu-id="94f58-115">如果仅使用变体支持来匹配方法签名和委托类型，且不使用 `in` 和 `out` 关键字，则可能会发现有时可以使用相同的 lambda 表达式或方法实例化委托，但不能将一个委托分配给另一个委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-115">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="94f58-116">在以下代码示例中，`SampleGenericDelegate<String>` 不能显式转换为 `SampleGenericDelegate<Object>`，尽管 `String` 继承 `Object`。</span><span class="sxs-lookup"><span data-stu-id="94f58-116">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="94f58-117">可以使用 `out` 关键字标记 泛型参数 `T` 解决此问题。</span><span class="sxs-lookup"><span data-stu-id="94f58-117">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a><span data-ttu-id="94f58-118">.NET 中具有变体类型参数的泛型委托</span><span class="sxs-lookup"><span data-stu-id="94f58-118">Generic Delegates That Have Variant Type Parameters in .NET</span></span>

<span data-ttu-id="94f58-119">.NET Framework 4 在几个现有泛型委托中引入了泛型类型参数的变体支持：</span><span class="sxs-lookup"><span data-stu-id="94f58-119">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="94f58-120"><xref:System> 命名空间的 `Action` 委托，例如 <xref:System.Action%601> 和 <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="94f58-120">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="94f58-121"><xref:System> 命名空间的 `Func` 委托，例如 <xref:System.Func%601> 和 <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="94f58-121">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="94f58-122"><xref:System.Predicate%601> 委托</span><span class="sxs-lookup"><span data-stu-id="94f58-122">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="94f58-123"><xref:System.Comparison%601> 委托</span><span class="sxs-lookup"><span data-stu-id="94f58-123">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="94f58-124"><xref:System.Converter%602> 委托</span><span class="sxs-lookup"><span data-stu-id="94f58-124">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="94f58-125">有关详细信息和示例，请参阅[对 Func 和 Action 泛型委托使用变体 (C#)](./using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="94f58-125">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="94f58-126">声明泛型委托中的变体类型参数</span><span class="sxs-lookup"><span data-stu-id="94f58-126">Declaring Variant Type Parameters in Generic Delegates</span></span>  

 <span data-ttu-id="94f58-127">如果泛型委托具有协变或逆变泛型类型参数，则该委托可被称为“变体泛型委托”。</span><span class="sxs-lookup"><span data-stu-id="94f58-127">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="94f58-128">可以使用 `out` 关键字声明泛型委托中的泛型类型参数协变。</span><span class="sxs-lookup"><span data-stu-id="94f58-128">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="94f58-129">协变类型只能用作方法返回类型，而不能用作方法参数的类型。</span><span class="sxs-lookup"><span data-stu-id="94f58-129">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="94f58-130">以下代码示例演示了如何声明协变泛型委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-130">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="94f58-131">可以使用 `in` 关键字声明泛型委托中的泛型类型参数逆变。</span><span class="sxs-lookup"><span data-stu-id="94f58-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="94f58-132">逆变类型只能用作方法参数的类型，而不能用作方法返回类型。</span><span class="sxs-lookup"><span data-stu-id="94f58-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="94f58-133">以下代码示例演示了如何声明逆变泛型委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="94f58-134">C# 中的 `ref`、`in` 和 `out` 参数不能标记为变体。</span><span class="sxs-lookup"><span data-stu-id="94f58-134">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="94f58-135">可以在同一个委托中支持变体和协变，但这只适用于不同类型的参数。</span><span class="sxs-lookup"><span data-stu-id="94f58-135">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="94f58-136">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="94f58-136">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="94f58-137">实例化和调用变体泛型委托</span><span class="sxs-lookup"><span data-stu-id="94f58-137">Instantiating and Invoking Variant Generic Delegates</span></span>  

 <span data-ttu-id="94f58-138">可以像实例化和调用固定委托一样，实例化和调用变体委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-138">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="94f58-139">在以下示例中，该委托通过 lambda 表达式进行实例化。</span><span class="sxs-lookup"><span data-stu-id="94f58-139">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="94f58-140">合并变体泛型委托</span><span class="sxs-lookup"><span data-stu-id="94f58-140">Combining Variant Generic Delegates</span></span>  

<span data-ttu-id="94f58-141">请勿合并变体委托。</span><span class="sxs-lookup"><span data-stu-id="94f58-141">Don't combine variant delegates.</span></span> <span data-ttu-id="94f58-142"><xref:System.Delegate.Combine%2A> 方法不支持变体委托转换，并且要求委托的类型完全相同。</span><span class="sxs-lookup"><span data-stu-id="94f58-142">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="94f58-143">这会导致在使用 <xref:System.Delegate.Combine%2A> 方法或使用 `+` 运算符合并委托时出现运行时异常，如以下代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="94f58-143">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="94f58-144">泛型类型参数中用于值和引用类型的变体</span><span class="sxs-lookup"><span data-stu-id="94f58-144">Variance in Generic Type Parameters for Value and Reference Types</span></span>  

 <span data-ttu-id="94f58-145">泛型类型参数的变体仅支持引用类型。</span><span class="sxs-lookup"><span data-stu-id="94f58-145">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="94f58-146">例如，`DVariant<int>` 不能隐式转换为 `DVariant<Object>` 或 `DVariant<long>`，因为整数是值类型。</span><span class="sxs-lookup"><span data-stu-id="94f58-146">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="94f58-147">以下示例演示了泛型类型参数中的变体不支持值类型。</span><span class="sxs-lookup"><span data-stu-id="94f58-147">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="94f58-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="94f58-148">See also</span></span>

- [<span data-ttu-id="94f58-149">泛型</span><span class="sxs-lookup"><span data-stu-id="94f58-149">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="94f58-150">对 Func 和 Action 泛型委托使用变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="94f58-150">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="94f58-151">如何合并委托（多播委托）</span><span class="sxs-lookup"><span data-stu-id="94f58-151">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
