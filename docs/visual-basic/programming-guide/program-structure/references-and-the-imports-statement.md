---
title: 引用和 Imports 语句
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097899"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="dd80e-102">引用和 Imports 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd80e-102">References and the Imports Statement (Visual Basic)</span></span>

<span data-ttu-id="dd80e-103">通过选择 "**项目**" 菜单上的 "**添加引用**" 命令，可以使外部对象对项目可用。</span><span class="sxs-lookup"><span data-stu-id="dd80e-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="dd80e-104">Visual Basic 中的引用可指向程序集，这些程序集类似于类型库，但包含更多信息。</span><span class="sxs-lookup"><span data-stu-id="dd80e-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="dd80e-105">Imports 语句</span><span class="sxs-lookup"><span data-stu-id="dd80e-105">The Imports Statement</span></span>  

 <span data-ttu-id="dd80e-106">程序集包括一个或多个命名空间。</span><span class="sxs-lookup"><span data-stu-id="dd80e-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="dd80e-107">添加对程序集的引用时，还可以向模块添加一个 `Imports` 语句，该模块控制该程序集的命名空间在模块中的可见性。</span><span class="sxs-lookup"><span data-stu-id="dd80e-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="dd80e-108">`Imports`语句提供了一个范围上下文，该上下文允许只使用提供唯一引用所需的命名空间部分。</span><span class="sxs-lookup"><span data-stu-id="dd80e-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="dd80e-109">`Imports`语句具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="dd80e-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="dd80e-110">`Aliasname` 引用可以在代码中用来引用导入的命名空间的短名称。</span><span class="sxs-lookup"><span data-stu-id="dd80e-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="dd80e-111">`Namespace` 是通过项目引用、项目中的定义或通过上一条语句提供的命名空间 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="dd80e-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="dd80e-112">模块可以包含任意多个 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="dd80e-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="dd80e-113">它们必须出现在任何 `Option` 语句之后（如果存在），但在任何其他代码之前。</span><span class="sxs-lookup"><span data-stu-id="dd80e-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd80e-114">不要将项目引用与 `Imports` 语句或 `Declare` 语句混淆。</span><span class="sxs-lookup"><span data-stu-id="dd80e-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="dd80e-115">项目引用使外部对象（如程序集中的对象）可用于 Visual Basic 项目。</span><span class="sxs-lookup"><span data-stu-id="dd80e-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="dd80e-116">`Imports`语句用于简化对项目引用的访问，但不提供对这些对象的访问权限。</span><span class="sxs-lookup"><span data-stu-id="dd80e-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="dd80e-117">`Declare`语句用于声明对动态链接库中的外部过程的引用 (DLL) 。</span><span class="sxs-lookup"><span data-stu-id="dd80e-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="dd80e-118">在 Imports 语句中使用别名</span><span class="sxs-lookup"><span data-stu-id="dd80e-118">Using Aliases with the Imports Statement</span></span>  

 <span data-ttu-id="dd80e-119">使用 `Imports` 语句，无需显式键入引用的完全限定名，就能更轻松地访问类的方法。</span><span class="sxs-lookup"><span data-stu-id="dd80e-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="dd80e-120">使用别名可以为一个命名空间的一部分分配更友好的名称。</span><span class="sxs-lookup"><span data-stu-id="dd80e-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="dd80e-121">例如，在多行上显示一段文本的回车/换行符序列是 <xref:Microsoft.VisualBasic.ControlChars> 命名空间中的模块的一部分 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="dd80e-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="dd80e-122">若要在不带别名的程序中使用此常量，需要键入以下代码：</span><span class="sxs-lookup"><span data-stu-id="dd80e-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="dd80e-123">`Imports` 语句必须始终是紧跟在模块中的任何语句之后的第一行 `Option` 。</span><span class="sxs-lookup"><span data-stu-id="dd80e-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="dd80e-124">下面的代码段演示了如何导入和分配模块的别名 <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="dd80e-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="dd80e-125">以后引用此命名空间可能会大大缩短：</span><span class="sxs-lookup"><span data-stu-id="dd80e-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="dd80e-126">如果 `Imports` 语句不包含别名，则在导入的命名空间中定义的元素无需限定即可在模块中使用。</span><span class="sxs-lookup"><span data-stu-id="dd80e-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="dd80e-127">如果指定了别名，则必须将其用作该命名空间中包含的名称的限定符。</span><span class="sxs-lookup"><span data-stu-id="dd80e-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd80e-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="dd80e-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="dd80e-129">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="dd80e-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="dd80e-130">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="dd80e-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="dd80e-131">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="dd80e-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
