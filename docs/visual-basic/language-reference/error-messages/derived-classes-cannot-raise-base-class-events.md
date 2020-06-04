---
title: 派生类无法引发基类事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409694"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>派生类无法引发基类事件
事件只能从声明它的声明空间引发。 因此，类无法从任何其他类（甚至是从中派生的类）引发事件。  
  
 **错误 ID：** BC30029  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 移动 `Event` 语句或 `RaiseEvent` 语句，使其位于同一个类中。  
  
## <a name="see-also"></a>另请参阅

- [Event 语句](../statements/event-statement.md)
- [RaiseEvent 语句](../statements/raiseevent-statement.md)
