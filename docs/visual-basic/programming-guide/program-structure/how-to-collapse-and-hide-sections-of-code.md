---
title: 如何：折叠和隐藏代码节
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404844"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="8be23-102">如何：折叠和隐藏代码节 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8be23-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="8be23-103">`#Region`指令使你可以折叠和隐藏 Visual Basic 文件中的代码段。</span><span class="sxs-lookup"><span data-stu-id="8be23-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="8be23-104">`#Region`使用指令，可以指定在使用 Visual Studio code 编辑器时可展开或折叠的代码块。</span><span class="sxs-lookup"><span data-stu-id="8be23-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="8be23-105">可以有选择地隐藏代码，使文件更易于管理且更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="8be23-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="8be23-106">有关详细信息，请参阅[大纲显示](/visualstudio/ide/outlining)。</span><span class="sxs-lookup"><span data-stu-id="8be23-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="8be23-107">`#Region`指令支持代码块语义，如 `#If...#End If` 。</span><span class="sxs-lookup"><span data-stu-id="8be23-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="8be23-108">这意味着它们不能以一个块开始，并在另一个块中结束;开始和结束必须在同一个块中。</span><span class="sxs-lookup"><span data-stu-id="8be23-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="8be23-109">`#Region`函数内不支持指令。</span><span class="sxs-lookup"><span data-stu-id="8be23-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="8be23-110">折叠和隐藏代码段</span><span class="sxs-lookup"><span data-stu-id="8be23-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="8be23-111">将代码段放置在 `#Region` 和语句之间 `#End Region` ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="8be23-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="8be23-112">`#Region`块可以在一个代码文件中多次使用; 因此，用户可以定义自己的过程和类块，进而可以进行折叠。</span><span class="sxs-lookup"><span data-stu-id="8be23-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="8be23-113">`#Region`块还可以嵌套在其他 `#Region` 块内。</span><span class="sxs-lookup"><span data-stu-id="8be23-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="8be23-114">隐藏代码不会阻止编译代码，也不会影响 `#If...#End If` 语句。</span><span class="sxs-lookup"><span data-stu-id="8be23-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="8be23-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8be23-115">See also</span></span>

- [<span data-ttu-id="8be23-116">条件编译</span><span class="sxs-lookup"><span data-stu-id="8be23-116">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="8be23-117">#Region 指令</span><span class="sxs-lookup"><span data-stu-id="8be23-117">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="8be23-118">#If...Then...#Else 指令</span><span class="sxs-lookup"><span data-stu-id="8be23-118">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="8be23-119">大纲显示</span><span class="sxs-lookup"><span data-stu-id="8be23-119">Outlining</span></span>](/visualstudio/ide/outlining)
