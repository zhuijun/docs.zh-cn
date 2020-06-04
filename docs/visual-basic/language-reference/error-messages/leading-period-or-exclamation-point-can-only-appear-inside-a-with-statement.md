---
title: 前导“.”或“!”只能出现在“With”语句内
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397319"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>前导“.”或“!”只能出现在“With”语句内
不在块内部的句号（.）或惊叹号（！）在 `With` 左侧没有表达式。 成员访问（ `.` ）和字典成员访问（ `!` ）需要一个表达式，该表达式指定包含成员的元素。 这必须立即出现在访问器的左侧，或作为 `With` 包含成员访问的块的目标。  
  
 **错误 ID：** BC30157  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 确保块的 `With` 格式正确。  
  
2. 如果没有 `With` 块，请在取值函数左侧添加一个表达式，该表达式的计算结果为包含成员的已定义元素。  
  
## <a name="see-also"></a>另请参阅

- [代码中的特殊字符](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With 语句](../statements/with-end-with-statement.md)
