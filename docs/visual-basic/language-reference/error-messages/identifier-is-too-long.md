---
title: 标识符太长
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: 084e3d9306ad84d7e6e36e5fe4bbfc868b8dfac6
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873998"
---
# <a name="identifier-is-too-long"></a>标识符太长

每个编程元素的名称或标识符限制为1023个字符。 此外，完全限定的名称不能超过1023个字符。 这意味着 () 的整个标识符字符串的 `<namespace>.<...>.<namespace>.<class>.<element>` 长度不能超过1023个字符，包括成员访问运算符 (`.`) 字符。  
  
 **错误 ID：** BC30033  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 减小标识符的长度。  
  
## <a name="see-also"></a>另请参阅

- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
