---
title: Nothing 和字符串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360561"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="7180a-102">Nothing 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7180a-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="7180a-103">当涉及到字符串时，Visual Basic 运行时和 .NET Framework 的评估 `Nothing` 方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="7180a-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="7180a-104">Visual Basic 运行时和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7180a-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="7180a-105">请看下面的示例：</span><span class="sxs-lookup"><span data-stu-id="7180a-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="7180a-106">Visual Basic 运行时通常计算 `Nothing` 为空字符串（""）。</span><span class="sxs-lookup"><span data-stu-id="7180a-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="7180a-107">但是，无论何时尝试对执行字符串操作，.NET Framework 都不会引发异常 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="7180a-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7180a-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7180a-108">See also</span></span>

- [<span data-ttu-id="7180a-109">字符串介绍 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7180a-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
