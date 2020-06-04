---
title: 溢出（Visual Basic 运行时错误）
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387265"
---
# <a name="overflow-visual-basic-run-time-error"></a>溢出（Visual Basic 运行时错误）
如果尝试的赋值超出了赋值目标的限制，则会发生溢出。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 请确保赋值、计算和数据类型转换的结果不太大，无法在此类型的值所允许的变量范围内表示，如果需要，可将值分配给可保存更大范围的值的类型变量。  
  
2. 请确保对属性的赋值符合它们所建立到的属性的范围。  
  
3. 请确保在转换为整数的计算中使用的数字没有大于整数的结果。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [数据类型](../data-types/index.md)
- [错误类型](../../programming-guide/language-features/error-types.md)
