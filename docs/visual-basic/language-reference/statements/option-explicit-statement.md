---
title: Option Explicit 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 44bf8205ec071710ee3660968ab3c3e9af33f74d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874940"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="c073c-102">Option Explicit 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c073c-102">Option Explicit Statement (Visual Basic)</span></span>

<span data-ttu-id="c073c-103">强制显式声明文件中的所有变量，或允许隐式声明变量。</span><span class="sxs-lookup"><span data-stu-id="c073c-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c073c-104">语法</span><span class="sxs-lookup"><span data-stu-id="c073c-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="c073c-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="c073c-105">Parts</span></span>  

 `On`  
 <span data-ttu-id="c073c-106">可选。</span><span class="sxs-lookup"><span data-stu-id="c073c-106">Optional.</span></span> <span data-ttu-id="c073c-107">启用 `Option Explicit` 检查。</span><span class="sxs-lookup"><span data-stu-id="c073c-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="c073c-108">如果 `On` `Off` 未指定或，则默认值为 `On` 。</span><span class="sxs-lookup"><span data-stu-id="c073c-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="c073c-109">可选。</span><span class="sxs-lookup"><span data-stu-id="c073c-109">Optional.</span></span> <span data-ttu-id="c073c-110">禁用 `Option Explicit` 检查。</span><span class="sxs-lookup"><span data-stu-id="c073c-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c073c-111">备注</span><span class="sxs-lookup"><span data-stu-id="c073c-111">Remarks</span></span>  

 <span data-ttu-id="c073c-112">当 `Option Explicit On` 或 `Option Explicit` 出现在文件中时，必须使用或语句显式声明所有变量 `Dim` `ReDim` 。</span><span class="sxs-lookup"><span data-stu-id="c073c-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="c073c-113">如果尝试使用未声明的变量名称，则会在编译时出现错误。</span><span class="sxs-lookup"><span data-stu-id="c073c-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="c073c-114">`Option Explicit Off`语句允许隐式声明变量。</span><span class="sxs-lookup"><span data-stu-id="c073c-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="c073c-115">使用时，`Option Explicit` 语句必须在文件中任何其他源代码语句之前。</span><span class="sxs-lookup"><span data-stu-id="c073c-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c073c-116">将设置 `Option Explicit` 为 `Off` 通常不是好的做法。</span><span class="sxs-lookup"><span data-stu-id="c073c-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="c073c-117">在一个或多个位置拼错变量名称，将会在程序运行时导致意想不到的结果。</span><span class="sxs-lookup"><span data-stu-id="c073c-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="c073c-118">当选项显式语句不存在时</span><span class="sxs-lookup"><span data-stu-id="c073c-118">When an Option Explicit Statement Is Not Present</span></span>  

 <span data-ttu-id="c073c-119">如果源代码不包含 `Option Explicit` 语句，则使用 "编译" 页上的 " **Option Explicit** " 设置，将使用 " [项目设计器" (Visual Basic) ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。</span><span class="sxs-lookup"><span data-stu-id="c073c-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="c073c-120">如果使用命令行编译器，则使用 [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="c073c-120">If the command-line compiler is used, the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="c073c-121">在 IDE 中设置 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="c073c-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="c073c-122">在 **解决方案资源管理器**中，选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="c073c-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="c073c-123">在“项目”菜单上，单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="c073c-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="c073c-124">单击“编译”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c073c-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="c073c-125">在 " **选项** " 框中设置值。</span><span class="sxs-lookup"><span data-stu-id="c073c-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="c073c-126">创建新项目时，"**编译**" 选项卡上的 " **option explicit** " 设置设置为 " **VB 默认值**" 对话框中的 "选项" "**显式**设置"。</span><span class="sxs-lookup"><span data-stu-id="c073c-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="c073c-127">若要访问 " **VB 默认值** " 对话框，请在 " **工具** " 菜单上单击 " **选项**"。</span><span class="sxs-lookup"><span data-stu-id="c073c-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="c073c-128">在“选项”对话框中，展开“项目和解决方案”，然后单击“VB 默认值”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c073c-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="c073c-129">**VB 默认**设置中的初始默认设置为 `On` 。</span><span class="sxs-lookup"><span data-stu-id="c073c-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="c073c-130">在命令行上设置 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="c073c-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="c073c-131">在**vbc**命令中包含[-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)编译器选项。</span><span class="sxs-lookup"><span data-stu-id="c073c-131">Include the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c073c-132">示例</span><span class="sxs-lookup"><span data-stu-id="c073c-132">Example</span></span>  

 <span data-ttu-id="c073c-133">下面的示例使用 `Option Explicit` 语句强制所有变量的显式声明。</span><span class="sxs-lookup"><span data-stu-id="c073c-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="c073c-134">尝试使用未声明的变量会导致编译时错误。</span><span class="sxs-lookup"><span data-stu-id="c073c-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="c073c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c073c-135">See also</span></span>

- [<span data-ttu-id="c073c-136">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="c073c-136">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="c073c-137">ReDim 语句</span><span class="sxs-lookup"><span data-stu-id="c073c-137">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="c073c-138">Option Compare 语句</span><span class="sxs-lookup"><span data-stu-id="c073c-138">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="c073c-139">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="c073c-139">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="c073c-140">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c073c-140">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="c073c-141">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c073c-141">-optionexplicit</span></span>](../../reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="c073c-142">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="c073c-142">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="c073c-143">“选项”对话框 ->“项目”->“Visual Basic 默认值”</span><span class="sxs-lookup"><span data-stu-id="c073c-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
