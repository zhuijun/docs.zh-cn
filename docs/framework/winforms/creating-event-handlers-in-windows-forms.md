---
title: 创建事件处理程序
description: 了解如何将 Windows 窗体中的事件分配给多个处理程序，以及如何动态更改处理特定事件的方法。
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 4dca198be69c200ea8dfc741a43801bf8f631b9d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326010"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="3f7d6-103">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="3f7d6-103">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="3f7d6-104">事件处理程序是代码中的过程，用于确定事件（例如用户单击按钮或消息队列收到消息）发生时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-104">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="3f7d6-105">引发事件时，将执行收到该事件的一个或多个事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-105">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="3f7d6-106">可以将事件分配给多个处理程序，并且可以动态更改处理特定事件的方法。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-106">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="3f7d6-107">你还可以使用 Visual Studio 中的 Windows 窗体设计器来创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-107">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3f7d6-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="3f7d6-108">In This Section</span></span>

 <span data-ttu-id="3f7d6-109">[事件概述](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-109">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="3f7d6-110">解释事件模型和委托的角色。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-110">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="3f7d6-111">[事件处理程序概述](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-111">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="3f7d6-112">描述如何处理事件。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-112">Describes how to handle events.</span></span>

 <span data-ttu-id="3f7d6-113">[如何：在运行时为 Windows 窗体创建事件处理程序](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-113">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="3f7d6-114">提供有关如何动态响应系统或用户事件的指令。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-114">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="3f7d6-115">[如何：在 Windows 窗体中将多个事件连接到单个事件处理程序](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-115">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="3f7d6-116">提供有关通过事件将同一功能分配给多个控件的指令。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-116">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="3f7d6-117">[事件在 Windows 窗体中的顺序](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-117">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="3f7d6-118">描述在 Windows 窗体控件中引发事件的顺序。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-118">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="3f7d6-119">[如何：使用设计器创建事件处理程序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))介绍如何使用 Windows 窗体设计器来创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-119">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3f7d6-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="3f7d6-120">Related Sections</span></span>

 <span data-ttu-id="3f7d6-121">[事件](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-121">[Events](../../standard/events/index.md)</span></span>\
 <span data-ttu-id="3f7d6-122">提供有关使用 .NET Framework 处理和引发事件的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-122">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="3f7d6-123">[Visual Basic 中继承的事件处理程序疑难解答](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="3f7d6-123">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="3f7d6-124">列出了继承的组件中的事件处理程序所发生的常见问题。</span><span class="sxs-lookup"><span data-stu-id="3f7d6-124">Lists common issues that occur with event handlers in inherited components.</span></span>
