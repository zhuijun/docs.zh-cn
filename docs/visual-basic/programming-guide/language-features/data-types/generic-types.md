---
title: 泛型类型
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: b14c7a3f1f667e7c13ec0ae46185ed3ece92beb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394047"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="e0ed0-102">Visual Basic 中的泛型类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0ed0-102">Generic Types in Visual Basic (Visual Basic)</span></span>
<span data-ttu-id="e0ed0-103">*泛型类型* 是可适应对多种数据类型执行相同功能的单个编程元素。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-103">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="e0ed0-104">定义泛型类或过程时，无需为可能需要对其执行该功能的每个数据类型定义单独版本。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-104">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="e0ed0-105">就好比是带有可拆卸刀头的螺丝刀。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-105">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="e0ed0-106">你检查需要拧动的螺丝，然后选择适合该螺丝的刀头（一字、十字、星形）。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-106">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="e0ed0-107">将正确的刀头插入到螺丝刀柄上后，你就可以使用螺丝刀执行完全相同的功能，即拧螺丝。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-107">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 ![具有不同磁头的平头集的图示。](./media/generic-types/generic-screwdriver-set.gif)  
  
 <span data-ttu-id="e0ed0-109">定义泛型类型时，即使用一个或多个数据类型将其参数化。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-109">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="e0ed0-110">这样可允许使用代码定制数据类型以满足其要求。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-110">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="e0ed0-111">代码可以通过泛型元素声明若干个不同的编程元素，每个元素可使用一组不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-111">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="e0ed0-112">但是，无论声明的元素使用哪些数据类型，它们均执行相同的逻辑。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-112">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="e0ed0-113">例如，你可能想创建并使用一个处理特定数据类型（例如 `String`）的队列类。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-113">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="e0ed0-114">可以通过 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>声明这样的类，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-114">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="e0ed0-115">现在，可以使用 `stringQ` 来专门处理 `String` 值。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-115">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="e0ed0-116">由于 `stringQ` 专用于 `String` 而未针对 `Object` 值进行泛型化，因此，不会有晚期绑定或类型转换。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-116">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="e0ed0-117">从而节省了执行时间并减少了运行时错误。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-117">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="e0ed0-118">有关使用泛型类型的更多信息，请参阅 [How to: Use a Generic Class](how-to-use-a-generic-class.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-118">For more information on using a generic type, see [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="e0ed0-119">泛型类的示例。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-119">Example of a Generic Class</span></span>  
 <span data-ttu-id="e0ed0-120">下面的示例演示了泛型类的主干定义。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-120">The following example shows a skeleton definition of a generic class.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="e0ed0-121">在上面的主干中， `t` 是一个 *类型形参*，即你在声明此类时提供的数据类型的占位符。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-121">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="e0ed0-122">在代码中的其他地方，可以通过为 `classHolder` 提供不同的数据类型来声明不同版本的 `t`</span><span class="sxs-lookup"><span data-stu-id="e0ed0-122">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="e0ed0-123">下面的示例演示了两个此类声明。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-123">The following example shows two such declarations.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="e0ed0-124">上面的语句声明了 *构造类*，在这些类中，特定的类型替换了类型形参。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-124">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="e0ed0-125">此类替换会在构造类中的代码内进行传播。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-125">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="e0ed0-126">下面的示例显示了 `processNewItem` 过程在 `integerClass`中的外观。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-126">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="e0ed0-127">有关更完整的示例，请参阅[如何：定义可在不同数据类型上提供相同功能的类](how-to-define-a-class-that-can-provide-identical-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-127">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="e0ed0-128">合格的编程元素</span><span class="sxs-lookup"><span data-stu-id="e0ed0-128">Eligible Programming Elements</span></span>  
 <span data-ttu-id="e0ed0-129">你可以定义并使用泛型类、结构、接口、过程和委托。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-129">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="e0ed0-130">请注意，.NET Framework 定义了几个泛型类、结构和表示常用泛型元素的接口。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-130">Note that the .NET Framework defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="e0ed0-131"><xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间提供字典、列表、队列和堆栈。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-131">The <xref:System.Collections.Generic?displayProperty=nameWithType> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="e0ed0-132">在定义自己的泛型元素之前，请查看 <xref:System.Collections.Generic?displayProperty=nameWithType>中是否已提供了此元素。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-132">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e0ed0-133">过程不是类型，但可以定义并使用泛型过程。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-133">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="e0ed0-134">请参阅 [Generic Procedures in Visual Basic](generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-134">See [Generic Procedures in Visual Basic](generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="e0ed0-135">泛型类型的优点</span><span class="sxs-lookup"><span data-stu-id="e0ed0-135">Advantages of Generic Types</span></span>  
 <span data-ttu-id="e0ed0-136">泛型类型用作声明几个不同编程元素的基础，而每个元素均处理特定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-136">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="e0ed0-137">泛型类型的替代项有：</span><span class="sxs-lookup"><span data-stu-id="e0ed0-137">The alternatives to a generic type are:</span></span>  
  
1. <span data-ttu-id="e0ed0-138">对 `Object` 数据类型进行处理的单一类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-138">A single type operating on the `Object` data type.</span></span>  
  
2. <span data-ttu-id="e0ed0-139">一组*特定于类型*的类型版本，每个版本单独进行编码并使用一种特定的数据类型（如 `String` 、 `Integer` ）或用户定义的类型（如） `customer` 。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-139">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="e0ed0-140">与上述替代项相比，泛型类型具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="e0ed0-140">A generic type has the following advantages over these alternatives:</span></span>  
  
- <span data-ttu-id="e0ed0-141">**类型安全。**</span><span class="sxs-lookup"><span data-stu-id="e0ed0-141">**Type Safety.**</span></span> <span data-ttu-id="e0ed0-142">泛型类型强制实施编译时类型检查。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-142">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="e0ed0-143">而基于 `Object` 的类型可接受任何数据类型，因此，你必须编写代码以检查是否可接受某种输入数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-143">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="e0ed0-144">通过泛型类型，编译器可以在运行时之前捕获类型的不匹配。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-144">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
- <span data-ttu-id="e0ed0-145">**性能。**</span><span class="sxs-lookup"><span data-stu-id="e0ed0-145">**Performance.**</span></span> <span data-ttu-id="e0ed0-146">泛型类型无需对数据进行 *装箱* 和 *un装箱* 操作，原因是每种泛型类型均专用于一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-146">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="e0ed0-147">而基于 `Object` 的操作必须将输入数据类型进行装箱，以将它们转换为 `Object` ，而且还将对预定输出的数据进行取消装箱操作。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-147">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="e0ed0-148">装箱和取消装箱操作会降低性能。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-148">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="e0ed0-149">此外，还要对基于 `Object` 的类型进行晚期绑定，这意味着需要编写额外的代码才能在运行时访问它们的成员。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-149">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="e0ed0-150">这同样会降低性能。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-150">This also reduces performance.</span></span>  
  
- <span data-ttu-id="e0ed0-151">**代码合并。**</span><span class="sxs-lookup"><span data-stu-id="e0ed0-151">**Code Consolidation.**</span></span> <span data-ttu-id="e0ed0-152">只能对泛型类型中的代码定义一次。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-152">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="e0ed0-153">而一组特定于类型的类型版本必须在每个版本中复制相同的代码，唯一的不同就是该版本的特定数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-153">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="e0ed0-154">利用泛型类型，特定于类型的版本全都利用原始的泛型类型生成。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-154">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
- <span data-ttu-id="e0ed0-155">**代码重用。**</span><span class="sxs-lookup"><span data-stu-id="e0ed0-155">**Code Reuse.**</span></span> <span data-ttu-id="e0ed0-156">对于不依赖特定数据类型的泛型代码，可以利用不同的数据类型重用它。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-156">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="e0ed0-157">你可以经常重用此类代码（甚至利用最初未预料到的数据类型来重用它）。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-157">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
- <span data-ttu-id="e0ed0-158">**IDE 支持。**</span><span class="sxs-lookup"><span data-stu-id="e0ed0-158">**IDE Support.**</span></span> <span data-ttu-id="e0ed0-159">在使用通过泛型类型声明的构造类型时，集成开发环境 (IDE) 可以在你开发代码时给予更多的支持。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-159">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="e0ed0-160">例如，IntelliSense 可以显示适用于构造函数或方法的某个参数的特定于类型的选项。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-160">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
- <span data-ttu-id="e0ed0-161">**泛型算法。**</span><span class="sxs-lookup"><span data-stu-id="e0ed0-161">**Generic Algorithms.**</span></span> <span data-ttu-id="e0ed0-162">独立于类型的抽象算法非常适用于泛型类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-162">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="e0ed0-163">例如，可以将使用 <xref:System.IComparable> 接口对项进行排序的泛型过程用于可实现 <xref:System.IComparable>的任何数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-163">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="e0ed0-164">约束</span><span class="sxs-lookup"><span data-stu-id="e0ed0-164">Constraints</span></span>  
 <span data-ttu-id="e0ed0-165">虽然泛型类型定义中的代码应尽可能独立于类型，但你可能需要要求向泛型类型提供任何数据类型的某项功能。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-165">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="e0ed0-166">例如，如果出于排序或对照的目的而想比较两个项，则它们的数据类型必须实现 <xref:System.IComparable> 接口。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-166">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="e0ed0-167">可通过向类型形参添加 *约束* 来强制实施此要求。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-167">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="e0ed0-168">约束的示例</span><span class="sxs-lookup"><span data-stu-id="e0ed0-168">Example of a Constraint</span></span>  
 <span data-ttu-id="e0ed0-169">下面的示例演示了带有约束（要求类型实参实现 <xref:System.IComparable>）的类的主干定义。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-169">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="e0ed0-170">如果后续代码尝试从提供未实现 `itemManager` 的类型的 <xref:System.IComparable>中构造一个类，则编译器会提示错误。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-170">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="e0ed0-171">约束的类型</span><span class="sxs-lookup"><span data-stu-id="e0ed0-171">Types of Constraints</span></span>  
 <span data-ttu-id="e0ed0-172">约束可以按任意组合指定下列要求：</span><span class="sxs-lookup"><span data-stu-id="e0ed0-172">Your constraint can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="e0ed0-173">该类型实参必须实现一个或多个接口</span><span class="sxs-lookup"><span data-stu-id="e0ed0-173">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="e0ed0-174">类型实参至多只能是一个类的类型，或至多只能从一个类继承</span><span class="sxs-lookup"><span data-stu-id="e0ed0-174">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
- <span data-ttu-id="e0ed0-175">对于通过类型实参创建对象的代码，类型实参必须公开一个可供其访问的无参数构造函数</span><span class="sxs-lookup"><span data-stu-id="e0ed0-175">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
- <span data-ttu-id="e0ed0-176">类型实参必须是*引用类型*，或者必须是*值类型*</span><span class="sxs-lookup"><span data-stu-id="e0ed0-176">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="e0ed0-177">如果需要强制实施多个要求，则可以使用以逗号分隔的 *约束列表* （括在大括号 (`{ }`) 内）。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-177">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="e0ed0-178">若要需要可访问的构造函数，请在列表中包含[New 运算符](../../../language-reference/operators/new-operator.md)关键字。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-178">To require an accessible constructor, you include the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="e0ed0-179">若需要引用类型，请加入 `Class` 关键字；若需要值类型，请加入 `Structure` 关键字。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-179">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="e0ed0-180">有关约束的详细信息，请参阅 [Type List](../../../language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-180">For more information on constraints, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="e0ed0-181">多个约束的示例</span><span class="sxs-lookup"><span data-stu-id="e0ed0-181">Example of Multiple Constraints</span></span>  
 <span data-ttu-id="e0ed0-182">下面的示例演示了带有类型形参约束列表的泛型类的主干定义。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-182">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="e0ed0-183">在创建此类的实例的代码中，类型实参必须实现 <xref:System.IComparable> 和 <xref:System.IDisposable> 接口，必须是引用类型，并且必须公开一个可访问的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-183">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a><span data-ttu-id="e0ed0-184">重要术语</span><span class="sxs-lookup"><span data-stu-id="e0ed0-184">Important Terms</span></span>  
 <span data-ttu-id="e0ed0-185">泛型类型引入并使用了以下术语：</span><span class="sxs-lookup"><span data-stu-id="e0ed0-185">Generic types introduce and use the following terms:</span></span>  
  
- <span data-ttu-id="e0ed0-186">*泛型类型*。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-186">*Generic Type*.</span></span> <span data-ttu-id="e0ed0-187">类、结构、接口、过程或委托的定义，在声明它们时要为它们提供至少一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-187">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
- <span data-ttu-id="e0ed0-188">*类型形参*。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-188">*Type Parameter*.</span></span> <span data-ttu-id="e0ed0-189">在泛型类型定义中，你在声明数据类型时为其提供的占位符。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-189">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
- <span data-ttu-id="e0ed0-190">*类型实参*。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-190">*Type Argument*.</span></span> <span data-ttu-id="e0ed0-191">一种特定的数据类型，用于在你通过泛型类型声明构造类型时替换类型形参。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-191">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
- <span data-ttu-id="e0ed0-192">*约束*。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-192">*Constraint*.</span></span> <span data-ttu-id="e0ed0-193">关于类型形参的条件，用于限制可以为类型形参提供的类型实参。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-193">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="e0ed0-194">约束可以要求类型实参必须实现特定接口，必须是特定的类或继承自特定的类，必须具有可访问的无参数构造函数，或者必须是引用类型或值类型。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-194">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="e0ed0-195">你可以组合这些约束，但至多只能指定一个类。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-195">You can combine these constraints, but you can specify at most one class.</span></span>  
  
- <span data-ttu-id="e0ed0-196">*构造的类型*。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-196">*Constructed Type*.</span></span> <span data-ttu-id="e0ed0-197">通过为泛型类型的类型形参提供类型实参，从泛型类型声明的类、结构、接口、过程或委托。</span><span class="sxs-lookup"><span data-stu-id="e0ed0-197">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ed0-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0ed0-198">See also</span></span>

- [<span data-ttu-id="e0ed0-199">数据类型</span><span class="sxs-lookup"><span data-stu-id="e0ed0-199">Data Types</span></span>](index.md)
- [<span data-ttu-id="e0ed0-200">类型字符</span><span class="sxs-lookup"><span data-stu-id="e0ed0-200">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="e0ed0-201">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="e0ed0-201">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="e0ed0-202">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="e0ed0-202">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="e0ed0-203">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="e0ed0-203">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="e0ed0-204">数据类型</span><span class="sxs-lookup"><span data-stu-id="e0ed0-204">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="e0ed0-205">个</span><span class="sxs-lookup"><span data-stu-id="e0ed0-205">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="e0ed0-206">方式</span><span class="sxs-lookup"><span data-stu-id="e0ed0-206">As</span></span>](../../../language-reference/statements/as-clause.md)
- [<span data-ttu-id="e0ed0-207">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="e0ed0-207">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="e0ed0-208">协变和逆变</span><span class="sxs-lookup"><span data-stu-id="e0ed0-208">Covariance and Contravariance</span></span>](../../concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="e0ed0-209">迭代器</span><span class="sxs-lookup"><span data-stu-id="e0ed0-209">Iterators</span></span>](../../concepts/iterators.md)
