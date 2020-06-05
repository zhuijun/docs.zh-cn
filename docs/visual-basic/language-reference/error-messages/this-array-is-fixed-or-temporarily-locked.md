---
title: 此数组是固定数组或被临时锁定
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 4a86460104b6c4d9d6791e60f6f377cec0030425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363028"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="54599-102">此数组被固定或临时锁定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54599-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="54599-103">此错误具有以下可能的原因：</span><span class="sxs-lookup"><span data-stu-id="54599-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="54599-104">使用 `ReDim` 更改固定大小数组的元素数。</span><span class="sxs-lookup"><span data-stu-id="54599-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="54599-105">Redimensioning 模块级动态数组，其中一个元素已作为参数传递给过程。</span><span class="sxs-lookup"><span data-stu-id="54599-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="54599-106">如果传递了某个元素，则会锁定数组，以防在过程中为引用参数释放内存。</span><span class="sxs-lookup"><span data-stu-id="54599-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="54599-107">尝试向 `Variant` 包含数组的变量赋值，但 `Variant` 当前已锁定。</span><span class="sxs-lookup"><span data-stu-id="54599-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54599-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="54599-108">To correct this error</span></span>  
  
1. <span data-ttu-id="54599-109">通过使用声明 `ReDim` （如果数组在过程中声明），或在不指定元素数的情况下（如果数组在模块级别声明），使原始数组成为动态的，而不是固定的。</span><span class="sxs-lookup"><span data-stu-id="54599-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="54599-110">确定是否确实需要传递元素，因为它在模块中的所有过程中可见。</span><span class="sxs-lookup"><span data-stu-id="54599-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="54599-111">确定锁定 `Variant` 和更正的内容。</span><span class="sxs-lookup"><span data-stu-id="54599-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54599-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54599-112">See also</span></span>

- [<span data-ttu-id="54599-113">数组</span><span class="sxs-lookup"><span data-stu-id="54599-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
