---
title: 索引数超过索引数组的维数
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 3fc2744bb471eabd9345994b28fbef3ebc76f00d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873660"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="0a314-102">索引数超过索引数组的维数</span><span class="sxs-lookup"><span data-stu-id="0a314-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>

<span data-ttu-id="0a314-103">用于访问数组元素的索引数必须完全等同于数组的秩，即为其声明的维数。</span><span class="sxs-lookup"><span data-stu-id="0a314-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="0a314-104">**错误 ID：** BC30106</span><span class="sxs-lookup"><span data-stu-id="0a314-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a314-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="0a314-105">To correct this error</span></span>  
  
- <span data-ttu-id="0a314-106">删除数组引用中的下标，直到下标的总数等于数组的秩。</span><span class="sxs-lookup"><span data-stu-id="0a314-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="0a314-107">例如：</span><span class="sxs-lookup"><span data-stu-id="0a314-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0a314-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a314-108">See also</span></span>

- [<span data-ttu-id="0a314-109">数组</span><span class="sxs-lookup"><span data-stu-id="0a314-109">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
