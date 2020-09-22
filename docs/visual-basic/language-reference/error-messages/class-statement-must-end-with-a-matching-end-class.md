---
title: “Class”语句必须以匹配的“End Class”结束
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: d67f0e71dbdbf97420ec5b5ba4b6f06acfba1bd9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874618"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="93f90-102">“Class”语句必须以匹配的“End Class”结束</span><span class="sxs-lookup"><span data-stu-id="93f90-102">'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="93f90-103">`Class` 用于启动 `Class` 块; 因此它只能出现在块的开头，并以匹配的 `End Class` 语句结束块。</span><span class="sxs-lookup"><span data-stu-id="93f90-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="93f90-104">您有冗余的 `Class` 语句，或者您没有 `Class` 用结束块 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="93f90-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="93f90-105">**错误 ID：** BC30481</span><span class="sxs-lookup"><span data-stu-id="93f90-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93f90-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="93f90-106">To correct this error</span></span>  
  
- <span data-ttu-id="93f90-107">找到并删除不必要的 `Class` 语句。</span><span class="sxs-lookup"><span data-stu-id="93f90-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="93f90-108">`Class`使用匹配的结束块 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="93f90-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f90-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93f90-109">See also</span></span>

- [<span data-ttu-id="93f90-110">End \<keyword> 语句</span><span class="sxs-lookup"><span data-stu-id="93f90-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="93f90-111">Class 语句</span><span class="sxs-lookup"><span data-stu-id="93f90-111">Class Statement</span></span>](../statements/class-statement.md)
