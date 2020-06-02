---
title: 安全和争用条件
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 715bf240a5f7f44ba3f914ad6788631074aa41b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291014"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="f51c4-102">安全和争用条件</span><span class="sxs-lookup"><span data-stu-id="f51c4-102">Security and Race Conditions</span></span>
<span data-ttu-id="f51c4-103">还有一个需要注意的问题是争用情况可能会导致安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="f51c4-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="f51c4-104">可以通过多种方式来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f51c4-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="f51c4-105">以下子主题概述了开发人员必须避免的一些主要缺陷。</span><span class="sxs-lookup"><span data-stu-id="f51c4-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="f51c4-106">Dispose 方法中的争用条件</span><span class="sxs-lookup"><span data-stu-id="f51c4-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="f51c4-107">如果类的**Dispose**方法（有关详细信息，请参阅[垃圾回收](../garbage-collection/index.md)）未同步，则可能会多次运行**Dispose**中的清理代码，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f51c4-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="f51c4-108">由于此**Dispose**实现不同步，因此可以 `Cleanup` 通过前一个线程调用，然后在 `_myObj` 设置为**null**之前调用另一个线程。</span><span class="sxs-lookup"><span data-stu-id="f51c4-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="f51c4-109">这是否是一个安全问题取决于代码运行时发生的情况 `Cleanup` 。</span><span class="sxs-lookup"><span data-stu-id="f51c4-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="f51c4-110">不同步**Dispose**实现的主要问题涉及使用资源句柄（如文件）。</span><span class="sxs-lookup"><span data-stu-id="f51c4-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="f51c4-111">不当处置可能会导致使用错误的句柄，这通常会导致安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="f51c4-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="f51c4-112">构造函数中的争用条件</span><span class="sxs-lookup"><span data-stu-id="f51c4-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="f51c4-113">在某些应用程序中，其他线程可能在其类构造函数完全运行之前访问类成员。</span><span class="sxs-lookup"><span data-stu-id="f51c4-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="f51c4-114">应查看所有类构造函数，以确保在发生这种情况时不会出现安全问题，如有必要，还应同步线程。</span><span class="sxs-lookup"><span data-stu-id="f51c4-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="f51c4-115">带有缓存对象的争用条件</span><span class="sxs-lookup"><span data-stu-id="f51c4-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="f51c4-116">如果类的其他部分未进行适当同步，则缓存安全信息或使用代码访问安全[断言](../../framework/misc/using-the-assert-method.md)操作的代码也可能易受到争用条件的影响，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f51c4-116">Code that caches security information or uses the code access security [Assert](../../framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="f51c4-117">如果有其他路径 `DoOtherWork` 可以从具有相同对象的另一个线程调用，则不受信任的调用方可以按需求。</span><span class="sxs-lookup"><span data-stu-id="f51c4-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="f51c4-118">如果你的代码缓存安全信息，请确保查看此漏洞。</span><span class="sxs-lookup"><span data-stu-id="f51c4-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="f51c4-119">终结器中的争用条件</span><span class="sxs-lookup"><span data-stu-id="f51c4-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="f51c4-120">争用条件也可能出现在引用静态或非托管资源的对象中，该对象随后会在其终结器中释放。</span><span class="sxs-lookup"><span data-stu-id="f51c4-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="f51c4-121">如果多个对象共享在类的终结器中操作的资源，则这些对象必须同步对该资源的所有访问。</span><span class="sxs-lookup"><span data-stu-id="f51c4-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51c4-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f51c4-122">See also</span></span>

- [<span data-ttu-id="f51c4-123">代码安全维护指南</span><span class="sxs-lookup"><span data-stu-id="f51c4-123">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
