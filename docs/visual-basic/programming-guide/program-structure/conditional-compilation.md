---
title: 条件编译
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e59296882edc018259816c73b6ae861b3b296783
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098964"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="1adbb-102">Visual Basic 中的条件编译</span><span class="sxs-lookup"><span data-stu-id="1adbb-102">Conditional Compilation in Visual Basic</span></span>

<span data-ttu-id="1adbb-103">在 *条件编译*中，程序中的特定代码块会有选择地编译，而其他代码块会被忽略。</span><span class="sxs-lookup"><span data-stu-id="1adbb-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="1adbb-104">例如，你可能想要编写调试语句来比较不同方法对相同编程任务的速度，或者可能想要针对多种语言对应用程序进行本地化。</span><span class="sxs-lookup"><span data-stu-id="1adbb-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="1adbb-105">条件编译语句设计为在编译时运行，而不是在运行时运行。</span><span class="sxs-lookup"><span data-stu-id="1adbb-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="1adbb-106">您可以用指令指示要有条件地编译的代码块 `#If...Then...#Else` 。</span><span class="sxs-lookup"><span data-stu-id="1adbb-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="1adbb-107">例如，若要从相同的源代码创建法语和德语版本的同一应用程序，可以 `#If...Then` 使用预定义的常量和将平台特定的代码段嵌入到语句中 `FrenchVersion` `GermanVersion` 。</span><span class="sxs-lookup"><span data-stu-id="1adbb-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="1adbb-108">下面的示例演示如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1adbb-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="1adbb-109">如果在 `FrenchVersion` 编译时将条件编译常量的值设置为 `True` ，则编译法语版本的条件代码。</span><span class="sxs-lookup"><span data-stu-id="1adbb-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="1adbb-110">如果将常量的值设置 `GermanVersion` 为 `True` ，则编译器将使用德语版本。</span><span class="sxs-lookup"><span data-stu-id="1adbb-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="1adbb-111">如果两者均未设置为 `True` ，则最后一个块中的代码将 `Else` 运行。</span><span class="sxs-lookup"><span data-stu-id="1adbb-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1adbb-112">当编辑代码时，自动完成功能将无法正常工作，如果代码不是当前分支的一部分，则使用条件编译指令。</span><span class="sxs-lookup"><span data-stu-id="1adbb-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="1adbb-113">声明条件编译常量</span><span class="sxs-lookup"><span data-stu-id="1adbb-113">Declaring Conditional Compilation Constants</span></span>  

 <span data-ttu-id="1adbb-114">可以通过以下三种方式之一来设置条件编译常量：</span><span class="sxs-lookup"><span data-stu-id="1adbb-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="1adbb-115">在**项目设计器**中</span><span class="sxs-lookup"><span data-stu-id="1adbb-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="1adbb-116">使用命令行编译器时在命令行上</span><span class="sxs-lookup"><span data-stu-id="1adbb-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="1adbb-117">在代码中</span><span class="sxs-lookup"><span data-stu-id="1adbb-117">In your code</span></span>  
  
 <span data-ttu-id="1adbb-118">条件编译常量具有特殊作用域，不能从标准代码进行访问。</span><span class="sxs-lookup"><span data-stu-id="1adbb-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="1adbb-119">条件编译常量的作用域取决于其设置方式。</span><span class="sxs-lookup"><span data-stu-id="1adbb-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="1adbb-120">下表列出了使用上述三种方法声明的常量的作用域。</span><span class="sxs-lookup"><span data-stu-id="1adbb-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="1adbb-121">如何设置常量</span><span class="sxs-lookup"><span data-stu-id="1adbb-121">How constant is set</span></span>|<span data-ttu-id="1adbb-122">常量范围</span><span class="sxs-lookup"><span data-stu-id="1adbb-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="1adbb-123">**项目设计器**</span><span class="sxs-lookup"><span data-stu-id="1adbb-123">**Project Designer**</span></span>|<span data-ttu-id="1adbb-124">公共到项目中的所有文件</span><span class="sxs-lookup"><span data-stu-id="1adbb-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="1adbb-125">命令行</span><span class="sxs-lookup"><span data-stu-id="1adbb-125">Command line</span></span>|<span data-ttu-id="1adbb-126">向传递到命令行编译器的所有文件公开</span><span class="sxs-lookup"><span data-stu-id="1adbb-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="1adbb-127">`#Const` 代码中的语句</span><span class="sxs-lookup"><span data-stu-id="1adbb-127">`#Const` statement in code</span></span>|<span data-ttu-id="1adbb-128">专用于声明它的文件</span><span class="sxs-lookup"><span data-stu-id="1adbb-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="1adbb-129">在项目设计器中设置常量</span><span class="sxs-lookup"><span data-stu-id="1adbb-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="1adbb-130">-在创建可执行文件之前，请按照[管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)中提供的步骤在 "**项目设计器**" 中设置常量。</span><span class="sxs-lookup"><span data-stu-id="1adbb-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="1adbb-131">在命令行中设置常量</span><span class="sxs-lookup"><span data-stu-id="1adbb-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="1adbb-132">-使用 **-d** 开关输入条件编译常量，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="1adbb-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="1adbb-133">**-D**开关和第一个常数之间不需要空格。</span><span class="sxs-lookup"><span data-stu-id="1adbb-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="1adbb-134">有关详细信息，请参阅 [-定义 (Visual Basic) ](../../reference/command-line-compiler/define.md)。</span><span class="sxs-lookup"><span data-stu-id="1adbb-134">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="1adbb-135">命令行声明会重写在 **项目设计器**中输入的声明，但不会将其删除。</span><span class="sxs-lookup"><span data-stu-id="1adbb-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="1adbb-136">在 **项目设计器** 中设置的参数对于后续编译仍有效。</span><span class="sxs-lookup"><span data-stu-id="1adbb-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="1adbb-137">在代码本身中编写常量时，没有严格的规则与它们的位置相关，因为它们的作用域是在其中声明它们的整个模块。</span><span class="sxs-lookup"><span data-stu-id="1adbb-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="1adbb-138">若要在代码中设置常量</span><span class="sxs-lookup"><span data-stu-id="1adbb-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="1adbb-139">-将常量放置在使用它们的模块的声明块中。</span><span class="sxs-lookup"><span data-stu-id="1adbb-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="1adbb-140">这有助于保持代码的组织和可读性。</span><span class="sxs-lookup"><span data-stu-id="1adbb-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="1adbb-141">相关主题</span><span class="sxs-lookup"><span data-stu-id="1adbb-141">Related Topics</span></span>  
  
|<span data-ttu-id="1adbb-142">Title</span><span class="sxs-lookup"><span data-stu-id="1adbb-142">Title</span></span>|<span data-ttu-id="1adbb-143">描述</span><span class="sxs-lookup"><span data-stu-id="1adbb-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="1adbb-144">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="1adbb-144">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="1adbb-145">提供使代码易于阅读和维护的建议。</span><span class="sxs-lookup"><span data-stu-id="1adbb-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="1adbb-146">参考</span><span class="sxs-lookup"><span data-stu-id="1adbb-146">Reference</span></span>  

 [<span data-ttu-id="1adbb-147">#Const 指令</span><span class="sxs-lookup"><span data-stu-id="1adbb-147">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="1adbb-148">#If...Then...#Else 指令</span><span class="sxs-lookup"><span data-stu-id="1adbb-148">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="1adbb-149">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1adbb-149">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
