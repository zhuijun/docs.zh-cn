---
title: 无错误继续执行
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870830"
---
# <a name="resume-without-error"></a><span data-ttu-id="7ee42-102">无错误继续执行</span><span class="sxs-lookup"><span data-stu-id="7ee42-102">Resume without error</span></span>

<span data-ttu-id="7ee42-103">`Resume`语句出现在错误处理代码之外，或代码跳转到错误处理程序，即使没有出错。</span><span class="sxs-lookup"><span data-stu-id="7ee42-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ee42-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="7ee42-104">To correct this error</span></span>  
  
1. <span data-ttu-id="7ee42-105">将 `Resume` 语句移动到错误处理程序中，或将其删除。</span><span class="sxs-lookup"><span data-stu-id="7ee42-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="7ee42-106">跳转到标签不能跨过程出现，因此请在过程中搜索标识错误处理程序的标签。</span><span class="sxs-lookup"><span data-stu-id="7ee42-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="7ee42-107">如果找到指定为不是语句的语句目标的重复标签 `GoTo` `On Error GoTo` ，则更改行标签以同意其预期目标。</span><span class="sxs-lookup"><span data-stu-id="7ee42-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee42-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ee42-108">See also</span></span>

- [<span data-ttu-id="7ee42-109">Resume 语句</span><span class="sxs-lookup"><span data-stu-id="7ee42-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="7ee42-110">On Error 语句</span><span class="sxs-lookup"><span data-stu-id="7ee42-110">On Error Statement</span></span>](../statements/on-error-statement.md)
