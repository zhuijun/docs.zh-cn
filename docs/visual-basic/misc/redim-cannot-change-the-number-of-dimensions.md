---
title: “ReDim”无法更改维数
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b2404927c2faf30d1d058d2163fd5d67e1a52e1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358162"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="9d1b5-102">“ReDim”无法更改维数</span><span class="sxs-lookup"><span data-stu-id="9d1b5-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="9d1b5-103">某操作尝试使用 `ReDim` 更改数组的秩（维数）。</span><span class="sxs-lookup"><span data-stu-id="9d1b5-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="9d1b5-104">`ReDim` 可以更改已形式声明的数组的一个或多个维度的大小，但它不能更改数组的秩。</span><span class="sxs-lookup"><span data-stu-id="9d1b5-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d1b5-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="9d1b5-105">To correct this error</span></span>  
  
- <span data-ttu-id="9d1b5-106">确保想要更改的是数组的秩而不是其维度的大小，尽可能使用 `Dim` 声明具有所需秩的新数组。</span><span class="sxs-lookup"><span data-stu-id="9d1b5-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1b5-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d1b5-107">See also</span></span>

- [<span data-ttu-id="9d1b5-108">Visual Basic 中的数组</span><span class="sxs-lookup"><span data-stu-id="9d1b5-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9d1b5-109">Visual Basic 中的数组维度</span><span class="sxs-lookup"><span data-stu-id="9d1b5-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="9d1b5-110">ReDim 语句</span><span class="sxs-lookup"><span data-stu-id="9d1b5-110">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="9d1b5-111">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="9d1b5-111">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
