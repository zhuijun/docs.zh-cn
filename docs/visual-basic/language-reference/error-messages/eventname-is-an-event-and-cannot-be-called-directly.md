---
title: “<eventname>”是事件，不能直接调用
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409590"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>“\<eventname>”是事件，不能直接调用
"<`eventname`>" 是一个事件，因此不能直接调用。 使用 `RaiseEvent` 语句引发事件。  
  
 过程调用指定过程名称的事件。 事件处理程序是一个过程，但事件本身就是信号设备，必须引发并处理。  
  
 **错误 ID：** BC32022  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 使用 `RaiseEvent` 语句对事件发出信号并调用处理该事件的过程。  
  
## <a name="see-also"></a>另请参阅

- [RaiseEvent 语句](../statements/raiseevent-statement.md)
