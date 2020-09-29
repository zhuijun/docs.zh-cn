---
title: 使用委托中的变体 (C#)
description: 了解如何使用包含的协变和逆变代码示例在委托中使用变体。
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 6704c3bf09dd854335f1e2719ccc8462cb7cde26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176313"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="80824-103">使用委托中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="80824-103">Using Variance in Delegates (C#)</span></span>

<span data-ttu-id="80824-104">向委托分配方法时，协变和逆变为匹配委托类型和方法签名提供了灵活性。</span><span class="sxs-lookup"><span data-stu-id="80824-104">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="80824-105">协变允许方法具有的派生返回类型多于委托中定义的类型。</span><span class="sxs-lookup"><span data-stu-id="80824-105">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="80824-106">逆变允许方法具有的派生参数类型少于委托类型中的类型。</span><span class="sxs-lookup"><span data-stu-id="80824-106">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="80824-107">示例 1：协变</span><span class="sxs-lookup"><span data-stu-id="80824-107">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="80824-108">描述</span><span class="sxs-lookup"><span data-stu-id="80824-108">Description</span></span>  

 <span data-ttu-id="80824-109">本示例演示如何将委托与具有返回类型的方法一起使用，这些返回类型派生自委托签名中的返回类型。</span><span class="sxs-lookup"><span data-stu-id="80824-109">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="80824-110">`DogsHandler` 返回的数据类型属于 `Dogs` 类型，它派生自委托中定义的 `Mammals` 类型。</span><span class="sxs-lookup"><span data-stu-id="80824-110">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="80824-111">代码</span><span class="sxs-lookup"><span data-stu-id="80824-111">Code</span></span>  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="80824-112">示例 2：逆变</span><span class="sxs-lookup"><span data-stu-id="80824-112">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="80824-113">描述</span><span class="sxs-lookup"><span data-stu-id="80824-113">Description</span></span>

<span data-ttu-id="80824-114">本示例演示如何将委托与具有参数的方法一起使用，这些参数的类型是委托签名参数类型的基类型。</span><span class="sxs-lookup"><span data-stu-id="80824-114">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="80824-115">通过逆变可以使用一个事件处理程序而不是多个单独的处理程序。</span><span class="sxs-lookup"><span data-stu-id="80824-115">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="80824-116">下面的示例使用两个委托：</span><span class="sxs-lookup"><span data-stu-id="80824-116">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="80824-117">定义 [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) 事件签名的 <xref:System.Windows.Forms.KeyEventHandler> 委托。</span><span class="sxs-lookup"><span data-stu-id="80824-117">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="80824-118">其签名为：</span><span class="sxs-lookup"><span data-stu-id="80824-118">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="80824-119">定义 [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) 事件签名的 <xref:System.Windows.Forms.MouseEventHandler> 委托。</span><span class="sxs-lookup"><span data-stu-id="80824-119">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="80824-120">其签名为：</span><span class="sxs-lookup"><span data-stu-id="80824-120">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="80824-121">该示例定义了一个具有 <xref:System.EventArgs> 参数的事件处理程序，并使用它来处理 `Button.KeyDown` 和 `Button.MouseClick` 事件。</span><span class="sxs-lookup"><span data-stu-id="80824-121">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="80824-122">它可以这样做是因为 <xref:System.EventArgs> 是 <xref:System.Windows.Forms.KeyEventArgs> 和 <xref:System.Windows.Forms.MouseEventArgs> 的基类型。</span><span class="sxs-lookup"><span data-stu-id="80824-122">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="80824-123">代码</span><span class="sxs-lookup"><span data-stu-id="80824-123">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="80824-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="80824-124">See also</span></span>

- [<span data-ttu-id="80824-125">委托中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="80824-125">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="80824-126">对 Func 和 Action 泛型委托使用变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="80824-126">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
