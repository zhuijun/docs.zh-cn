---
title: 如何在派生类中引发基类事件 - C# 编程指南
description: 了解如何在派生类中引发基类事件。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 5456639052310cc64854e32caa1df9b391c042cb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558017"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="691d4-104">如何在派生类中引发基类事件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="691d4-104">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="691d4-105">下面的简单示例演示用于在基类中声明事件，以便也可以从派生类引发它们的标准方法。</span><span class="sxs-lookup"><span data-stu-id="691d4-105">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="691d4-106">此模式广泛用于 .NET 类库中的 Windows 窗体类。</span><span class="sxs-lookup"><span data-stu-id="691d4-106">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="691d4-107">创建可以用作其他类的基类的类时，应考虑到以下事实：事件是特殊类型的委托，只能从声明它们的类中进行调用。</span><span class="sxs-lookup"><span data-stu-id="691d4-107">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="691d4-108">派生类不能直接调用在基类中声明的事件。</span><span class="sxs-lookup"><span data-stu-id="691d4-108">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="691d4-109">虽然有时可能需要只能由基类引发的事件，不过在大多数情况下，应使派生类可以调用基类事件。</span><span class="sxs-lookup"><span data-stu-id="691d4-109">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="691d4-110">为此，可以在包装事件的基类中创建受保护的调用方法。</span><span class="sxs-lookup"><span data-stu-id="691d4-110">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="691d4-111">通过调用或重写此调用方法，派生类可以间接调用事件。</span><span class="sxs-lookup"><span data-stu-id="691d4-111">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="691d4-112">不要在基类中声明虚拟事件并在派生类中重写它们。</span><span class="sxs-lookup"><span data-stu-id="691d4-112">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="691d4-113">C# 编译器不会处理这些事件，并且无法预知派生事件的订阅者是否实际上会订阅基类事件。</span><span class="sxs-lookup"><span data-stu-id="691d4-113">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="691d4-114">示例</span><span class="sxs-lookup"><span data-stu-id="691d4-114">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="691d4-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="691d4-115">See also</span></span>

- [<span data-ttu-id="691d4-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="691d4-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="691d4-117">事件</span><span class="sxs-lookup"><span data-stu-id="691d4-117">Events</span></span>](./index.md)
- [<span data-ttu-id="691d4-118">委托</span><span class="sxs-lookup"><span data-stu-id="691d4-118">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="691d4-119">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="691d4-119">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="691d4-120">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="691d4-120">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
