---
title: 变量声明
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 587cb84faa09b686361c255c413ad852780b8971
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410291"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="dee2a-102">Visual Basic 中的变量声明</span><span class="sxs-lookup"><span data-stu-id="dee2a-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="dee2a-103">声明一个变量来指定其名称和特征。</span><span class="sxs-lookup"><span data-stu-id="dee2a-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="dee2a-104">变量的声明语句是[Dim 语句](../../../language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-104">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="dee2a-105">其位置和内容确定变量的特征。</span><span class="sxs-lookup"><span data-stu-id="dee2a-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="dee2a-106">有关变量命名规则和注意事项，请参阅已[声明的元素名称](../declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-106">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="dee2a-107">声明级别</span><span class="sxs-lookup"><span data-stu-id="dee2a-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="dee2a-108">局部变量和成员变量</span><span class="sxs-lookup"><span data-stu-id="dee2a-108">Local and Member Variables</span></span>  
 <span data-ttu-id="dee2a-109">局部变量是在过程中声明的*变量*。</span><span class="sxs-lookup"><span data-stu-id="dee2a-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="dee2a-110">*成员变量*是 Visual Basic 类型的成员;它在模块级别、类、结构或模块中声明，但不在该类、结构或模块内部的任何过程中声明。</span><span class="sxs-lookup"><span data-stu-id="dee2a-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="dee2a-111">共享变量和实例变量</span><span class="sxs-lookup"><span data-stu-id="dee2a-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="dee2a-112">在类或结构中，成员变量的类别取决于它是否是共享的。</span><span class="sxs-lookup"><span data-stu-id="dee2a-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="dee2a-113">如果使用[shared](../../../language-reference/modifiers/shared.md)关键字进行声明，则它是*共享变量*，并且存在于在类或结构的所有实例中共享的单个副本。</span><span class="sxs-lookup"><span data-stu-id="dee2a-113">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="dee2a-114">否则，它是一个*实例变量*，为类或结构的每个实例创建一个单独的副本。</span><span class="sxs-lookup"><span data-stu-id="dee2a-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="dee2a-115">实例变量的给定副本仅可用于创建它的类或结构的实例。</span><span class="sxs-lookup"><span data-stu-id="dee2a-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="dee2a-116">它与类或结构的任何其他实例中的实例变量副本无关。</span><span class="sxs-lookup"><span data-stu-id="dee2a-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="dee2a-117">声明数据类型</span><span class="sxs-lookup"><span data-stu-id="dee2a-117">Declaring Data Type</span></span>  
 <span data-ttu-id="dee2a-118">声明语句中的[As](../../../language-reference/statements/as-clause.md)子句允许您定义要声明的变量的数据类型或对象类型。</span><span class="sxs-lookup"><span data-stu-id="dee2a-118">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="dee2a-119">您可以为变量指定以下任意类型：</span><span class="sxs-lookup"><span data-stu-id="dee2a-119">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="dee2a-120">基本数据类型，如 `Boolean` 、 `Long` 或`Decimal`</span><span class="sxs-lookup"><span data-stu-id="dee2a-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="dee2a-121">复合数据类型，例如数组或结构</span><span class="sxs-lookup"><span data-stu-id="dee2a-121">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="dee2a-122">在应用程序或其他应用程序中定义的对象类型或类</span><span class="sxs-lookup"><span data-stu-id="dee2a-122">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="dee2a-123">.NET Framework 类，如 <xref:System.Windows.Forms.Label> 或<xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="dee2a-123">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="dee2a-124">接口类型，如 <xref:System.IComparable> 或<xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="dee2a-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="dee2a-125">您可以在一个语句中声明多个变量，而不必重复该数据类型。</span><span class="sxs-lookup"><span data-stu-id="dee2a-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="dee2a-126">在下面的语句中，变量 `i` 、 `j` 和 `k` 被声明为类型 `Integer` ， `l` `m` `Long` `x` `y` `Single` and 和 and 作为：</span><span class="sxs-lookup"><span data-stu-id="dee2a-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="dee2a-127">有关数据类型的详细信息，请参阅[数据类型](../data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-127">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="dee2a-128">有关对象的详细信息，请参阅[对象和类](../objects-and-classes/index.md)和[对组件进行编程](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="dee2a-128">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="dee2a-129">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="dee2a-129">Local Type Inference</span></span>  
 <span data-ttu-id="dee2a-130">*类型推理*用于确定没有子句声明的局部变量的数据类型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="dee2a-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="dee2a-131">编译器从初始化表达式的类型推断出变量的类型。</span><span class="sxs-lookup"><span data-stu-id="dee2a-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="dee2a-132">这样，便可以在不显式声明类型的情况下声明变量。</span><span class="sxs-lookup"><span data-stu-id="dee2a-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="dee2a-133">在下面的示例中， `num1` 和 `num2` 均强类型化为整数。</span><span class="sxs-lookup"><span data-stu-id="dee2a-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="dee2a-134">如果要使用局部类型推理，则 `Option Infer` 必须将设置为 `On` 。</span><span class="sxs-lookup"><span data-stu-id="dee2a-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="dee2a-135">有关详细信息，请参阅[本地类型推断](local-type-inference.md)和 [Option Infer 语句](../../../language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-135">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="dee2a-136">声明变量的特征</span><span class="sxs-lookup"><span data-stu-id="dee2a-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="dee2a-137">变量的*生存期*是指可供使用的时间段。</span><span class="sxs-lookup"><span data-stu-id="dee2a-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="dee2a-138">一般情况下，只要声明该变量的元素（如过程或类）继续存在，就会存在该变量。</span><span class="sxs-lookup"><span data-stu-id="dee2a-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="dee2a-139">如果变量不需要在其包含元素的生存期之外继续存在，则无需在声明中执行任何特殊操作。</span><span class="sxs-lookup"><span data-stu-id="dee2a-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="dee2a-140">如果变量需要比其包含元素更长的时间，则可以 `Static` `Shared` 在其语句中包含或关键字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="dee2a-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="dee2a-141">有关详细信息，请参阅[Visual Basic 中的生存期](../declared-elements/lifetime.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-141">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="dee2a-142">变量的*作用域*是指可以引用它的所有代码的集合，而无需限定其名称。</span><span class="sxs-lookup"><span data-stu-id="dee2a-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="dee2a-143">变量的作用域由声明它的位置确定。</span><span class="sxs-lookup"><span data-stu-id="dee2a-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="dee2a-144">位于给定区域的代码可以使用该区域中定义的变量，而不必限定其名称。</span><span class="sxs-lookup"><span data-stu-id="dee2a-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="dee2a-145">有关详细信息，请参阅 [Scope in Visual Basic](../declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-145">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="dee2a-146">变量的*访问级别*是有权访问它的代码的范围。</span><span class="sxs-lookup"><span data-stu-id="dee2a-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="dee2a-147">这取决于你在语句中使用的访问修饰符（如[Public](../../../language-reference/modifiers/public.md)或[Private](../../../language-reference/modifiers/private.md)） `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="dee2a-147">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="dee2a-148">有关详细信息，请参阅[Visual Basic 中的访问级别](../declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2a-148">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee2a-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dee2a-149">See also</span></span>

- [<span data-ttu-id="dee2a-150">如何：创建新变量</span><span class="sxs-lookup"><span data-stu-id="dee2a-150">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="dee2a-151">如何：将数据移入和移出变量</span><span class="sxs-lookup"><span data-stu-id="dee2a-151">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="dee2a-152">数据类型</span><span class="sxs-lookup"><span data-stu-id="dee2a-152">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="dee2a-153">避免</span><span class="sxs-lookup"><span data-stu-id="dee2a-153">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="dee2a-154">友好</span><span class="sxs-lookup"><span data-stu-id="dee2a-154">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="dee2a-155">静态</span><span class="sxs-lookup"><span data-stu-id="dee2a-155">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="dee2a-156">已声明元素的特性</span><span class="sxs-lookup"><span data-stu-id="dee2a-156">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="dee2a-157">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="dee2a-157">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="dee2a-158">Option Infer 语句</span><span class="sxs-lookup"><span data-stu-id="dee2a-158">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
