---
title: 部分
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: 2482facadd0e0528ed1b71df6edb4a447947a902
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867782"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="bcc93-102">分部 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcc93-102">Partial (Visual Basic)</span></span>

<span data-ttu-id="bcc93-103">指示类型声明为类型的分部定义。</span><span class="sxs-lookup"><span data-stu-id="bcc93-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="bcc93-104">可以使用 `Partial` 关键字在几个声明之间划分类型的定义。</span><span class="sxs-lookup"><span data-stu-id="bcc93-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="bcc93-105">可以根据需要在任意数量的不同源文件中使用任意数量的分部声明。</span><span class="sxs-lookup"><span data-stu-id="bcc93-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="bcc93-106">但是，所有声明都必须在相同的程序集和相同的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="bcc93-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcc93-107">Visual Basic 支持 *分部方法*，这些方法通常在分部类中实现。</span><span class="sxs-lookup"><span data-stu-id="bcc93-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="bcc93-108">有关详细信息，请参阅 [分部方法](../../programming-guide/language-features/procedures/partial-methods.md) 和 [Sub 语句](../statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-108">For more information, see [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc93-109">语法</span><span class="sxs-lookup"><span data-stu-id="bcc93-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="bcc93-110">组成部分</span><span class="sxs-lookup"><span data-stu-id="bcc93-110">Parts</span></span>  
  
|<span data-ttu-id="bcc93-111">术语</span><span class="sxs-lookup"><span data-stu-id="bcc93-111">Term</span></span>|<span data-ttu-id="bcc93-112">定义</span><span class="sxs-lookup"><span data-stu-id="bcc93-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="bcc93-113">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-113">Optional.</span></span> <span data-ttu-id="bcc93-114">应用于此类型的特性列表。</span><span class="sxs-lookup"><span data-stu-id="bcc93-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="bcc93-115">必须将 [属性列表](../statements/attribute-list.md) 用尖括号括起来 (`< >`) 。</span><span class="sxs-lookup"><span data-stu-id="bcc93-115">You must enclose the [Attribute List](../statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="bcc93-116">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-116">Optional.</span></span> <span data-ttu-id="bcc93-117">指定哪些代码可以访问此类型。</span><span class="sxs-lookup"><span data-stu-id="bcc93-117">Specifies what code can access this type.</span></span> <span data-ttu-id="bcc93-118">请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-118">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="bcc93-119">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-119">Optional.</span></span> <span data-ttu-id="bcc93-120">请参阅 [阴影](shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-120">See [Shadows](shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="bcc93-121">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-121">Optional.</span></span> <span data-ttu-id="bcc93-122">请参阅 [MustInherit](mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-122">See [MustInherit](mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="bcc93-123">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-123">Optional.</span></span> <span data-ttu-id="bcc93-124">请参阅 [NotInheritable](notinheritable.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-124">See [NotInheritable](notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="bcc93-125">必需。</span><span class="sxs-lookup"><span data-stu-id="bcc93-125">Required.</span></span> <span data-ttu-id="bcc93-126">此类型的名称。</span><span class="sxs-lookup"><span data-stu-id="bcc93-126">Name of this type.</span></span> <span data-ttu-id="bcc93-127">必须匹配在同一类型的所有其他分部声明中定义的名称。</span><span class="sxs-lookup"><span data-stu-id="bcc93-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="bcc93-128">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-128">Optional.</span></span> <span data-ttu-id="bcc93-129">指定这是一种泛型类型。</span><span class="sxs-lookup"><span data-stu-id="bcc93-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="bcc93-130">请参阅 [Visual Basic 中的泛型类型](../../programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-130">See [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="bcc93-131">如果使用，则 [是必需的](../statements/of-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-131">Required if you use [Of](../statements/of-clause.md).</span></span> <span data-ttu-id="bcc93-132">请参阅 [类型列表](../statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-132">See [Type List](../statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="bcc93-133">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-133">Optional.</span></span> <span data-ttu-id="bcc93-134">请参阅 [Inherits 语句](../statements/inherits-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-134">See [Inherits Statement](../statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="bcc93-135">如果使用 `Inherits`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="bcc93-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="bcc93-136">派生此类的类或接口的名称。</span><span class="sxs-lookup"><span data-stu-id="bcc93-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="bcc93-137">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-137">Optional.</span></span> <span data-ttu-id="bcc93-138">请参阅 [Implements 语句](../statements/implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-138">See [Implements Statement](../statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="bcc93-139">如果使用 `Implements`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="bcc93-139">Required if you use `Implements`.</span></span> <span data-ttu-id="bcc93-140">此类型实现的接口的名称。</span><span class="sxs-lookup"><span data-stu-id="bcc93-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="bcc93-141">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-141">Optional.</span></span> <span data-ttu-id="bcc93-142">声明该类型的其他变量和事件的语句。</span><span class="sxs-lookup"><span data-stu-id="bcc93-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="bcc93-143">可选。</span><span class="sxs-lookup"><span data-stu-id="bcc93-143">Optional.</span></span> <span data-ttu-id="bcc93-144">声明和定义该类型的其他过程的语句。</span><span class="sxs-lookup"><span data-stu-id="bcc93-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="bcc93-145">`End Class` 或 `End Structure`</span><span class="sxs-lookup"><span data-stu-id="bcc93-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="bcc93-146">结束此分部 `Class` 或 `Structure` 定义。</span><span class="sxs-lookup"><span data-stu-id="bcc93-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcc93-147">备注</span><span class="sxs-lookup"><span data-stu-id="bcc93-147">Remarks</span></span>  

 <span data-ttu-id="bcc93-148">Visual Basic 使用分部类定义将生成的代码与单独的源文件中用户编写的代码分开。</span><span class="sxs-lookup"><span data-stu-id="bcc93-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="bcc93-149">例如，“Windows 窗体设计器”\*\*\*\* 定义了控件的分部类，如 <xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="bcc93-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="bcc93-150">不应修改这些控件中生成的代码。</span><span class="sxs-lookup"><span data-stu-id="bcc93-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="bcc93-151">创建分部类型时，将应用类、结构、接口和模块创建的所有规则（如用于修饰符的使用和继承的规则）。</span><span class="sxs-lookup"><span data-stu-id="bcc93-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="bcc93-152">最佳实践</span><span class="sxs-lookup"><span data-stu-id="bcc93-152">Best Practices</span></span>  
  
- <span data-ttu-id="bcc93-153">正常情况下，不应将单个类型的开发分跨两个或多个声明。</span><span class="sxs-lookup"><span data-stu-id="bcc93-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="bcc93-154">因此，在大多数情况下不需要 `Partial` 关键字。</span><span class="sxs-lookup"><span data-stu-id="bcc93-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="bcc93-155">为了提高可读性，类型的每个分部声明都应包含 `Partial` 关键字。</span><span class="sxs-lookup"><span data-stu-id="bcc93-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="bcc93-156">编译器最多允许一个分部声明省略关键字；如果两个或多个分部声明省略了关键字，则编译器将发出错误信号。</span><span class="sxs-lookup"><span data-stu-id="bcc93-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="bcc93-157">行为</span><span class="sxs-lookup"><span data-stu-id="bcc93-157">Behavior</span></span>  
  
- <span data-ttu-id="bcc93-158">**声明的联合。**</span><span class="sxs-lookup"><span data-stu-id="bcc93-158">**Union of Declarations.**</span></span> <span data-ttu-id="bcc93-159">编译器将类型视为其所有分部声明的联合。</span><span class="sxs-lookup"><span data-stu-id="bcc93-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="bcc93-160">每个分部定义的每个修饰符均可应用于整个类型，并且每个分部定义的每个成员均可用于整个类型。</span><span class="sxs-lookup"><span data-stu-id="bcc93-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="bcc93-161">**模块中不允许使用分部类型的类型提升。**</span><span class="sxs-lookup"><span data-stu-id="bcc93-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="bcc93-162">如果分部定义位于模块内，则该类型的类型提升会自动失效。</span><span class="sxs-lookup"><span data-stu-id="bcc93-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="bcc93-163">在这种情况下，一组分部定义可能导致意外的结果，甚至导致编译器错误。</span><span class="sxs-lookup"><span data-stu-id="bcc93-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="bcc93-164">有关详细信息，请参阅 [类型提升](../../programming-guide/language-features/declared-elements/type-promotion.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc93-164">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="bcc93-165">仅当其完全限定的路径相同时，编译器才将合并分部定义。</span><span class="sxs-lookup"><span data-stu-id="bcc93-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="bcc93-166">`Partial` 关键字可用于以下上下文中：</span><span class="sxs-lookup"><span data-stu-id="bcc93-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bcc93-167">Class 语句</span><span class="sxs-lookup"><span data-stu-id="bcc93-167">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="bcc93-168">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="bcc93-168">Structure Statement</span></span>](../statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="bcc93-169">示例</span><span class="sxs-lookup"><span data-stu-id="bcc93-169">Example</span></span>  

 <span data-ttu-id="bcc93-170">下面的示例将类 `sampleClass` 的定义拆分到两个声明中，其中每一个均定义一个不同的 `Sub` 过程。</span><span class="sxs-lookup"><span data-stu-id="bcc93-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="bcc93-171">前面示例中的两个分部定义可能在同一源文件中或在两个不同的源文件中。</span><span class="sxs-lookup"><span data-stu-id="bcc93-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc93-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bcc93-172">See also</span></span>

- [<span data-ttu-id="bcc93-173">Class 语句</span><span class="sxs-lookup"><span data-stu-id="bcc93-173">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="bcc93-174">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="bcc93-174">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="bcc93-175">类型提升</span><span class="sxs-lookup"><span data-stu-id="bcc93-175">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="bcc93-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="bcc93-176">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="bcc93-177">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bcc93-177">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="bcc93-178">分部方法</span><span class="sxs-lookup"><span data-stu-id="bcc93-178">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
