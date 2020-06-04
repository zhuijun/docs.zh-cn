---
title: 在符合 CLS 的接口中不允许出现不符合 CLS 的 <membername>
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409395"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>在符合 CLS 的接口中不允许出现不符合 CLS 的 \<membername>
接口中的属性、过程或事件被标记为 `<CLSCompliant(True)>` 当接口本身标记为 `<CLSCompliant(False)>` 或未标记时。  
  
 为了使接口符合[语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md)（CLS），其所有成员都必须符合。  
  
 当将 <xref:System.CLSCompliantAttribute> 应用到编程元素中时，需要将该特性的 `isCompliant` 参数设置为 `True` 或 `False` 来指示符合或不符合性。 此参数没有默认值，必须为其提供一个值。  
  
 如果不将 <xref:System.CLSCompliantAttribute> 应用到元素，则它将被视为不符合规范。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID：** BC40033  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 如果你需要 CLS 符合性并且可以控制接口源代码，请将接口标记为 `<CLSCompliant(True)>` 符合其所有成员的条件。  
  
- 如果你需要 CLS 符合性并且无法控制接口源代码，或者不符合要求，请在不同的接口中定义此成员。  
  
- 如果要求此成员保留在其当前接口内，请 <xref:System.CLSCompliantAttribute> 从其定义中删除或将其标记为 `<CLSCompliant(False)>` 。  
  
## <a name="see-also"></a>另请参阅

- [Interface 语句](../statements/interface-statement.md)
