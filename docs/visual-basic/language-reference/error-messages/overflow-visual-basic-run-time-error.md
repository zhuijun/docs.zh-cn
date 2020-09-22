---
title: 溢出（Visual Basic 运行时错误）
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: e287d6c24eca75d8bf20181a201056f467d6fc4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871219"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="a78bb-102">溢出（Visual Basic 运行时错误）</span><span class="sxs-lookup"><span data-stu-id="a78bb-102">Overflow (Visual Basic Run-Time Error)</span></span>

<span data-ttu-id="a78bb-103">如果尝试的赋值超出了赋值目标的限制，则会发生溢出。</span><span class="sxs-lookup"><span data-stu-id="a78bb-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a78bb-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="a78bb-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a78bb-105">请确保赋值、计算和数据类型转换的结果不太大，无法在此类型的值所允许的变量范围内表示，如果需要，可将值分配给可保存更大范围的值的类型变量。</span><span class="sxs-lookup"><span data-stu-id="a78bb-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="a78bb-106">请确保对属性的赋值符合它们所建立到的属性的范围。</span><span class="sxs-lookup"><span data-stu-id="a78bb-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="a78bb-107">请确保在转换为整数的计算中使用的数字没有大于整数的结果。</span><span class="sxs-lookup"><span data-stu-id="a78bb-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78bb-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a78bb-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="a78bb-109">数据类型</span><span class="sxs-lookup"><span data-stu-id="a78bb-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="a78bb-110">错误类型</span><span class="sxs-lookup"><span data-stu-id="a78bb-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
