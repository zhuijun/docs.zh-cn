---
title: Stop 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: c9226ccaea9a0709a9d6a49900f69cb9ac9e1dbe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871741"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="0f1da-102">Stop 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f1da-102">Stop Statement (Visual Basic)</span></span>

<span data-ttu-id="0f1da-103">挂起执行。</span><span class="sxs-lookup"><span data-stu-id="0f1da-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f1da-104">语法</span><span class="sxs-lookup"><span data-stu-id="0f1da-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="0f1da-105">备注</span><span class="sxs-lookup"><span data-stu-id="0f1da-105">Remarks</span></span>  

 <span data-ttu-id="0f1da-106">您可以 `Stop` 在过程中的任何位置放置语句来挂起执行。</span><span class="sxs-lookup"><span data-stu-id="0f1da-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="0f1da-107">使用 `Stop` 语句与在代码中设置断点类似。</span><span class="sxs-lookup"><span data-stu-id="0f1da-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="0f1da-108">`Stop`语句暂停执行，但与 `End` 此不同，它不会关闭任何文件或清除任何变量，除非在已编译的可执行文件 ( .exe) 文件中出现。</span><span class="sxs-lookup"><span data-stu-id="0f1da-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f1da-109">如果 `Stop` 在集成开发环境外部运行的代码中遇到语句 (IDE) ，则调用调试器。</span><span class="sxs-lookup"><span data-stu-id="0f1da-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="0f1da-110">无论代码是在调试模式下编译还是在发布模式下编译，都是如此。</span><span class="sxs-lookup"><span data-stu-id="0f1da-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f1da-111">示例</span><span class="sxs-lookup"><span data-stu-id="0f1da-111">Example</span></span>  

 <span data-ttu-id="0f1da-112">此示例使用 `Stop` 语句通过循环挂起每个迭代的执行 `For...Next` 。</span><span class="sxs-lookup"><span data-stu-id="0f1da-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="0f1da-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f1da-113">See also</span></span>

- [<span data-ttu-id="0f1da-114">End 语句</span><span class="sxs-lookup"><span data-stu-id="0f1da-114">End Statement</span></span>](end-statement.md)
