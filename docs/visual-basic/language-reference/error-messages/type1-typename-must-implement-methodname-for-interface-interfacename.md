---
title: <type1>“<typename>”必须为接口“<interfacename>”实现“<methodname>”
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 8bf8872277ec901e066a8b950aaf3e61babfcc48
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872102"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1>“\<typename>”必须为接口“\<interfacename>”实现“\<methodname>”

类或结构声明实现接口，但不实现由接口定义的过程。 必须实现接口的每个成员。  
  
 **错误 ID：** BC30149  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 使用在接口中定义的相同名称和签名声明过程。 请确保至少包含 `End Function` 或 `End Sub` 语句。  
  
2. 将 `Implements` 子句添加到或语句的末尾 `Function` `Sub` 。 例如：  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>另请参阅

- [Implements 语句](../statements/implements-statement.md)
- [接口](../../programming-guide/language-features/interfaces/index.md)
