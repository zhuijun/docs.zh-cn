---
title: 如何实现自定义事件访问器 - C# 编程指南
description: 了解如何实现自定义事件访问器。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4094aa1fedbceb68790b484608b3ea0ebc1e5cf6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302134"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>如何实现自定义事件访问器（C# 编程指南）
事件是一种特殊的多播委托，只能从声明它的类中进行调用。 客户端代码通过提供对应在引发事件时调用的方法的引用来订阅事件。 这些方法通过事件访问器添加到委托的调用列表中，事件访问器类似于属性访问器，不同之处在于事件访问器命名为 `add` 和 `remove`。 在大多数情况下，无需提供自定义事件访问器。 如果代码中没有提供自定义事件访问器，编译器将自动添加它们。 但在某些情况下，可能需要提供自定义行为。 主题[如何实现接口事件](./how-to-implement-interface-events.md)中介绍了这样一种情况。
  
## <a name="example"></a>示例  
 下面的示例演示如何实现自定义的 add 和 remove 事件访问器。 虽然可以替换访问器内的任何代码，但建议先锁定事件，再添加或删除新的事件处理程序方法。  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>请参阅

- [事件](./index.md)
- [event](../../language-reference/keywords/event.md)
