---
title: 自变量“Period”必须小于或等于自变量“Life”
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 0b20bb1fd1c0954e30262dd3a3b43d145226b7cc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367719"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a>自变量“Period”必须小于或等于自变量“Life”
`Period` 参数的值（指定计算资产折旧的时期）大于 `Life` 参数的值。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 确保 `Life` 和 `Period` 参数以相同的单位表示。 例如，如果 `Life` 以月为单位，则 `Period` 也应以月为单位。  
  
## <a name="see-also"></a>另请参阅

- [按值和按引用传递参数](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
