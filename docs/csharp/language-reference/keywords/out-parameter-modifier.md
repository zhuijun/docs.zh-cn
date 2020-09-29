---
description: out 参数修饰符 - C# 参考
title: out 参数修饰符 - C# 参考
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 6addfa3a654c0bb4e10213a3fb4fc0368f2570b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200181"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="5ef35-103">out 参数修饰符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="5ef35-103">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="5ef35-104">`out` 关键字通过引用传递参数。</span><span class="sxs-lookup"><span data-stu-id="5ef35-104">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="5ef35-105">它让形参成为实参的别名，这必须是变量。</span><span class="sxs-lookup"><span data-stu-id="5ef35-105">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="5ef35-106">换而言之，对形参执行的任何操作都是对实参执行的。</span><span class="sxs-lookup"><span data-stu-id="5ef35-106">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="5ef35-107">它与 [ref](ref.md) 关键字相似，只不过 `ref` 要求在传递之前初始化变量。</span><span class="sxs-lookup"><span data-stu-id="5ef35-107">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="5ef35-108">它也类似于 [in](in-parameter-modifier.md) 关键字，只不过 `in` 不允许通过调用方法来修改参数值。</span><span class="sxs-lookup"><span data-stu-id="5ef35-108">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="5ef35-109">若要使用 `out` 参数，方法定义和调用方法均必须显式使用 `out` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5ef35-109">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="5ef35-110">例如：</span><span class="sxs-lookup"><span data-stu-id="5ef35-110">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="5ef35-111">`out` 关键字也可与泛型类型参数结合使用，以指定该类型参数是协变参数。</span><span class="sxs-lookup"><span data-stu-id="5ef35-111">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="5ef35-112">有关在此上下文中使用 `out` 关键字的详细信息，请参阅 [out（泛型修饰符）](out-generic-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="5ef35-112">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="5ef35-113">作为 `out` 参数传递的变量在方法调用中传递之前不必进行初始化。</span><span class="sxs-lookup"><span data-stu-id="5ef35-113">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="5ef35-114">但是，被调用的方法需要在返回之前赋一个值。</span><span class="sxs-lookup"><span data-stu-id="5ef35-114">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="5ef35-115">`in`、`ref` 和 `out` 关键字不被视为用于重载决议的方法签名的一部分。</span><span class="sxs-lookup"><span data-stu-id="5ef35-115">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="5ef35-116">因此，如果唯一的不同是一个方法采用 `ref` 或 `in` 参数，而另一个方法采用 `out` 参数，则无法重载这两个方法。</span><span class="sxs-lookup"><span data-stu-id="5ef35-116">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="5ef35-117">例如，以下代码将不会编译：</span><span class="sxs-lookup"><span data-stu-id="5ef35-117">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="5ef35-118">但是，如果一个方法采用 `ref`、`in` 或 `out` 参数，而另一个方法采用其他参数，则可以完成重载，如：</span><span class="sxs-lookup"><span data-stu-id="5ef35-118">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="5ef35-119">编译器通过将调用站点上的参数修饰符与方法调用中使用的参数修饰符进行匹配，从而选择最佳重载。</span><span class="sxs-lookup"><span data-stu-id="5ef35-119">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="5ef35-120">属性不是变量，因此不能作为 `out` 参数传递。</span><span class="sxs-lookup"><span data-stu-id="5ef35-120">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="5ef35-121">不能将 `in`、`ref` 和 `out` 关键字用于以下几种方法：</span><span class="sxs-lookup"><span data-stu-id="5ef35-121">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="5ef35-122">异步方法，通过使用 [async](./async.md) 修饰符定义。</span><span class="sxs-lookup"><span data-stu-id="5ef35-122">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="5ef35-123">迭代器方法，包括 [yield return](./yield.md) 或 `yield break` 语句。</span><span class="sxs-lookup"><span data-stu-id="5ef35-123">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="5ef35-124">此外，[扩展方法](../../programming-guide/classes-and-structs/extension-methods.md)具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="5ef35-124">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="5ef35-125">不能对扩展方法的第一个参数使用 `out` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5ef35-125">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="5ef35-126">当参数不是结构或是不被约束为结构的泛型类型时，不能对扩展方法的第一个参数使用 `ref` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5ef35-126">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="5ef35-127">除非第一个参数是结构，否则不能使用 `in` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5ef35-127">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="5ef35-128">即使约束为结构，也不能对任何泛型类型使用 `in` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5ef35-128">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="5ef35-129">声明 `out` 参数</span><span class="sxs-lookup"><span data-stu-id="5ef35-129">Declaring `out` parameters</span></span>

<span data-ttu-id="5ef35-130">使用 `out` 参数声明方法是返回多个值的经典解决方法。</span><span class="sxs-lookup"><span data-stu-id="5ef35-130">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="5ef35-131">自 C# 7.0 起，可以考虑针对类似方案使用[值元组](../builtin-types/value-tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="5ef35-131">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="5ef35-132">下面的示例使用 `out` 返回具有单个方法调用的三个变量。</span><span class="sxs-lookup"><span data-stu-id="5ef35-132">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="5ef35-133">第三个参数分配为 null。</span><span class="sxs-lookup"><span data-stu-id="5ef35-133">The third argument is assigned to null.</span></span> <span data-ttu-id="5ef35-134">这使得方法可以有选择地返回值。</span><span class="sxs-lookup"><span data-stu-id="5ef35-134">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="5ef35-135">调用具有 `out` 参数的方法</span><span class="sxs-lookup"><span data-stu-id="5ef35-135">Calling a method with an `out` argument</span></span>

<span data-ttu-id="5ef35-136">在 C# 6 及更早版本中，必须先在单独的语句中声明变量，然后才能将其作为 `out` 参数传递。</span><span class="sxs-lookup"><span data-stu-id="5ef35-136">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="5ef35-137">下面的示例先声明了变量 `number`，然后再将它传递给将字符串转换为数字的 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法。</span><span class="sxs-lookup"><span data-stu-id="5ef35-137">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="5ef35-138">从 C# 7.0 开始，可以在方法调用的参数列表而不是单独的变量声明中声明 `out` 变量。</span><span class="sxs-lookup"><span data-stu-id="5ef35-138">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="5ef35-139">这使得代码更简洁可读，还能防止在方法调用之前无意中向该变量赋值。</span><span class="sxs-lookup"><span data-stu-id="5ef35-139">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="5ef35-140">下面的示例与上一个示例基本相同，不同之处在于它在对 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的调用中定义了 `number` 变量。</span><span class="sxs-lookup"><span data-stu-id="5ef35-140">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="5ef35-141">在上一个示例中，`number` 变量被强类型化为 `int`。</span><span class="sxs-lookup"><span data-stu-id="5ef35-141">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="5ef35-142">你也可以声明一个隐式类型本地变量，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="5ef35-142">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="5ef35-143">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="5ef35-143">C# Language Specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ef35-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ef35-144">See also</span></span>

- [<span data-ttu-id="5ef35-145">C# 参考</span><span class="sxs-lookup"><span data-stu-id="5ef35-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5ef35-146">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="5ef35-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5ef35-147">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="5ef35-147">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="5ef35-148">方法参数</span><span class="sxs-lookup"><span data-stu-id="5ef35-148">Method Parameters</span></span>](./method-parameters.md)
