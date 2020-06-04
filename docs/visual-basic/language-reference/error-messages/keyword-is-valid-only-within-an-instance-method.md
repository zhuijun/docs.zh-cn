---
title: “<keyword>”只在实例方法中有效
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397397"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>“\<keyword>”只在实例方法中有效
`Me`、 `MyClass` 和 `MyBase` 关键字引用特定的类实例。 不能在共享或过程中使用它们 `Function` `Sub` 。  
  
 **错误 ID：** BC30043  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 从过程中删除关键字，或 `Shared` 从过程声明中删除关键字。  
  
## <a name="see-also"></a>另请参阅

- [对象变量赋值](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承基础知识](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
