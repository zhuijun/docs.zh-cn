---
title: 序号无效
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7b9bd8435b56dd5e33d14eb35d76aacc7d60c8b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413047"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="8fed3-102">序号无效</span><span class="sxs-lookup"><span data-stu-id="8fed3-102">Ordinal is not valid</span></span>
<span data-ttu-id="8fed3-103">对动态链接库（DLL）的调用会使用语法，指示使用数字而不是过程名称 `#num` 。</span><span class="sxs-lookup"><span data-stu-id="8fed3-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="8fed3-104">此错误具有以下可能的原因：</span><span class="sxs-lookup"><span data-stu-id="8fed3-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="8fed3-105">尝试将 `#num` 表达式转换为序号失败。</span><span class="sxs-lookup"><span data-stu-id="8fed3-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="8fed3-106">指定的不 `#num` 指定 DLL 中的任何函数。</span><span class="sxs-lookup"><span data-stu-id="8fed3-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="8fed3-107">类型库具有无效的声明，导致内部使用的序号无效。</span><span class="sxs-lookup"><span data-stu-id="8fed3-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8fed3-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="8fed3-108">To correct this error</span></span>  
  
1. <span data-ttu-id="8fed3-109">请确保表达式表示有效数字，或按名称调用该过程。</span><span class="sxs-lookup"><span data-stu-id="8fed3-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="8fed3-110">请确保 `#num` 在 DLL 中标识有效函数。</span><span class="sxs-lookup"><span data-stu-id="8fed3-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="8fed3-111">通过注释掉代码，隔离导致问题的过程调用。</span><span class="sxs-lookup"><span data-stu-id="8fed3-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="8fed3-112">`Declare`为过程编写语句，并将问题报告给类型库供应商。</span><span class="sxs-lookup"><span data-stu-id="8fed3-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fed3-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fed3-113">See also</span></span>

- [<span data-ttu-id="8fed3-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="8fed3-114">Declare Statement</span></span>](../statements/declare-statement.md)
