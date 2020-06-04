---
title: 共享 WithEvents 变量的事件不能由非共享方法处理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409564"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共享 WithEvents 变量的事件不能由非共享方法处理
使用修饰符声明的变量 `Shared` 是共享变量。 共享变量精确标识一个存储位置。 使用修饰符声明的变量 `WithEvents` 断言变量所属的类型将处理变量引发的事件集。 将值分配给变量时，由声明创建的属性将 `WithEvents` 卸载任何现有的事件处理程序，并通过方法挂钩新的事件处理程序 `Add` 。  
  
 **错误 ID：** BC30594  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 声明事件处理程序 `Shared` 。  
  
## <a name="see-also"></a>另请参阅

- [共享](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
