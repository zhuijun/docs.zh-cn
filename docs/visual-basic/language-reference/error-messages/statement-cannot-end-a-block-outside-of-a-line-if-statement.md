---
title: 语句不能在“If”语句行之外结束块
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 5e75c29e57a9c04c66e6bca79d99bb18c513f667
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870742"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>语句不能在“If”语句行之外结束块

单行 `If` 语句包含用冒号分隔的多个语句 (： ) ，其中一个语句 `End` 用于单个行外的控制块 `If` 。 单行 `If` 语句不使用 `End If` 语句。  
  
 **错误 ID：** BC32005  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 在 `If` 包含语句的控制块外移动单行语句 `End If` 。  
  
## <a name="see-also"></a>另请参阅

- [If...Then...Else 语句](../statements/if-then-else-statement.md)
