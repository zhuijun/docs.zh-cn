---
title: 常量必须是内部类型或者枚举类型，不能是类、结构、类型参数或数组类型
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: a9bbf27615233f4282e481710a0234b2fa589f63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874566"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>常量必须是内部类型或者枚举类型，不能是类、结构、类型参数或数组类型

您尝试将常量声明为类、结构或数组类型，或者声明为由包含泛型类型定义的类型参数。  
  
 常量必须是内部类型 (、、、、、、、、、、、、、 `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` 或 `UShort`) 或 `Enum` 基于其中一个整型类型的类型。  
  
 **错误 ID：** BC30424  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 将常量声明为内部类型或 `Enum` 类型。  
  
2. 常数也可以是一个特殊值 `True` ，如、 `False` 或 `Nothing` 。 编译器将这些预定义的值视为适当的内部类型。  
  
## <a name="see-also"></a>另请参阅

- [常量和枚举](../constants-and-enumerations.md)
- [数据类型](../../programming-guide/language-features/data-types/index.md)
- [数据类型](../data-types/index.md)
