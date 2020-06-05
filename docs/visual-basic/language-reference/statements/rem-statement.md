---
title: REM 语句
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 68c898145bd8845c657b6ebb8776a3a9027c359c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404260"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="35cbe-102">REM 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35cbe-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="35cbe-103">用于在程序的源代码中包括解释性注释。</span><span class="sxs-lookup"><span data-stu-id="35cbe-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35cbe-104">语法</span><span class="sxs-lookup"><span data-stu-id="35cbe-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="35cbe-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="35cbe-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="35cbe-106">可选。</span><span class="sxs-lookup"><span data-stu-id="35cbe-106">Optional.</span></span> <span data-ttu-id="35cbe-107">要包括的任何注释的文本。</span><span class="sxs-lookup"><span data-stu-id="35cbe-107">The text of any comment you want to include.</span></span> <span data-ttu-id="35cbe-108">关键字和之间必须有一个空格 `REM` `comment` 。</span><span class="sxs-lookup"><span data-stu-id="35cbe-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35cbe-109">备注</span><span class="sxs-lookup"><span data-stu-id="35cbe-109">Remarks</span></span>  
 <span data-ttu-id="35cbe-110">您可以将 `REM` 语句放在一行上，也可以将其放在另一语句后面的行上。</span><span class="sxs-lookup"><span data-stu-id="35cbe-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="35cbe-111">`REM`语句必须是行中的最后一条语句。</span><span class="sxs-lookup"><span data-stu-id="35cbe-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="35cbe-112">如果它跟在另一语句之后，则 `REM` 必须用空格将其与该语句分隔开。</span><span class="sxs-lookup"><span data-stu-id="35cbe-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="35cbe-113">您可以使用单引号（ `'` ），而不是 `REM` 。</span><span class="sxs-lookup"><span data-stu-id="35cbe-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="35cbe-114">无论您的注释是在同一行后面还是单独的行上，都是如此。</span><span class="sxs-lookup"><span data-stu-id="35cbe-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35cbe-115">不能 `REM` 使用行继续符（）继续执行语句 `_` 。</span><span class="sxs-lookup"><span data-stu-id="35cbe-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="35cbe-116">注释开始后，编译器不会检查字符的特殊含义。</span><span class="sxs-lookup"><span data-stu-id="35cbe-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="35cbe-117">对于多行注释，请 `REM` 在每行上使用另一个语句或注释符号（ `'` ）。</span><span class="sxs-lookup"><span data-stu-id="35cbe-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35cbe-118">示例</span><span class="sxs-lookup"><span data-stu-id="35cbe-118">Example</span></span>  
 <span data-ttu-id="35cbe-119">下面的示例说明 `REM` 语句，该语句用于在程序中包含解释性注释。</span><span class="sxs-lookup"><span data-stu-id="35cbe-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="35cbe-120">它还显示了使用单引号（ `'` ）而不是的的替代方法 `REM` 。</span><span class="sxs-lookup"><span data-stu-id="35cbe-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="35cbe-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35cbe-121">See also</span></span>

- [<span data-ttu-id="35cbe-122">代码中的注释</span><span class="sxs-lookup"><span data-stu-id="35cbe-122">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="35cbe-123">如何：在代码中拆分和合并语句</span><span class="sxs-lookup"><span data-stu-id="35cbe-123">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
