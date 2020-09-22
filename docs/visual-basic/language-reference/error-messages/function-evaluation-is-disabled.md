---
title: 已禁用函数求值，因为前一个函数求值超时
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 9bdc12e3dc57b440ed9f304201b8ec401db37871
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874069"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>已禁用函数求值，因为前一个函数求值超时

已禁用函数求值，因为上一个函数求值超时。若要重新启用函数求值，请再次单步执行或重新启动调试。  
  
 在 Visual Studio 调试器中，表达式指定了一个过程调用，但另一个计算已超时。  
  
 过程调用超时的可能原因包括无限循环或 *无限循环*。 有关详细信息，请参阅 [For .。。下一语句](../statements/for-next-statement.md)。  
  
 无限循环的一种特殊情况是 " *递归*"。 有关详细信息，请参阅 [递归过程](../../programming-guide/language-features/procedures/recursive-procedures.md)。  
  
 **错误 ID：** BC30957  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 如果可能，请确定以前的函数求值以及导致其超时的原因。否则，可能会再次遇到此错误。  
  
2. 再次单步执行调试器，或终止并重新启动调试。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Studio 中进行调试](/visualstudio/debugger/debugger-feature-tour)
- [使用调试器浏览代码](/visualstudio/debugger/navigating-through-code-with-the-debugger)
