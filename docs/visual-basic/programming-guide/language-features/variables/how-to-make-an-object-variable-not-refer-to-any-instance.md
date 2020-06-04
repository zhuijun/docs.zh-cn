---
title: 如何：使对象变量不引用任何实例
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410446"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>如何：使对象变量不引用任何实例 (Visual Basic)
您可以通过将对象变量设置为 "[无](../../../language-reference/nothing.md)" 来解除对象变量与任何对象实例的关联。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>断开对象变量与任何对象实例的关联  
  
- `Nothing`在赋值语句中将变量设置为。  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>可靠编程  
 如果你的代码尝试访问已设置为的对象变量的成员 `Nothing` ，则 <xref:System.NullReferenceException> 会发生。 如果将一个对象变量设置为 `Nothing` "频繁"，或者如果可能该变量未初始化，则最好将成员访问包含在 `Try...Catch...Finally` 块中。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果对包含机密数据或敏感数据的对象使用对象变量，则可以将变量设置为，以便在 `Nothing` 不主动处理其中一个对象时使用。 这减少了恶意代码访问数据的可能性。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.NullReferenceException>
- [对象变量](object-variables.md)
- [对象变量赋值](object-variable-assignment.md)
- [Nothing](../../../language-reference/nothing.md)
- [Try...Catch...Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)
