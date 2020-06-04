---
title: 委托类“<classname>”没有 Invoke 方法，所以此类型的表达式不能作为方法调用的目标
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 27be97ba2930791bcb9012c824bc418a0089b037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409707"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>委托类“\<classname>”没有 Invoke 方法，所以此类型的表达式不能作为方法调用的目标
`Invoke`通过委托调用失败，因为 `Invoke` 未在委托类上实现。  
  
 **错误 ID：** BC30220  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 请确保已使用语句创建了委托类的实例 `Dim` ，并且已使用运算符将一个过程分配给了该委托实例 `AddressOf` 。  
  
2. 找到实现委托类的代码，并确保它实现 `Invoke` 过程。  
  
## <a name="see-also"></a>另请参阅

- [委托](../../programming-guide/language-features/delegates/index.md)
- [Delegate 语句](../statements/delegate-statement.md)
- [AddressOf 运算符](../operators/addressof-operator.md)
- [Dim 语句](../statements/dim-statement.md)
