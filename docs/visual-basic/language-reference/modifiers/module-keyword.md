---
title: 模块<keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 0cb009c22dada7b92956e113d33505923a92f2b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362419"
---
# <a name="module-keyword-visual-basic"></a>Module \<keyword> (Visual Basic)
指定源文件开头的属性应用于当前程序集模块。  
  
## <a name="remarks"></a>备注  
 许多属性都属于单个编程元素，如类或属性。 您可以通过将特性块附加到尖括号（）中，将此类特性 `< >` 直接附加到声明语句。  
  
 如果特性不仅与以下元素有关，而与当前程序集模块有关，请将特性块放在源文件的开头，并使用关键字标识特性 `Module` 。 如果它适用于整个程序集，则可以使用[assembly](assembly.md)关键字。  
  
 `Module`修饰符与[Module 语句](../statements/module-statement.md)不同。  
  
## <a name="see-also"></a>另请参阅

- [程序集](assembly.md)
- [Module 语句](../statements/module-statement.md)
- [属性概述](../../programming-guide/concepts/attributes/index.md)
