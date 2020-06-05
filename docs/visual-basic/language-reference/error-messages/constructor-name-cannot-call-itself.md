---
title: 构造函数“<name>”不能调用自身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409798"
---
# <a name="constructor-name-cannot-call-itself"></a>构造函数“\<name>”不能调用自身
`Sub New`类或结构中的过程调用自身。  
  
 构造函数的目的是在第一次创建类或结构时初始化该类或结构的实例。 类或结构可以有多个构造函数，前提是它们都具有不同的参数列表。 除了自身之外，还允许构造函数调用另一个构造函数来执行其功能。 但构造函数调用自身是毫无意义的，事实上，如果允许，它会导致无限递归。  
  
 **错误 ID：** BC30298  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 检查正在被调用的构造函数的参数列表。 它应不同于发出调用的构造函数的。  
  
2. 如果不打算调用另一个构造函数，请完全删除该 `Sub New` 调用。  
  
## <a name="see-also"></a>另请参阅

- [对象生存期：如何创建和销毁对象](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
