---
title: 如何：标记语句
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 8f04d592c51b6a0630bfe623fd3574555aef9ff8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403208"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="e5022-102">如何：标记语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5022-102">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="e5022-103">语句块由用冒号分隔的代码行组成。</span><span class="sxs-lookup"><span data-stu-id="e5022-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="e5022-104">以标识字符串或整数开头的代码行称为 "*标记*"。</span><span class="sxs-lookup"><span data-stu-id="e5022-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="e5022-105">语句标签用于标记代码行，以将其标识为与等语句一起使用 `On Error Goto` 。</span><span class="sxs-lookup"><span data-stu-id="e5022-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="e5022-106">标签可以是有效 Visual Basic 标识符（如标识编程元素的标识符），也可以是整数文本。</span><span class="sxs-lookup"><span data-stu-id="e5022-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="e5022-107">标签必须出现在源代码行的开头，并且必须后跟一个冒号，而不考虑它是否后跟同一行中的语句。</span><span class="sxs-lookup"><span data-stu-id="e5022-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="e5022-108">编译器通过检查行首是否与任何已定义的标识符匹配来标识标签。</span><span class="sxs-lookup"><span data-stu-id="e5022-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="e5022-109">如果不是，编译器将假定它是一个标签。</span><span class="sxs-lookup"><span data-stu-id="e5022-109">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="e5022-110">标签具有自己的声明空间，不会干扰其他标识符。</span><span class="sxs-lookup"><span data-stu-id="e5022-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="e5022-111">标签的范围是方法的主体。</span><span class="sxs-lookup"><span data-stu-id="e5022-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="e5022-112">标签声明优先于任何不明确的情况。</span><span class="sxs-lookup"><span data-stu-id="e5022-112">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="e5022-113">标签只能用于方法中的可执行语句。</span><span class="sxs-lookup"><span data-stu-id="e5022-113">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="e5022-114">为代码行添加标签</span><span class="sxs-lookup"><span data-stu-id="e5022-114">To label a line of code</span></span>

<span data-ttu-id="e5022-115">在源代码行的开头放置一个标识符，后跟一个冒号。</span><span class="sxs-lookup"><span data-stu-id="e5022-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="e5022-116">例如，以下代码行分别标记有 `Jump` 和 `120` ：</span><span class="sxs-lookup"><span data-stu-id="e5022-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="e5022-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5022-117">See also</span></span>

- [<span data-ttu-id="e5022-118">语句</span><span class="sxs-lookup"><span data-stu-id="e5022-118">Statements</span></span>](../language-features/statements.md)
- [<span data-ttu-id="e5022-119">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="e5022-119">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="e5022-120">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="e5022-120">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
