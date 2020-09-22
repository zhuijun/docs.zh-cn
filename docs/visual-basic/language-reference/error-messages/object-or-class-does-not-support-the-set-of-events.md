---
title: 对象或类不支持事件集
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873648"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>对象或类不支持事件集

您尝试使用的 `WithEvents` 变量的组件无法作为指定事件集的事件源。 例如，你想要接收对象的事件，然后创建第一个对象的另一个对象 `Implements` 。 尽管你可能会认为可以从实现的对象接收事件，但并不总是这样。 `Implements` 仅实现方法和属性的接口。 `WithEvents` 不支持私有 `UserControls` ，因为引发的类型信息 `ObjectEvent` 在运行时不可用。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 不能接收不是源事件的组件的事件。  
  
## <a name="see-also"></a>另请参阅

- [WithEvents](../modifiers/withevents.md)
- [Implements 语句](../statements/implements-statement.md)
