---
title: Option Strict Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: ab1094961e2bc3aed0e975e40369a5f5c1ba93eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873133"
---
# <a name="option-strict-statement"></a><span data-ttu-id="37d42-102">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="37d42-102">Option Strict Statement</span></span>

<span data-ttu-id="37d42-103">将隐式数据类型转换限制为仅进行扩大转换，不允许后期绑定，并允许导致类型的隐式 `Object` 类型化。</span><span class="sxs-lookup"><span data-stu-id="37d42-103">Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d42-104">语法</span><span class="sxs-lookup"><span data-stu-id="37d42-104">Syntax</span></span>  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="37d42-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="37d42-105">Parts</span></span>  
  
|<span data-ttu-id="37d42-106">术语</span><span class="sxs-lookup"><span data-stu-id="37d42-106">Term</span></span>|<span data-ttu-id="37d42-107">定义</span><span class="sxs-lookup"><span data-stu-id="37d42-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="37d42-108">可选。</span><span class="sxs-lookup"><span data-stu-id="37d42-108">Optional.</span></span> <span data-ttu-id="37d42-109">启用 `Option Strict` 检查。</span><span class="sxs-lookup"><span data-stu-id="37d42-109">Enables `Option Strict` checking.</span></span>|  
|`Off`|<span data-ttu-id="37d42-110">可选。</span><span class="sxs-lookup"><span data-stu-id="37d42-110">Optional.</span></span> <span data-ttu-id="37d42-111">禁用 `Option Strict` 检查。</span><span class="sxs-lookup"><span data-stu-id="37d42-111">Disables `Option Strict` checking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37d42-112">备注</span><span class="sxs-lookup"><span data-stu-id="37d42-112">Remarks</span></span>  

 <span data-ttu-id="37d42-113">当 `Option Strict On` 或 `Option Strict` 出现在文件中时，以下情况会导致编译时错误：</span><span class="sxs-lookup"><span data-stu-id="37d42-113">When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:</span></span>  
  
- <span data-ttu-id="37d42-114">隐式收缩转换</span><span class="sxs-lookup"><span data-stu-id="37d42-114">Implicit narrowing conversions</span></span>  
  
- <span data-ttu-id="37d42-115">后期绑定</span><span class="sxs-lookup"><span data-stu-id="37d42-115">Late binding</span></span>  
  
- <span data-ttu-id="37d42-116">隐式键入会导致 `Object` 类型</span><span class="sxs-lookup"><span data-stu-id="37d42-116">Implicit typing that results in an `Object` type</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37d42-117">在可以在 "编译" 页上设置的警告配置中 [，"项目设计器" (Visual Basic) ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，有三个与导致编译时错误的三个条件相对应的设置。</span><span class="sxs-lookup"><span data-stu-id="37d42-117">In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error.</span></span> <span data-ttu-id="37d42-118">有关如何使用这些设置的详细信息，请参阅本主题后面的将 [警告配置设置到 IDE](option-strict-statement.md#conditions) 中。</span><span class="sxs-lookup"><span data-stu-id="37d42-118">For information about how to use these settings, see [To set warning configurations in the IDE](option-strict-statement.md#conditions) later in this topic.</span></span>  
  
 <span data-ttu-id="37d42-119">`Option Strict Off`对于所有三个条件，语句将关闭错误和警告检查，即使关联的 IDE 设置指定打开这些错误或警告。</span><span class="sxs-lookup"><span data-stu-id="37d42-119">The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings.</span></span> <span data-ttu-id="37d42-120">`Option Strict On`即使关联的 IDE 设置指定关闭这些错误或警告，语句也会对所有三个条件启用错误和警告检查。</span><span class="sxs-lookup"><span data-stu-id="37d42-120">The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.</span></span>  
  
 <span data-ttu-id="37d42-121">如果使用， `Option Strict` 语句必须出现在文件中的任何其他代码语句之前。</span><span class="sxs-lookup"><span data-stu-id="37d42-121">If used, the `Option Strict` statement must appear before any other code statements in a file.</span></span>  
  
 <span data-ttu-id="37d42-122">当你将设置 `Option Strict` 为时 `On` ，Visual Basic 将检查是否为所有编程元素指定了数据类型。</span><span class="sxs-lookup"><span data-stu-id="37d42-122">When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements.</span></span> <span data-ttu-id="37d42-123">可以显式指定数据类型，也可以使用局部类型推理来指定数据类型。</span><span class="sxs-lookup"><span data-stu-id="37d42-123">Data types can be specified explicitly, or specified by using local type inference.</span></span> <span data-ttu-id="37d42-124">建议为所有编程元素指定数据类型，原因如下：</span><span class="sxs-lookup"><span data-stu-id="37d42-124">Specifying data types for all your programming elements is recommended, for the following reasons:</span></span>  
  
- <span data-ttu-id="37d42-125">它为你的变量和参数启用 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="37d42-125">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="37d42-126">这使您可以在键入代码时查看它们的属性和其他成员。</span><span class="sxs-lookup"><span data-stu-id="37d42-126">This enables you to see their properties and other members as you type code.</span></span>  
  
- <span data-ttu-id="37d42-127">它使编译器可以执行类型检查。</span><span class="sxs-lookup"><span data-stu-id="37d42-127">It enables the compiler to perform type checking.</span></span> <span data-ttu-id="37d42-128">类型检查有助于在运行时查找可能因类型转换错误而失败的语句。</span><span class="sxs-lookup"><span data-stu-id="37d42-128">Type checking helps you find statements that can fail at run time because of type conversion errors.</span></span> <span data-ttu-id="37d42-129">它还标识对不支持这些方法的对象上的方法的调用。</span><span class="sxs-lookup"><span data-stu-id="37d42-129">It also identifies calls to methods on objects that do not support those methods.</span></span>  
  
- <span data-ttu-id="37d42-130">它可加速代码的执行。</span><span class="sxs-lookup"><span data-stu-id="37d42-130">It speeds up the execution of code.</span></span> <span data-ttu-id="37d42-131">导致这种情况的原因之一是，如果未指定编程元素的数据类型，则 Visual Basic 编译器会为其分配 `Object` 类型。</span><span class="sxs-lookup"><span data-stu-id="37d42-131">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="37d42-132">编译的代码可能需要在 `Object` 和其他数据类型之间来回转换，这会降低性能。</span><span class="sxs-lookup"><span data-stu-id="37d42-132">Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="implicit-narrowing-conversion-errors"></a><span data-ttu-id="37d42-133">隐式收缩转换错误</span><span class="sxs-lookup"><span data-stu-id="37d42-133">Implicit Narrowing Conversion Errors</span></span>  

 <span data-ttu-id="37d42-134">隐式数据类型转换为收缩转换时，将发生隐式收缩转换错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-134">Implicit narrowing conversion errors occur when there is an implicit data type conversion that is a narrowing conversion.</span></span>  
  
 <span data-ttu-id="37d42-135">Visual Basic 可以将多个数据类型转换为其他数据类型。</span><span class="sxs-lookup"><span data-stu-id="37d42-135">Visual Basic can convert many data types to other data types.</span></span> <span data-ttu-id="37d42-136">当一种数据类型的值转换为精度较低或容量较小的数据类型时，可能会发生数据丢失。</span><span class="sxs-lookup"><span data-stu-id="37d42-136">Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity.</span></span> <span data-ttu-id="37d42-137">如果这种收缩转换失败，则会发生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-137">A run-time error occurs if such a narrowing conversion fails.</span></span> <span data-ttu-id="37d42-138">`Option Strict` 确保这些收缩转换的编译时通知，以便你可以避免这些转换。</span><span class="sxs-lookup"><span data-stu-id="37d42-138">`Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them.</span></span> <span data-ttu-id="37d42-139">有关详细信息，请参阅 [隐式和显式转换](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) 以及 [扩大和收缩转换](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="37d42-139">For more information, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="37d42-140">可能导致错误的转换包括表达式中发生的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="37d42-140">Conversions that can cause errors include implicit conversions that occur in expressions.</span></span> <span data-ttu-id="37d42-141">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="37d42-141">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="37d42-142">+ 运算符</span><span class="sxs-lookup"><span data-stu-id="37d42-142">+ Operator</span></span>](../operators/addition-operator.md)  
  
- [<span data-ttu-id="37d42-143">+ = 运算符</span><span class="sxs-lookup"><span data-stu-id="37d42-143">+= Operator</span></span>](../operators/addition-assignment-operator.md)  
  
- [<span data-ttu-id="37d42-144">\ 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="37d42-144">\ Operator (Visual Basic)</span></span>](../operators/integer-division-operator.md)  
  
- [<span data-ttu-id="37d42-145">/= 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="37d42-145">/= Operator (Visual Basic)</span></span>](../operators/floating-point-division-assignment-operator.md)  
  
- [<span data-ttu-id="37d42-146">Char 数据类型</span><span class="sxs-lookup"><span data-stu-id="37d42-146">Char Data Type</span></span>](../data-types/char-data-type.md)  
  
 <span data-ttu-id="37d42-147">通过使用 [& 运算符](../operators/concatenation-operator.md)来串联字符串时，将所有字符串转换都视为扩大。</span><span class="sxs-lookup"><span data-stu-id="37d42-147">When you concatenate strings by using the [& Operator](../operators/concatenation-operator.md), all conversions to the strings are considered to be widening.</span></span> <span data-ttu-id="37d42-148">因此，这些转换不会生成隐式收缩转换错误，即使 `Option Strict` 启用了也是如此。</span><span class="sxs-lookup"><span data-stu-id="37d42-148">So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.</span></span>  
  
 <span data-ttu-id="37d42-149">如果调用的方法具有的数据类型与相应的参数不同，则收缩转换将在打开时导致编译时错误 `Option Strict` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-149">When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on.</span></span> <span data-ttu-id="37d42-150">您可以通过使用扩大转换或显式转换来避免编译时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-150">You can avoid the compile-time error by using a widening conversion or an explicit conversion.</span></span>  
  
 <span data-ttu-id="37d42-151">在编译时，隐式收缩转换错误将从集合中的元素转换 `For Each…Next` 为循环控制变量。</span><span class="sxs-lookup"><span data-stu-id="37d42-151">Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="37d42-152">即使处于打开的情况下也会发生这种情况 `Option Strict` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-152">This occurs even if `Option Strict` is on.</span></span> <span data-ttu-id="37d42-153">有关详细信息，请参阅中的 "收缩转换" 一节 [。下一语句](for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="37d42-153">For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](for-each-next-statement.md).</span></span>  
  
## <a name="late-binding-errors"></a><span data-ttu-id="37d42-154">后期绑定错误</span><span class="sxs-lookup"><span data-stu-id="37d42-154">Late Binding Errors</span></span>  

 <span data-ttu-id="37d42-155">如果将对象分配给声明为 `Object` 类型的变量，则该对象为晚期绑定。</span><span class="sxs-lookup"><span data-stu-id="37d42-155">An object is late bound when it is assigned to a property or method of a variable that is declared to be of type `Object`.</span></span> <span data-ttu-id="37d42-156">有关详细信息，请参阅 [早期和后期绑定](../../programming-guide/language-features/early-late-binding/index.md)。</span><span class="sxs-lookup"><span data-stu-id="37d42-156">For more information, see [Early and Late Binding](../../programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
## <a name="implicit-object-type-errors"></a><span data-ttu-id="37d42-157">隐式对象类型错误</span><span class="sxs-lookup"><span data-stu-id="37d42-157">Implicit Object Type Errors</span></span>  

 <span data-ttu-id="37d42-158">如果无法为已声明的变量推断出合适的类型，则会发生隐式对象类型错误，因此 `Object` 类型是推断出来的。</span><span class="sxs-lookup"><span data-stu-id="37d42-158">Implicit object type errors occur when an appropriate type cannot be inferred for a declared variable, so a type of `Object` is inferred.</span></span> <span data-ttu-id="37d42-159">这主要是在未使用 `As` 子句的情况下使用 `Dim` 语句声明变量，且 `Option Infer` 为关闭时发生的。</span><span class="sxs-lookup"><span data-stu-id="37d42-159">This primarily occurs when you use a `Dim` statement to declare a variable without using an `As` clause, and `Option Infer` is off.</span></span> <span data-ttu-id="37d42-160">有关详细信息，请参阅 [选项推断语句](option-infer-statement.md) 和 [Visual Basic 语言规范](../../reference/language-specification/index.md)。</span><span class="sxs-lookup"><span data-stu-id="37d42-160">For more information, see [Option Infer Statement](option-infer-statement.md) and the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>  
  
 <span data-ttu-id="37d42-161">对于方法参数， `As` 如果为 off，则子句是可选的 `Option Strict` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-161">For method parameters, the `As` clause is optional if `Option Strict` is off.</span></span> <span data-ttu-id="37d42-162">但是，如果任何一个参数使用 `As` 子句，则所有参数都必须使用它。</span><span class="sxs-lookup"><span data-stu-id="37d42-162">However, if any one parameter uses an `As` clause, they all must use it.</span></span> <span data-ttu-id="37d42-163">如果 `Option Strict` 为 on，则 `As` 每个参数定义都需要子句。</span><span class="sxs-lookup"><span data-stu-id="37d42-163">If `Option Strict` is on, the `As` clause is required for every parameter definition.</span></span>  
  
 <span data-ttu-id="37d42-164">如果在不使用子句的情况下声明变量 `As` 并将其设置为 `Nothing` ，则该变量的类型为 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-164">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="37d42-165">如果 `Option Strict` 为 on，则在此情况下不会发生编译时错误 `Option Infer` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-165">No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on.</span></span> <span data-ttu-id="37d42-166">这是一个示例 `Dim something = Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-166">An example of this is `Dim something = Nothing`.</span></span>  
  
### <a name="default-data-types-and-values"></a><span data-ttu-id="37d42-167">默认数据类型和值</span><span class="sxs-lookup"><span data-stu-id="37d42-167">Default Data Types and Values</span></span>  

 <span data-ttu-id="37d42-168">下表描述了在 [Dim 语句](dim-statement.md)中指定数据类型和初始值设定项的各种组合的结果。</span><span class="sxs-lookup"><span data-stu-id="37d42-168">The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](dim-statement.md).</span></span>  
  
|<span data-ttu-id="37d42-169">是否指定数据类型？</span><span class="sxs-lookup"><span data-stu-id="37d42-169">Data type specified?</span></span>|<span data-ttu-id="37d42-170">是否指定初始值设定项？</span><span class="sxs-lookup"><span data-stu-id="37d42-170">Initializer specified?</span></span>|<span data-ttu-id="37d42-171">示例</span><span class="sxs-lookup"><span data-stu-id="37d42-171">Example</span></span>|<span data-ttu-id="37d42-172">结果</span><span class="sxs-lookup"><span data-stu-id="37d42-172">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="37d42-173">否</span><span class="sxs-lookup"><span data-stu-id="37d42-173">No</span></span>|<span data-ttu-id="37d42-174">否</span><span class="sxs-lookup"><span data-stu-id="37d42-174">No</span></span>|`Dim qty`|<span data-ttu-id="37d42-175">如果 `Option Strict` 处于关闭状态（默认），则将变量设置为 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="37d42-175">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="37d42-176">如果 `Option Strict` 处于打开状态，则发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-176">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="37d42-177">否</span><span class="sxs-lookup"><span data-stu-id="37d42-177">No</span></span>|<span data-ttu-id="37d42-178">是</span><span class="sxs-lookup"><span data-stu-id="37d42-178">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="37d42-179">如果 `Option Infer` 处于打开状态（默认），则变量采用初始值设定项的数据类型。</span><span class="sxs-lookup"><span data-stu-id="37d42-179">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="37d42-180">请参阅 [局部类型推理](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="37d42-180">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="37d42-181">如果 `Option Infer` 和 `Option Strict` 均处于关闭状态，则变量采用 `Object` 的数据类型。</span><span class="sxs-lookup"><span data-stu-id="37d42-181">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="37d42-182">如果 `Option Infer` 处于关闭状态但 `Option Strict` 处于打开状态，则发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-182">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="37d42-183">是</span><span class="sxs-lookup"><span data-stu-id="37d42-183">Yes</span></span>|<span data-ttu-id="37d42-184">否</span><span class="sxs-lookup"><span data-stu-id="37d42-184">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="37d42-185">将变量初始化为数据类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="37d42-185">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="37d42-186">有关详细信息，请参阅 [Dim 语句](dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="37d42-186">For more information, see [Dim Statement](dim-statement.md).</span></span>|  
|<span data-ttu-id="37d42-187">是</span><span class="sxs-lookup"><span data-stu-id="37d42-187">Yes</span></span>|<span data-ttu-id="37d42-188">是</span><span class="sxs-lookup"><span data-stu-id="37d42-188">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="37d42-189">如果初始值设定项的数据类型不可转换为指定数据类型，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-189">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a><span data-ttu-id="37d42-190">当 Option Strict 语句不存在时</span><span class="sxs-lookup"><span data-stu-id="37d42-190">When an Option Strict Statement Is Not Present</span></span>  

 <span data-ttu-id="37d42-191">如果源代码不包含 `Option Strict` 语句，则使用 "编译" 页上的 " **Option strict** " 设置 [，"项目设计器" (Visual Basic) ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。</span><span class="sxs-lookup"><span data-stu-id="37d42-191">If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="37d42-192">" **编译" 页** 中的设置提供对生成错误的条件的更多控制。</span><span class="sxs-lookup"><span data-stu-id="37d42-192">The **Compile Page** has settings that provide additional control over the conditions that generate an error.</span></span>  
  
 <span data-ttu-id="37d42-193">如果你使用的是命令行编译器，则可以使用 [-optionstrict](../../reference/command-line-compiler/optionstrict.md) 编译器选项来指定的设置 `Option Strict` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-193">If you are using the command-line compiler, you can use the [-optionstrict](../../reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.</span></span>  
  
### <a name="to-set-option-strict-in-the-ide"></a><span data-ttu-id="37d42-194">在 IDE 中设置 Option Strict</span><span class="sxs-lookup"><span data-stu-id="37d42-194">To set Option Strict in the IDE</span></span>  

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. <span data-ttu-id="37d42-195">在 **解决方案资源管理器**中，选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="37d42-195">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="37d42-196">在 **“项目”** 菜单上，单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="37d42-196">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="37d42-197">在 " **编译** " 选项卡上，在 " **选项严格限制** " 框中设置值。</span><span class="sxs-lookup"><span data-stu-id="37d42-197">On the **Compile** tab, set the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-warning-configurations-in-the-ide"></a><a name="conditions"></a> <span data-ttu-id="37d42-198">在 IDE 中设置警告配置</span><span class="sxs-lookup"><span data-stu-id="37d42-198">To set warning configurations in the IDE</span></span>  

 <span data-ttu-id="37d42-199">使用 "编译" [页时，"项目设计器" (Visual Basic) ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 而不是 `Option Strict` 语句，您可以对生成错误的条件进行其他控制。</span><span class="sxs-lookup"><span data-stu-id="37d42-199">When you use the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors.</span></span> <span data-ttu-id="37d42-200">"**编译" 页**的 "**警告配置**" 部分具有与在上时导致编译时错误的三个条件相对应的设置 `Option Strict` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-200">The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on.</span></span> <span data-ttu-id="37d42-201">这些设置如下：</span><span class="sxs-lookup"><span data-stu-id="37d42-201">Following are these settings:</span></span>  
  
- <span data-ttu-id="37d42-202">**隐式转换**</span><span class="sxs-lookup"><span data-stu-id="37d42-202">**Implicit conversion**</span></span>  
  
- <span data-ttu-id="37d42-203">晚期绑定；调用可能在运行时失败\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="37d42-203">**Late binding; call could fail at run time**</span></span>  
  
- <span data-ttu-id="37d42-204">隐式类型；假定为对象\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="37d42-204">**Implicit type; object assumed**</span></span>  
  
 <span data-ttu-id="37d42-205">“Option Strict”设置为“开启”时，所有这三个警告配置设置都将被设置为“错误”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="37d42-205">When you set **Option Strict** to **On**, all three of these warning configuration settings are set to **Error**.</span></span> <span data-ttu-id="37d42-206">“Option Strict”设置为“关闭”时，所有这三个设置都将被设置为“无”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="37d42-206">When you set **Option Strict** to **Off**, all three settings are set to **None**.</span></span>  
  
 <span data-ttu-id="37d42-207">可单独将各个警告配置设置更改为“无”、“警告”或“错误”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="37d42-207">You can individually change each warning configuration setting to **None**, **Warning**, or **Error**.</span></span> <span data-ttu-id="37d42-208">如果所有三个警告配置设置均设置为 " **错误**"， `On` 则会出现在 `Option strict` 框中。</span><span class="sxs-lookup"><span data-stu-id="37d42-208">If all three warning configuration settings are set to **Error**, `On` appears in the `Option strict` box.</span></span> <span data-ttu-id="37d42-209">如果所有三个均设置为 " **无**"，则 `Off` 在此框中显示。</span><span class="sxs-lookup"><span data-stu-id="37d42-209">If all three are set to **None**, `Off` appears in this box.</span></span> <span data-ttu-id="37d42-210">对于这些配置的任何其他组合，显示“(自定义)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="37d42-210">For any other combination of these settings, **(custom)** appears.</span></span>  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a><span data-ttu-id="37d42-211">为新项目设置选项 Strict 默认设置</span><span class="sxs-lookup"><span data-stu-id="37d42-211">To set the Option Strict default setting for new projects</span></span>  

 <span data-ttu-id="37d42-212">创建项目时，"**编译**" 选项卡上的 " **option strict** " 设置设置为 "**选项**" 对话框中的 " **option strict** " 设置。</span><span class="sxs-lookup"><span data-stu-id="37d42-212">When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="37d42-213">若要 `Option Strict` 在此对话框中设置，请在 " **工具** " 菜单上单击 " **选项**"。</span><span class="sxs-lookup"><span data-stu-id="37d42-213">To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="37d42-214">在“选项”对话框中，展开“项目和解决方案”，然后单击“VB 默认值”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="37d42-214">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="37d42-215">**VB 默认**设置中的初始默认设置为 `Off` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-215">The initial default setting in **VB Defaults** is `Off`.</span></span>  
  
### <a name="to-set-option-strict-on-the-command-line"></a><span data-ttu-id="37d42-216">在命令行上设置 Option Strict</span><span class="sxs-lookup"><span data-stu-id="37d42-216">To set Option Strict on the command line</span></span>  

 <span data-ttu-id="37d42-217">在**vbc**命令中包含[-optionstrict](../../reference/command-line-compiler/optionstrict.md)编译器选项。</span><span class="sxs-lookup"><span data-stu-id="37d42-217">Include the [-optionstrict](../../reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37d42-218">示例</span><span class="sxs-lookup"><span data-stu-id="37d42-218">Example</span></span>  

 <span data-ttu-id="37d42-219">下面的示例演示由收缩转换的隐式类型转换导致的编译时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-219">The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions.</span></span> <span data-ttu-id="37d42-220">此类别的错误对应于 "**编译" 页**上的**隐式转换**条件。</span><span class="sxs-lookup"><span data-stu-id="37d42-220">This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a><span data-ttu-id="37d42-221">示例</span><span class="sxs-lookup"><span data-stu-id="37d42-221">Example</span></span>  

 <span data-ttu-id="37d42-222">下面的示例演示后期绑定导致的编译时错误。</span><span class="sxs-lookup"><span data-stu-id="37d42-222">The following example demonstrates a compile-time error caused by late binding.</span></span> <span data-ttu-id="37d42-223">此类别的错误对应于后期绑定; "**编译" 页**上的 "**调用可能在运行时失败**" 条件。</span><span class="sxs-lookup"><span data-stu-id="37d42-223">This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a><span data-ttu-id="37d42-224">示例</span><span class="sxs-lookup"><span data-stu-id="37d42-224">Example</span></span>  

 <span data-ttu-id="37d42-225">下面的示例演示由使用隐式类型声明的变量导致的错误 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="37d42-225">The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`.</span></span> <span data-ttu-id="37d42-226">此类别的错误对应于 **隐式类型;** " **编译" 页**上的 "对象假定" 条件。</span><span class="sxs-lookup"><span data-stu-id="37d42-226">This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a><span data-ttu-id="37d42-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37d42-227">See also</span></span>

- [<span data-ttu-id="37d42-228">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="37d42-228">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="37d42-229">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="37d42-229">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="37d42-230">“项目设计器”->“编译”页 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37d42-230">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="37d42-231">Option Explicit 语句</span><span class="sxs-lookup"><span data-stu-id="37d42-231">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="37d42-232">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="37d42-232">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="37d42-233">如何：访问对象的成员</span><span class="sxs-lookup"><span data-stu-id="37d42-233">How to: Access Members of an Object</span></span>](../../programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="37d42-234">XML 中的嵌入式表达式</span><span class="sxs-lookup"><span data-stu-id="37d42-234">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="37d42-235">宽松委托转换</span><span class="sxs-lookup"><span data-stu-id="37d42-235">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="37d42-236">Late Binding in Office Solutions</span><span class="sxs-lookup"><span data-stu-id="37d42-236">Late Binding in Office Solutions</span></span>](/visualstudio/vsto/late-binding-in-office-solutions)
- [<span data-ttu-id="37d42-237">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="37d42-237">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="37d42-238">“选项”对话框 ->“项目”->“Visual Basic 默认值”</span><span class="sxs-lookup"><span data-stu-id="37d42-238">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
