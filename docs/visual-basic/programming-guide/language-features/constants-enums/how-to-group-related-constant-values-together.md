---
title: 如何：将相关的常量值组合在一起
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414435"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>如何：将相关的常量值组合在一起 (Visual Basic)
枚举是将相关常量组合在一起的最佳方式。 使用 `Enum` 类或模块的声明部分中的语句创建枚举。 有关详细信息，请参阅[如何：声明枚举](how-to-declare-enumerations.md)。  
  
### <a name="to-group-related-constant-values"></a>对相关常数值分组  
  
1. 编写包含代码访问级别、 `Enum` 关键字和有效名称的声明。 此示例创建 `Private` 枚举 `temperatureValues` 。  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. 定义枚举中的常量。 此示例创建 `Public` 枚举 `temperatureValues` 并分配其值。  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>另请参阅

- [枚举和名称限定](enumerations-and-name-qualification.md)
- [如何：引用枚举成员](how-to-refer-to-an-enumeration-member.md)
- [何时使用枚举](when-to-use-an-enumeration.md)
- [常量概述](constants-overview.md)
- [常数和文本数据类型](constant-and-literal-data-types.md)
- [常量和枚举](../../../language-reference/constants-and-enumerations.md)
