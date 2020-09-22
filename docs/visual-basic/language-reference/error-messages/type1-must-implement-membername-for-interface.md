---
title: <type1>“<typename>”必须为接口“<interfacename>”实现“<membername>”
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 7b74ee3a05000f5d6cd94176b48dea116b647a2a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872169"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>“\<typename>”必须为接口“\<interfacename>”实现“\<membername>”

" \<typename> " 必须为接口 "" 实现 "" \<membername> \<interfacename> 。 实现属性必须具有匹配的 "ReadOnly"/"WriteOnly" 说明符。  
  
 类或结构声明实现接口，但不实现由接口定义的过程、属性或事件。 必须实现接口的每个成员。  
  
 **错误 ID：** BC30154  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 使用在接口中定义的相同名称和签名声明成员。 请确保至少包含 `End Function` 、 `End Sub` 或 `End Property` 语句。  
  
2. 将 `Implements` 子句添加到 `Function` 、、 `Sub` `Property` 或 `Event` 语句的末尾。 例如：  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. 实现某个属性时，请确保 `ReadOnly` 或的 `WriteOnly` 使用方式与接口定义中的相同。  
  
4. 在实现属性时，请 `Get` `Set` 根据需要声明和过程。  
  
## <a name="see-also"></a>另请参阅

- [Implements 语句](../statements/implements-statement.md)
- [接口](../../programming-guide/language-features/interfaces/index.md)
