---
title: “#Region”和“#End Region”语句在方法体/多行 lambda 内无效
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: e3147b6192f54ce85d0fecd6b67f7d80f6281b54
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870880"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="cc78f-102">“#Region”和“#End Region”语句在方法体/多行 lambda 内无效</span><span class="sxs-lookup"><span data-stu-id="cc78f-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="cc78f-103">`#Region`必须在类、模块或命名空间级别声明块。</span><span class="sxs-lookup"><span data-stu-id="cc78f-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="cc78f-104">可折叠区域可以包含一个或多个过程，但不能在过程中开始或结束。</span><span class="sxs-lookup"><span data-stu-id="cc78f-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="cc78f-105">**错误 ID：** BC32025</span><span class="sxs-lookup"><span data-stu-id="cc78f-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc78f-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="cc78f-106">To correct this error</span></span>  
  
1. <span data-ttu-id="cc78f-107">确保使用或语句正确终止前面的过程 `End Function` `End Sub` 。</span><span class="sxs-lookup"><span data-stu-id="cc78f-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="cc78f-108">确保 `#Region` 和 `#End Region` 指令位于同一个代码块中。</span><span class="sxs-lookup"><span data-stu-id="cc78f-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc78f-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc78f-109">See also</span></span>

- [<span data-ttu-id="cc78f-110">#Region 指令</span><span class="sxs-lookup"><span data-stu-id="cc78f-110">#Region Directive</span></span>](../directives/region-directive.md)
