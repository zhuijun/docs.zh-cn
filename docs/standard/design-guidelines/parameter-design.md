---
title: 参数设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: e0bc52f5679a7771d5690be9f903e677ce611605
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621582"
---
# <a name="parameter-design"></a><span data-ttu-id="ad200-102">参数设计</span><span class="sxs-lookup"><span data-stu-id="ad200-102">Parameter Design</span></span>

<span data-ttu-id="ad200-103">本部分提供有关参数设计的广泛准则，包括包含检查参数准则的部分。</span><span class="sxs-lookup"><span data-stu-id="ad200-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="ad200-104">此外，还应参阅[命名参数](naming-parameters.md)中所述的准则。</span><span class="sxs-lookup"><span data-stu-id="ad200-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="ad200-105">✔️使用最不提供成员所需功能的派生参数类型。</span><span class="sxs-lookup"><span data-stu-id="ad200-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="ad200-106">例如，假设要设计一个方法，该方法可枚举集合并将每个项输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="ad200-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="ad200-107">此类方法应采用 <xref:System.Collections.IEnumerable> 参数，而不是 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList> ，例如。</span><span class="sxs-lookup"><span data-stu-id="ad200-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="ad200-108">❌不要使用保留的参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="ad200-109">如果在将来的某个版本中需要对成员进行更多输入，则可以添加新的重载。</span><span class="sxs-lookup"><span data-stu-id="ad200-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="ad200-110">❌不具有公开的方法，这些方法采用指针、指针数组或多维数组作为参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="ad200-111">指针和多维数组相对较难正确使用。</span><span class="sxs-lookup"><span data-stu-id="ad200-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="ad200-112">几乎在所有情况下，都可以重新设计 Api，以避免将这些类型作为参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="ad200-113">✔️将所有的 `out` 参数置于所有按值和 `ref` 参数（不包括参数数组）之后，即使它导致在重载之间参数排序不一致（请参阅[成员重载](member-overloading.md)）。</span><span class="sxs-lookup"><span data-stu-id="ad200-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="ad200-114">`out`参数可以视为额外的返回值，并将它们组合在一起，使方法签名更易于理解。</span><span class="sxs-lookup"><span data-stu-id="ad200-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="ad200-115">重写成员或实现接口成员时，✔️在命名参数中保持一致。</span><span class="sxs-lookup"><span data-stu-id="ad200-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="ad200-116">这更好地传达了方法之间的关系。</span><span class="sxs-lookup"><span data-stu-id="ad200-116">This better communicates the relationship between the methods.</span></span>

### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="ad200-117">选择枚举参数和布尔参数</span><span class="sxs-lookup"><span data-stu-id="ad200-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="ad200-118">如果成员将使用两个或多个布尔参数，✔️确实使用枚举。</span><span class="sxs-lookup"><span data-stu-id="ad200-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="ad200-119">❌不要使用布尔值，除非你完全确定不需要两个以上的值。</span><span class="sxs-lookup"><span data-stu-id="ad200-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="ad200-120">枚举为您提供了一些空间供将来添加值，但您应了解将值添加到枚举的所有含义，如[枚举设计](enum.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="ad200-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="ad200-121">✔️考虑为构造函数参数使用布尔值，这些参数是真正的双状态值，只用于初始化布尔属性。</span><span class="sxs-lookup"><span data-stu-id="ad200-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validating-arguments"></a><span data-ttu-id="ad200-122">验证参数</span><span class="sxs-lookup"><span data-stu-id="ad200-122">Validating Arguments</span></span>
 <span data-ttu-id="ad200-123">✔️验证传递到公共、受保护或显式实现的成员的参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="ad200-124"><xref:System.ArgumentException?displayProperty=nameWithType>如果验证失败，则引发或其子类之一。</span><span class="sxs-lookup"><span data-stu-id="ad200-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="ad200-125">请注意，实际验证不一定要在公共或受保护的成员本身中发生。</span><span class="sxs-lookup"><span data-stu-id="ad200-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="ad200-126">在某些专用或内部例程中，它可能会在较低的级别上发生。</span><span class="sxs-lookup"><span data-stu-id="ad200-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="ad200-127">要点是向最终用户公开的整个图面区域会检查参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="ad200-128"><xref:System.ArgumentNullException>如果传递了 null 参数并且该成员不支持 null 参数，✔️将引发。</span><span class="sxs-lookup"><span data-stu-id="ad200-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="ad200-129">✔️验证枚举参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="ad200-130">不要假设枚举参数将在由枚举定义的范围内。</span><span class="sxs-lookup"><span data-stu-id="ad200-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="ad200-131">CLR 允许将任何整数值强制转换为枚举值，即使枚举中未定义该值。</span><span class="sxs-lookup"><span data-stu-id="ad200-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="ad200-132">❌不要用于 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 枚举范围检查。</span><span class="sxs-lookup"><span data-stu-id="ad200-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="ad200-133">✔️请注意，可变参数在验证后可能已更改。</span><span class="sxs-lookup"><span data-stu-id="ad200-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="ad200-134">如果成员区分安全，则建议您创建一个副本，然后验证并处理参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="parameter-passing"></a><span data-ttu-id="ad200-135">参数传递</span><span class="sxs-lookup"><span data-stu-id="ad200-135">Parameter Passing</span></span>
 <span data-ttu-id="ad200-136">从框架设计器的角度来看，有三个主要参数组：按值参数、 `ref` 参数和 `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="ad200-137">当通过值参数传递参数时，该成员将接收传入的实参的副本。</span><span class="sxs-lookup"><span data-stu-id="ad200-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="ad200-138">如果参数是值类型，则将参数的副本放在堆栈上。</span><span class="sxs-lookup"><span data-stu-id="ad200-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="ad200-139">如果参数是引用类型，则将引用的副本放在堆栈上。</span><span class="sxs-lookup"><span data-stu-id="ad200-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="ad200-140">最常用的 CLR 语言（例如 c #、VB.NET 和 c + +）默认为通过值传递参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="ad200-141">当通过参数传递参数时 `ref` ，该成员将接收对传入的实际参数的引用。</span><span class="sxs-lookup"><span data-stu-id="ad200-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="ad200-142">如果参数是值类型，则将对该参数的引用置于堆栈上。</span><span class="sxs-lookup"><span data-stu-id="ad200-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="ad200-143">如果参数是引用类型，则对该引用的引用将放在堆栈上。</span><span class="sxs-lookup"><span data-stu-id="ad200-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="ad200-144">`Ref`参数可用于允许成员修改调用方传递的参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="ad200-145">`Out`参数类似于 `ref` 参数，但有一些细微的差异。</span><span class="sxs-lookup"><span data-stu-id="ad200-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="ad200-146">参数最初被视为未分配，在为其赋值之前，无法在成员正文中读取。</span><span class="sxs-lookup"><span data-stu-id="ad200-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="ad200-147">此外，在成员返回之前，必须为参数赋值。</span><span class="sxs-lookup"><span data-stu-id="ad200-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="ad200-148">❌避免使用 `out` 或 `ref` 参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="ad200-149">使用 `out` 或 `ref` 参数需要使用指针的经验，了解值类型和引用类型的不同之处，以及处理具有多个返回值的方法。</span><span class="sxs-lookup"><span data-stu-id="ad200-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="ad200-150">此外，和参数之间的差异 `out` 并 `ref` 不被广泛理解。</span><span class="sxs-lookup"><span data-stu-id="ad200-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="ad200-151">一般受众设计框架架构师不应指望用户使用 `out` 或 `ref` 参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="ad200-152">❌不要通过引用传递引用类型。</span><span class="sxs-lookup"><span data-stu-id="ad200-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="ad200-153">规则有一些例外情况，例如可用于交换引用的方法。</span><span class="sxs-lookup"><span data-stu-id="ad200-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="ad200-154">参数数目可变的成员</span><span class="sxs-lookup"><span data-stu-id="ad200-154">Members with Variable Number of Parameters</span></span>
 <span data-ttu-id="ad200-155">可以通过提供数组参数来表示可采用可变数量的参数的成员。</span><span class="sxs-lookup"><span data-stu-id="ad200-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="ad200-156">例如， <xref:System.String> 提供以下方法：</span><span class="sxs-lookup"><span data-stu-id="ad200-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="ad200-157">然后，用户可以调用 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ad200-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="ad200-158">向数组参数添加 c # params 关键字会将参数更改为所谓的 params 数组参数，并提供创建临时数组的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="ad200-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="ad200-159">这样，用户就可以通过在参数列表中直接传递数组元素来调用方法。</span><span class="sxs-lookup"><span data-stu-id="ad200-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="ad200-160">请注意，只能将 params 关键字添加到参数列表中的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="ad200-161">如果预计最终用户要传递具有少量元素的数组，✔️考虑将 params 关键字添加到数组参数。</span><span class="sxs-lookup"><span data-stu-id="ad200-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="ad200-162">如果预计会在常见方案中传递多个元素，则用户可能无法以内联方式传递这些元素，因此不需要 params 关键字。</span><span class="sxs-lookup"><span data-stu-id="ad200-162">If it's expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="ad200-163">❌如果调用方几乎始终具有数组中的输入，请避免使用 params 数组。</span><span class="sxs-lookup"><span data-stu-id="ad200-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="ad200-164">例如，具有字节数组参数的成员几乎不会通过传递单个字节来调用。</span><span class="sxs-lookup"><span data-stu-id="ad200-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="ad200-165">出于此原因，.NET Framework 中的字节数组参数不使用 params 关键字。</span><span class="sxs-lookup"><span data-stu-id="ad200-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="ad200-166">❌如果使用 params 数组参数的成员修改了数组，则不要使用 params 数组。</span><span class="sxs-lookup"><span data-stu-id="ad200-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="ad200-167">由于很多编译器会将成员的参数转换为调用站点的临时数组，因此数组可能是临时对象，因此对数组进行的任何修改都将丢失。</span><span class="sxs-lookup"><span data-stu-id="ad200-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="ad200-168">✔️考虑在简单重载中使用 params 关键字，即使比较复杂的重载无法使用它也是如此。</span><span class="sxs-lookup"><span data-stu-id="ad200-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="ad200-169">询问用户是否要将 params 数组作为参数的值，即使它不在所有重载中也是如此。</span><span class="sxs-lookup"><span data-stu-id="ad200-169">Ask yourself if users would value having the params array in one overload even if it wasn't in all overloads.</span></span>

 <span data-ttu-id="ad200-170">✔️尝试对参数进行排序，以便可以使用 params 关键字。</span><span class="sxs-lookup"><span data-stu-id="ad200-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="ad200-171">✔️考虑为在极高性能的 Api 中使用少量参数的调用提供特殊重载和代码路径。</span><span class="sxs-lookup"><span data-stu-id="ad200-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="ad200-172">这样，当使用少量参数调用 API 时，就可以避免创建数组对象。</span><span class="sxs-lookup"><span data-stu-id="ad200-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="ad200-173">通过采用数组参数的单数形式并添加数字后缀，形成参数的名称。</span><span class="sxs-lookup"><span data-stu-id="ad200-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="ad200-174">仅当要使用特殊的代码路径（而不仅仅是创建数组并调用更常规的方法）时，才应执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ad200-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="ad200-175">✔️请注意，null 可作为参数数组参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="ad200-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="ad200-176">在处理之前，应该验证数组是否为 null。</span><span class="sxs-lookup"><span data-stu-id="ad200-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="ad200-177">❌不要使用 `varargs` 方法，也称为省略号。</span><span class="sxs-lookup"><span data-stu-id="ad200-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="ad200-178">某些 CLR 语言（如 c + +）支持用于传递变量参数列表（称为方法）的替代约定 `varargs` 。</span><span class="sxs-lookup"><span data-stu-id="ad200-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="ad200-179">不应在框架中使用约定，因为它不符合 CLS。</span><span class="sxs-lookup"><span data-stu-id="ad200-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="ad200-180">指针参数</span><span class="sxs-lookup"><span data-stu-id="ad200-180">Pointer Parameters</span></span>
 <span data-ttu-id="ad200-181">通常，指针不应出现在设计良好的托管代码框架的公共表面区中。</span><span class="sxs-lookup"><span data-stu-id="ad200-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="ad200-182">大多数情况下，应封装指针。</span><span class="sxs-lookup"><span data-stu-id="ad200-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="ad200-183">但是，在某些情况下，出于互操作性原因需要使用指针，因此在这种情况下使用指针是合适的。</span><span class="sxs-lookup"><span data-stu-id="ad200-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="ad200-184">✔️确实为采用指针参数的任何成员提供了一种替代方法，因为指针不符合 CLS。</span><span class="sxs-lookup"><span data-stu-id="ad200-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="ad200-185">❌避免对指针参数执行昂贵的参数检查。</span><span class="sxs-lookup"><span data-stu-id="ad200-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="ad200-186">✔️在用指针设计成员时遵循常见的指针相关约定。</span><span class="sxs-lookup"><span data-stu-id="ad200-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="ad200-187">例如，无需传递开始索引，因为可以使用简单指针算法来实现相同的结果。</span><span class="sxs-lookup"><span data-stu-id="ad200-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="ad200-188">*部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="ad200-188">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ad200-189">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="ad200-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ad200-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad200-190">See also</span></span>

- [<span data-ttu-id="ad200-191">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="ad200-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="ad200-192">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="ad200-192">Framework Design Guidelines</span></span>](index.md)
