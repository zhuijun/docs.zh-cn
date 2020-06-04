---
title: 程序集
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373155"
---
# <a name="assembly-visual-basic"></a>程序集 (Visual Basic)
指定源文件开头的属性应用于整个程序集。  
  
## <a name="remarks"></a>备注  
 许多属性都属于单个编程元素，如类或属性。 您可以通过将特性块附加到尖括号（）中，将此类特性 `< >` 直接附加到声明语句。  
  
 如果某个特性不仅与以下元素有关，而不属于整个程序集，则可以将特性块放在源文件的开头，并使用关键字标识该特性 `Assembly` 。 如果它适用于当前程序集模块，则使用[module](module-keyword.md)关键字。  
  
 你还可以在 AssemblyInfo 文件中将属性应用于程序集，在这种情况下，你不必在主源代码文件中使用属性块。  
  
## <a name="see-also"></a>另请参阅

- [模块\<keyword>](module-keyword.md)
- [属性概述](../../programming-guide/concepts/attributes/index.md)
