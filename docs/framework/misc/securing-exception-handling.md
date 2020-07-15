---
title: 保护异常处理
description: 请参阅如何在 .NET 代码中确保异常处理的安全。 如果有 try、except、catch 和 finally 语句，请查看代码的运行顺序。
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: 73597f83d7236cd48a18a891c987b4f5d7e1723d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309035"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="2131b-104">保护异常处理</span><span class="sxs-lookup"><span data-stu-id="2131b-104">Securing Exception Handling</span></span>
<span data-ttu-id="2131b-105">在 Visual C++ 和 Visual Basic 中，堆栈中的一个筛选器表达式将在任何语句之前运行 `finally` 。</span><span class="sxs-lookup"><span data-stu-id="2131b-105">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any `finally` statement.</span></span> <span data-ttu-id="2131b-106">与该筛选器相关联的**catch**块在 `finally` 语句之后运行。</span><span class="sxs-lookup"><span data-stu-id="2131b-106">The **catch** block associated with that filter runs after the `finally` statement.</span></span> <span data-ttu-id="2131b-107">有关详细信息，请参阅[使用用户筛选的异常](../../standard/exceptions/using-user-filtered-exception-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="2131b-107">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="2131b-108">本部分将介绍此顺序的安全隐患。</span><span class="sxs-lookup"><span data-stu-id="2131b-108">This section examines the security implications of this order.</span></span> <span data-ttu-id="2131b-109">请考虑以下伪代码示例，其中阐释了筛选语句和 `finally` 语句的运行顺序。</span><span class="sxs-lookup"><span data-stu-id="2131b-109">Consider the following pseudocode example that illustrates the order in which filter statements and `finally` statements run.</span></span>  
  
```cpp  
void Main()
{  
    try
    {  
        Sub();  
    }
    except (Filter())
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()
{  
    try
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }
    finally
    {  
        Console.WriteLine("finally");  
    }  
}
```  
  
 <span data-ttu-id="2131b-110">此代码将打印以下代码。</span><span class="sxs-lookup"><span data-stu-id="2131b-110">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="2131b-111">筛选器在语句之前运行 `finally` ，因此，在执行其他代码的情况下，任何更改状态的内容都可以引入安全问题。</span><span class="sxs-lookup"><span data-stu-id="2131b-111">The filter runs before the `finally` statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="2131b-112">例如：</span><span class="sxs-lookup"><span data-stu-id="2131b-112">For example:</span></span>  
  
```cpp  
try
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and
    // so on) that could be exploited if malicious
    // code ran before state is restored.  
    Do_some_work();  
}
finally
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 <span data-ttu-id="2131b-113">此伪代码允许堆栈上较高的筛选器运行任意代码。</span><span class="sxs-lookup"><span data-stu-id="2131b-113">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="2131b-114">具有类似效果的其他操作示例是对其他标识的临时模拟、设置跳过某些安全检查的内部标志或更改与线程关联的区域性。</span><span class="sxs-lookup"><span data-stu-id="2131b-114">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="2131b-115">建议的解决方案是引入异常处理程序，以将代码的更改从调用方的筛选器块隔离到线程状态。</span><span class="sxs-lookup"><span data-stu-id="2131b-115">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="2131b-116">但是，正确地引入异常处理程序或不解决此问题很重要。</span><span class="sxs-lookup"><span data-stu-id="2131b-116">However, it's important to properly introduce the exception handler or this problem won't be fixed.</span></span> <span data-ttu-id="2131b-117">下面的示例将切换 UI 区域性，但任何类型的线程状态更改都可能会以同样的方式公开。</span><span class="sxs-lookup"><span data-stu-id="2131b-117">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 <span data-ttu-id="2131b-118">在这种情况下，正确的修复方法是**try** / 在**try**catch 块中包装现有 try**finally**块 / **catch** 。</span><span class="sxs-lookup"><span data-stu-id="2131b-118">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="2131b-119">只需将**catch throw**子句引入现有**try** / **finally**块中，就不能解决问题，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="2131b-119">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 <span data-ttu-id="2131b-120">这不会解决此问题，因为在 `finally` 获取控件之前语句尚未运行 `FilterFunc` 。</span><span class="sxs-lookup"><span data-stu-id="2131b-120">This does not fix the problem because the `finally` statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="2131b-121">下面的示例通过确保在将 `finally` 异常提供给调用方的异常筛选器块之前执行了子句来修复此问题。</span><span class="sxs-lookup"><span data-stu-id="2131b-121">The following example fixes the problem by ensuring that the `finally` clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try
    {  
        try
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2131b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2131b-122">See also</span></span>

- [<span data-ttu-id="2131b-123">代码安全维护指南</span><span class="sxs-lookup"><span data-stu-id="2131b-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
