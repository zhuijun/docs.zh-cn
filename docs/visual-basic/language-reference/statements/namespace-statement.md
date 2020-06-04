---
title: Namespace 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 0f1ba9a038fc604b6e4ede758891832e087fc096
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404429"
---
# <a name="namespace-statement"></a><span data-ttu-id="9f901-102">Namespace 语句</span><span class="sxs-lookup"><span data-stu-id="9f901-102">Namespace Statement</span></span>
<span data-ttu-id="9f901-103">声明命名空间的名称，并导致在该命名空间中编译跟在声明后的源代码。</span><span class="sxs-lookup"><span data-stu-id="9f901-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f901-104">语法</span><span class="sxs-lookup"><span data-stu-id="9f901-104">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="9f901-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="9f901-105">Parts</span></span>  
 <span data-ttu-id="9f901-106">全球</span><span class="sxs-lookup"><span data-stu-id="9f901-106">Global</span></span>  
 <span data-ttu-id="9f901-107">可选。</span><span class="sxs-lookup"><span data-stu-id="9f901-107">Optional.</span></span> <span data-ttu-id="9f901-108">允许你在项目的根命名空间外定义命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="9f901-109">请参阅[Visual Basic 中的命名空间](../../programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="9f901-109">See [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="9f901-110">必需。</span><span class="sxs-lookup"><span data-stu-id="9f901-110">Required.</span></span> <span data-ttu-id="9f901-111">标识命名空间的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="9f901-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="9f901-112">必须是有效的 Visual Basic 标识符。</span><span class="sxs-lookup"><span data-stu-id="9f901-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="9f901-113">有关详细信息，请参阅已[声明的元素名称](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="9f901-113">For more information, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="9f901-114">可选。</span><span class="sxs-lookup"><span data-stu-id="9f901-114">Optional.</span></span> <span data-ttu-id="9f901-115">构成命名空间的元素。</span><span class="sxs-lookup"><span data-stu-id="9f901-115">Elements that make up the namespace.</span></span> <span data-ttu-id="9f901-116">其中包括但不限于枚举、结构、接口、类、模块、委托和其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="9f901-117">终止 `Namespace` 块。</span><span class="sxs-lookup"><span data-stu-id="9f901-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f901-118">备注</span><span class="sxs-lookup"><span data-stu-id="9f901-118">Remarks</span></span>  
 <span data-ttu-id="9f901-119">命名空间用作组织系统。</span><span class="sxs-lookup"><span data-stu-id="9f901-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="9f901-120">它们提供了一种方法来分类和显示向其他程序和应用程序公开的编程元素。</span><span class="sxs-lookup"><span data-stu-id="9f901-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="9f901-121">请注意，在类或结构为的意义上，命名空间不是*类型*，不能将编程元素声明为具有命名空间的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9f901-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="9f901-122">语句后声明的所有编程元素都 `Namespace` 属于该命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="9f901-123">Visual Basic 继续将元素编译到最后一个声明的命名空间中，直到它遇到 `End Namespace` 语句或另一个 `Namespace` 语句。</span><span class="sxs-lookup"><span data-stu-id="9f901-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="9f901-124">如果命名空间已定义，即使是项目外部的命名空间，也可以向其中添加编程元素。</span><span class="sxs-lookup"><span data-stu-id="9f901-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="9f901-125">为此，请使用 `Namespace` 语句来指示 Visual Basic 将元素编译到该命名空间中。</span><span class="sxs-lookup"><span data-stu-id="9f901-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="9f901-126">只能 `Namespace` 在文件或命名空间级别使用语句。</span><span class="sxs-lookup"><span data-stu-id="9f901-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="9f901-127">这意味着命名空间的*声明上下文*必须是源文件或其他命名空间，不能是类、结构、模块、接口或过程。</span><span class="sxs-lookup"><span data-stu-id="9f901-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="9f901-128">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9f901-128">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="9f901-129">可以在另一个命名空间中声明一个命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-129">You can declare one namespace within another.</span></span> <span data-ttu-id="9f901-130">您可以声明的嵌套级别没有严格限制，但是请记住，如果其他代码访问在最内层命名空间中声明的元素，则必须使用包含嵌套层次结构中所有命名空间名称的限定字符串。</span><span class="sxs-lookup"><span data-stu-id="9f901-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="9f901-131">访问级别</span><span class="sxs-lookup"><span data-stu-id="9f901-131">Access Level</span></span>  
 <span data-ttu-id="9f901-132">命名空间将被视为具有 `Public` 访问级别。</span><span class="sxs-lookup"><span data-stu-id="9f901-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="9f901-133">可以从同一项目中的任何位置、引用该项目的其他项目以及从项目生成的任何程序集访问该命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="9f901-134">在命名空间级别声明的编程元素（在命名空间中，而不是在任何其他元素内）可以具有 `Public` 或 `Friend` 访问。</span><span class="sxs-lookup"><span data-stu-id="9f901-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="9f901-135">如果未指定，则默认情况下，此类元素的访问级别使用 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="9f901-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="9f901-136">可在命名空间级别声明的元素包括类、结构、模块、接口、枚举和委托。</span><span class="sxs-lookup"><span data-stu-id="9f901-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="9f901-137">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9f901-137">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="9f901-138">根命名空间</span><span class="sxs-lookup"><span data-stu-id="9f901-138">Root Namespace</span></span>  
 <span data-ttu-id="9f901-139">项目中的所有命名空间名称都基于*根命名空间*。</span><span class="sxs-lookup"><span data-stu-id="9f901-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="9f901-140">Visual Studio 针对项目中的所有代码，将项目名称指定为默认根命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="9f901-141">例如，如果项目命名为 `Payroll`，则其编程元素属于命名空间 `Payroll`。</span><span class="sxs-lookup"><span data-stu-id="9f901-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="9f901-142">如果声明 `Namespace funding` ，则该命名空间的完整名称为 `Payroll.funding` 。</span><span class="sxs-lookup"><span data-stu-id="9f901-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="9f901-143">如果要在语句中指定现有命名空间（ `Namespace` 如泛型列表类示例中所示），可以将根命名空间设置为 null 值。</span><span class="sxs-lookup"><span data-stu-id="9f901-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="9f901-144">为此，请单击 "**项目**" 菜单中的 "**项目属性**"，然后清除 "**根命名空间**" 条目，以便此框为空。</span><span class="sxs-lookup"><span data-stu-id="9f901-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="9f901-145">如果未在泛型列表类示例中执行此操作，则 Visual Basic 编译器会将 `System.Collections.Generic` 项目中的新命名空间作为的 `Payroll` 完整名称 `Payroll.System.Collections.Generic` 。</span><span class="sxs-lookup"><span data-stu-id="9f901-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="9f901-146">或者，可以使用 `Global` 关键字来引用在项目外部定义的命名空间的元素。</span><span class="sxs-lookup"><span data-stu-id="9f901-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="9f901-147">这样做可以使项目名称保留为根命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="9f901-148">这可以减少无意中将您的编程元素与现有命名空间的合并。</span><span class="sxs-lookup"><span data-stu-id="9f901-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="9f901-149">有关详细信息，请参阅[Visual Basic 中命名空间](../../programming-guide/program-structure/namespaces.md)的 "完全限定名称中的全局关键字" 部分。</span><span class="sxs-lookup"><span data-stu-id="9f901-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="9f901-150">`Global`关键字还可以在命名空间语句中使用。</span><span class="sxs-lookup"><span data-stu-id="9f901-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="9f901-151">这将允许你定义项目根命名空间之外的命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="9f901-152">有关详细信息，请参阅[Visual Basic 的命名空间](../../programming-guide/program-structure/namespaces.md)中的 "命名空间语句中的全局关键字" 部分。</span><span class="sxs-lookup"><span data-stu-id="9f901-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="9f901-153">**有关.**</span><span class="sxs-lookup"><span data-stu-id="9f901-153">**Troubleshooting.**</span></span> <span data-ttu-id="9f901-154">根命名空间可能会导致命名空间名称出现意外的串联。</span><span class="sxs-lookup"><span data-stu-id="9f901-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="9f901-155">如果你引用在项目外部定义的命名空间，则 Visual Basic 编译器可以将它们作为根命名空间中的嵌套命名空间 construe。</span><span class="sxs-lookup"><span data-stu-id="9f901-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="9f901-156">在这种情况下，编译器不能识别已在外部命名空间中定义的任何类型。</span><span class="sxs-lookup"><span data-stu-id="9f901-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="9f901-157">若要避免这种情况，请将根命名空间设置为空值（如 "根命名空间" 中所述）或使用 `Global` 关键字访问外部命名空间的元素。</span><span class="sxs-lookup"><span data-stu-id="9f901-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="9f901-158">特性和修饰符</span><span class="sxs-lookup"><span data-stu-id="9f901-158">Attributes and Modifiers</span></span>  
 <span data-ttu-id="9f901-159">不能将属性应用到命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="9f901-160">特性向程序集的元数据提供信息，这对于源分类器（如命名空间）没有意义。</span><span class="sxs-lookup"><span data-stu-id="9f901-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="9f901-161">不能将任何访问或过程修饰符或任何其他修饰符应用到命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="9f901-162">由于这不是类型，因此这些修饰符没有意义。</span><span class="sxs-lookup"><span data-stu-id="9f901-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f901-163">示例</span><span class="sxs-lookup"><span data-stu-id="9f901-163">Example</span></span>  
 <span data-ttu-id="9f901-164">下面的示例声明了两个命名空间，一个嵌套在另一个。</span><span class="sxs-lookup"><span data-stu-id="9f901-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a><span data-ttu-id="9f901-165">示例</span><span class="sxs-lookup"><span data-stu-id="9f901-165">Example</span></span>  
 <span data-ttu-id="9f901-166">下面的示例在一行上声明多个嵌套命名空间，并且它等效于前面的示例。</span><span class="sxs-lookup"><span data-stu-id="9f901-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="9f901-167">示例</span><span class="sxs-lookup"><span data-stu-id="9f901-167">Example</span></span>  
 <span data-ttu-id="9f901-168">以下示例访问在前面的示例中定义的类。</span><span class="sxs-lookup"><span data-stu-id="9f901-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="9f901-169">示例</span><span class="sxs-lookup"><span data-stu-id="9f901-169">Example</span></span>  
 <span data-ttu-id="9f901-170">下面的示例定义了一个新的泛型列表类的主干，并将其添加到了 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="9f901-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f901-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f901-171">See also</span></span>

- [<span data-ttu-id="9f901-172">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="9f901-172">Imports Statement (.NET Namespace and Type)</span></span>](imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="9f901-173">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="9f901-173">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="9f901-174">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="9f901-174">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
