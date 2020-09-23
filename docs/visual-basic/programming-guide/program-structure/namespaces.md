---
title: 命名空间
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: f4521fa10c3bb9e8e121e3c228a23061becd1741
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072192"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="8c3c5-102">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="8c3c5-102">Namespaces in Visual Basic</span></span>

<span data-ttu-id="8c3c5-103">命名空间组织程序集中定义的对象。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="8c3c5-104">程序集可以包含多个命名空间，命名空间又可以包含其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="8c3c5-105">使用大组对象（比如类库）时，命名空间可以避免多义性和简化引用。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="8c3c5-106">例如，.NET Framework 在 <xref:System.Windows.Forms.ListBox> 命名空间中定义类 <xref:System.Windows.Forms?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8c3c5-107">以下代码段演示如何使用此类的完全限定名称声明变量：</span><span class="sxs-lookup"><span data-stu-id="8c3c5-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="8c3c5-108">避免名称冲突</span><span class="sxs-lookup"><span data-stu-id="8c3c5-108">Avoiding Name Collisions</span></span>  

 <span data-ttu-id="8c3c5-109">.NET Framework 命名空间解决有时被称为 *命名空间污染*的问题，在这种情况下，类库的开发人员会受到另一个库中使用类似名称的阻碍。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="8c3c5-110">这些冲突及其现有组件有时被称为 *名称冲突*。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="8c3c5-111">例如，如果创建一个名为 `ListBox`的新类，你可以在项目中不加限定地使用它。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="8c3c5-112">但是，如果您想要 <xref:System.Windows.Forms.ListBox> 在同一项目中使用 .NET Framework 类，则必须使用完全限定引用来使引用唯一。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="8c3c5-113">如果引用不唯一，Visual Basic 将产生一个错误，指出名称不明确。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="8c3c5-114">下面的代码示例演示如何声明这些对象：</span><span class="sxs-lookup"><span data-stu-id="8c3c5-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="8c3c5-115">下图显示了两个命名空间层次结构，它们都包含一个名为的对象 `ListBox` ：</span><span class="sxs-lookup"><span data-stu-id="8c3c5-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![显示两个命名空间层次结构的屏幕截图。](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="8c3c5-117">默认情况下，使用 Visual Basic 创建的每个可执行文件都包含与项目具有相同名称的命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="8c3c5-118">例如，如果在一个名为 `ListBoxProject`的项目中定义对象，则可执行文件 ListBoxProject.exe 包含一个名为 `ListBoxProject`的命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="8c3c5-119">多个程序集可以使用相同的命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="8c3c5-120">Visual Basic 将它们视为一组名称。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="8c3c5-121">例如，你可以为名为 `SomeNameSpace` 的程序集中名为 `Assemb1`的命名空间定义多个类，并为名为 `Assemb2`的程序集中相同的命名空间定义其他类。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="8c3c5-122">完全限定名</span><span class="sxs-lookup"><span data-stu-id="8c3c5-122">Fully Qualified Names</span></span>  

 <span data-ttu-id="8c3c5-123">完全限定名是以在其中定义对象的命名空间的名称为前缀的对象引用。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="8c3c5-124">如果创建对类的引用（通过选择“项目” \*\*\*\* 菜单中的“添加引用” \*\*\*\* ），然后为代码中的对象使用完全限定名，则可以使用在其他项目中定义的对象。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="8c3c5-125">以下代码段演示如何为来自另一个项目命名空间的对象使用完全限定名：</span><span class="sxs-lookup"><span data-stu-id="8c3c5-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="8c3c5-126">完全限定名避免命名冲突，因为它们可以使编译器确定哪些对象正在被使用。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="8c3c5-127">但是，名称本身可能会变得冗长繁杂。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="8c3c5-128">为避免这一问题，可以使用 `Imports` 语句来定义 *别名*- 可用于代替完全限定名的缩略名。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="8c3c5-129">例如，以下代码示例为两个完全限定名创建别名，并使用这些别名来定义两个对象。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="8c3c5-130">如果不带别名使用 `Imports` 语句，可以使用命名空间中的所有名称而无需限定，只要这些名称唯一。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="8c3c5-131">如果项目包含同名的项的命名空间使用的 `Imports` 语句，则使用时必须完全限定该名称。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="8c3c5-132">例如，假设项目包含以下两个 `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="8c3c5-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="8c3c5-133">如果尝试使用 `Class1` 而不对其完全限定，Visual Basic 会生成一个错误，指出名称 `Class1` 不明确。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="8c3c5-134">命名空间级别语句</span><span class="sxs-lookup"><span data-stu-id="8c3c5-134">Namespace Level Statements</span></span>  

 <span data-ttu-id="8c3c5-135">在命名空间中，可以定义项，如模块、接口、类、委托、枚举、结构和其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="8c3c5-136">无法在命名空间级别定义属性、过程、变量和事件等项。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="8c3c5-137">这些项必须在模块、结构或类等容器内部进行声明。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="8c3c5-138">完全限定名中的全局关键字</span><span class="sxs-lookup"><span data-stu-id="8c3c5-138">Global Keyword in Fully Qualified Names</span></span>  

 <span data-ttu-id="8c3c5-139">如果定义了命名空间的嵌套层次结构，该层次结构内的代码可能会被阻止访问 .NET Framework 的 <xref:System?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="8c3c5-140">下面的示例阐释了 `SpecialSpace.System` 命名空间阻止访问 <xref:System?displayProperty=nameWithType>的层次结构。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="8c3c5-141">结果是，Visual Basic 编译器无法成功地解析对 <xref:System.Int32?displayProperty=nameWithType>的引用，因为 `SpecialSpace.System` 没有定义 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="8c3c5-142">可以使用 `Global` 关键字在.NET Framework 类库的最外层级别上启动限定链。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="8c3c5-143">这将允许你指定类库中的 <xref:System?displayProperty=nameWithType> 命名空间或任何其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="8c3c5-144">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-144">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="8c3c5-145">可以使用 `Global` 访问其他根级别的命名空间，如 <xref:Microsoft.VisualBasic?displayProperty=nameWithType>和与项目相关联的任何命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="8c3c5-146">命名空间语句中的全局关键字</span><span class="sxs-lookup"><span data-stu-id="8c3c5-146">Global Keyword in Namespace Statements</span></span>  

 <span data-ttu-id="8c3c5-147">还可以使用 `Global` 中的 [Global](../../language-reference/statements/namespace-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-147">You can also use the `Global` keyword in a [Namespace Statement](../../language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="8c3c5-148">这将允许你定义项目根命名空间之外的命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="8c3c5-149">项目中的所有命名空间均基于项目的根命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="8c3c5-150">Visual Studio 针对项目中的所有代码，将项目名称指定为默认根命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="8c3c5-151">例如，如果项目命名为 `ConsoleApplication1`，则其编程元素属于命名空间 `ConsoleApplication1`。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="8c3c5-152">如果声明 `Namespace Magnetosphere`，项目中对 `Magnetosphere` 的引用将访问 `ConsoleApplication1.Magnetosphere`。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="8c3c5-153">以下示例使用 `Global` 关键字来为项目声明根命名空间之外的命名空间。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="8c3c5-154">在命名空间声明中， `Global` 不能嵌套于另一个命名空间中。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="8c3c5-155">可以使用 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) 查看和修改项目的“根命名空间” \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="8c3c5-156">对于新项目，“根命名空间” \*\*\*\* 默认为该项目的名称。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="8c3c5-157">若要使 `Global` 成为顶级命名空间，可以清除“根命名空间” \*\*\*\* 条目，以便此框为空。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="8c3c5-158">清除“根命名空间” \*\*\*\* 移除了命名空间声明中需要的 `Global` 关键字。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="8c3c5-159">如果 `Namespace` 语句声明一个名称，而该名称也是.NET Framework 中的命名空间，则如果 `Global` 关键字未在完全限定名中使用，.NET Framework 命名空间会变得不可用。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="8c3c5-160">在不使用 `Global` 关键字的情况下，若要启用对该 .NET Framework 命名空间的访问，可以将 `Global` 关键字包括到 `Namespace` 语句中。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="8c3c5-161">以下示例在 `Global` 命名空间声明中具有 `System.Text` 关键字。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="8c3c5-162">如果命名空间声明中不存在 `Global` 关键字，若不指定 <xref:System.Text.StringBuilder> 将无法访问 `Global.System.Text.StringBuilder`。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="8c3c5-163">对于名为 `ConsoleApplication1`的项目，如果未使用 `System.Text` 关键字，对 `ConsoleApplication1.System.Text` 的引用会访问 `Global` 。</span><span class="sxs-lookup"><span data-stu-id="8c3c5-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="8c3c5-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="8c3c5-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="8c3c5-165">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="8c3c5-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="8c3c5-166">引用和 Imports 语句</span><span class="sxs-lookup"><span data-stu-id="8c3c5-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="8c3c5-167">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="8c3c5-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="8c3c5-168">在 Office 解决方案中编写代码</span><span class="sxs-lookup"><span data-stu-id="8c3c5-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
