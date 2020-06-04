---
title: 名称 <membername> 不符合 CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 45c9332237dffc7311daeedaf36035d9e9958415
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397176"
---
# <a name="name-membername-is-not-cls-compliant"></a>名称 \<membername> 不符合 CLS
程序集标记为， `<CLSCompliant(True)>` 但公开名称以下划线（）开头的成员 `_` 。  
  
 编程元素可以包含一个或多个下划线，但要符合[语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md)（CLS），它不能以下划线开头。 请参阅 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 当将 <xref:System.CLSCompliantAttribute> 应用到编程元素中时，需要将该特性的 `isCompliant` 参数设置为 `True` 或 `False` 来指示符合或不符合性。 此参数没有默认值，必须为其提供一个值。  
  
 如果不将 <xref:System.CLSCompliantAttribute> 应用到元素，则它将被视为不符合规范。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID：** BC40031  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 如果你可以控制源代码，请更改成员名称，使其不以下划线开头。  
  
- 如果要求成员名称保持不变，请 <xref:System.CLSCompliantAttribute> 从其定义中删除或将其标记为 `<CLSCompliant(False)>` 。 你仍可以将程序集标记为 `<CLSCompliant(True)>` 。  
  
## <a name="see-also"></a>另请参阅

- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic 命名约定](../../programming-guide/program-structure/naming-conventions.md)
