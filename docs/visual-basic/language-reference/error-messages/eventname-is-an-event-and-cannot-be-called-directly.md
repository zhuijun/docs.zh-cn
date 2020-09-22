---
title: “<eventname>”是事件，不能直接调用
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 3366bc215a45cd7de9dc2de285758a78144df509
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874313"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>“\<eventname>”是事件，不能直接调用

"<`eventname`>" 是一个事件，因此不能直接调用。 使用 `RaiseEvent` 语句引发事件。  
  
 过程调用指定过程名称的事件。 事件处理程序是一个过程，但事件本身就是信号设备，必须引发并处理。  
  
 **错误 ID：** BC32022  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 使用 `RaiseEvent` 语句对事件发出信号并调用处理该事件的过程。  
  
## <a name="see-also"></a>另请参阅

- [RaiseEvent 语句](../statements/raiseevent-statement.md)
