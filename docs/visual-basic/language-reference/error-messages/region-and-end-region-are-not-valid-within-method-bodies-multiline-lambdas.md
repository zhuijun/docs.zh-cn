---
title: “#Region”和“#End Region”语句在方法体/多行 lambda 内无效
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: e3147b6192f54ce85d0fecd6b67f7d80f6281b54
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870880"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>“#Region”和“#End Region”语句在方法体/多行 lambda 内无效

`#Region`必须在类、模块或命名空间级别声明块。 可折叠区域可以包含一个或多个过程，但不能在过程中开始或结束。  
  
 **错误 ID：** BC32025  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 确保使用或语句正确终止前面的过程 `End Function` `End Sub` 。  
  
2. 确保 `#Region` 和 `#End Region` 指令位于同一个代码块中。  
  
## <a name="see-also"></a>另请参阅

- [#Region 指令](../directives/region-directive.md)
