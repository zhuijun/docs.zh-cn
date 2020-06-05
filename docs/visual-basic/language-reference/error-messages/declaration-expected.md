---
title: 需要声明
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 237622d0dc6c57f66d402f491a6191a5911574e2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409733"
---
# <a name="declaration-expected"></a>需要声明
Nondeclarative 语句，如赋值语句或循环语句，在任何过程外发生。 仅允许在过程外使用声明。  
  
 或者，在没有声明关键字（如或）的情况下声明编程元素 `Dim` `Const` 。  
  
 **错误 ID：** BC30188  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 将 nondeclarative 语句移到过程的主体。  
  
- 使用适当的声明关键字开始声明。  
  
- 确保声明关键字没有拼写错误。  
  
## <a name="see-also"></a>另请参阅

- [过程](../../programming-guide/language-features/procedures/index.md)
- [Dim 语句](../statements/dim-statement.md)
