---
title: Alias 子句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408466"
---
# <a name="alias-clause-visual-basic"></a>Alias 子句 (Visual Basic)
指示外部过程在其 DLL 中有另一个名称。  
  
## <a name="remarks"></a>备注  
 `Alias`关键字可以在此上下文中使用：  
  
 [Declare Statement](declare-statement.md)  
  
 在下面的示例中， `Alias` 关键字用于提供 advapi32.dll 中的函数的名称， `GetUserNameA` `getUserName` 此名称用于替代本示例中的。 `getUserName`在 sub 中调用函数 `getUser` ，该函数显示当前用户的名称。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另请参阅

- [关键字](../keywords/index.md)
