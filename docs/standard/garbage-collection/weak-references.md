---
title: 弱引用
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
ms.openlocfilehash: 4b7e7a62b92b2c685ff39baa75f4bc33602b5da2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287579"
---
# <a name="weak-references"></a><span data-ttu-id="e614e-102">弱引用</span><span class="sxs-lookup"><span data-stu-id="e614e-102">Weak References</span></span>
<span data-ttu-id="e614e-103">如果应用程序的代码可以访问一个正由该程序使用的对象，垃圾回收器就不能回收该对象，</span><span class="sxs-lookup"><span data-stu-id="e614e-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="e614e-104">那么，就认为应用程序对该对象具有强引用。</span><span class="sxs-lookup"><span data-stu-id="e614e-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="e614e-105">弱引用允许应用程序访问对象，同时也允许垃圾回收器收集相应的对象。</span><span class="sxs-lookup"><span data-stu-id="e614e-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="e614e-106">如果不存在强引用，则弱引用的有限期只限于收集对象前的一个不确定的时间段。</span><span class="sxs-lookup"><span data-stu-id="e614e-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="e614e-107">使用弱引用时，应用程序仍可对该对象进行强引用，这样做可防止该对象被收集。</span><span class="sxs-lookup"><span data-stu-id="e614e-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="e614e-108">但始终存在这样的风险：垃圾回收器在重新建立强引用之前先处理该对象。</span><span class="sxs-lookup"><span data-stu-id="e614e-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="e614e-109">占用大量内存，但通过垃圾回收功能回收以后很容易重新创建的对象特别适合使用弱引用。</span><span class="sxs-lookup"><span data-stu-id="e614e-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="e614e-110">假设 Windows 窗体应用中的树状视图向用户显示层次结构复杂的选项。</span><span class="sxs-lookup"><span data-stu-id="e614e-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="e614e-111">如果基础数据量很大，则用户使用应用程序中的其他部分时，在内存中保留该树会导致效率低下。</span><span class="sxs-lookup"><span data-stu-id="e614e-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="e614e-112">当用户切换到应用的其他部分时，可以使用 <xref:System.WeakReference> 类创建对树的弱引用，并销毁所有强引用。</span><span class="sxs-lookup"><span data-stu-id="e614e-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="e614e-113">当用户切换回该树时，应用程序会尝试获得对该树的强引用，如果成功，就不必重新构造该树。</span><span class="sxs-lookup"><span data-stu-id="e614e-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="e614e-114">若要对某对象建立弱引用，请使用要跟踪的对象实例创建 <xref:System.WeakReference>。</span><span class="sxs-lookup"><span data-stu-id="e614e-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="e614e-115">然后将 <xref:System.WeakReference.Target%2A> 属性设置为该对象，将该对象的原始引用设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="e614e-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="e614e-116">有关代码示例，请参阅类库中的 <xref:System.WeakReference>。</span><span class="sxs-lookup"><span data-stu-id="e614e-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="e614e-117">短弱引用和长弱引用</span><span class="sxs-lookup"><span data-stu-id="e614e-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="e614e-118">可以创建短弱引用或长弱引用：</span><span class="sxs-lookup"><span data-stu-id="e614e-118">You can create a short weak reference or a long weak reference:</span></span>  
  
- <span data-ttu-id="e614e-119">Short</span><span class="sxs-lookup"><span data-stu-id="e614e-119">Short</span></span>  
  
     <span data-ttu-id="e614e-120">垃圾回收功能回收对象后，短弱引用的目标会变为 `null`。</span><span class="sxs-lookup"><span data-stu-id="e614e-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="e614e-121">弱引用本身是托管对象，与其他任何托管对象一样需要经过垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="e614e-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="e614e-122">短弱引用是 <xref:System.WeakReference> 的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="e614e-122">A short weak reference is the parameterless constructor for <xref:System.WeakReference>.</span></span>  
  
- <span data-ttu-id="e614e-123">Long</span><span class="sxs-lookup"><span data-stu-id="e614e-123">Long</span></span>  
  
     <span data-ttu-id="e614e-124">在对象的 <xref:System.Object.Finalize%2A> 方法已调用后，长弱引用获得保留。</span><span class="sxs-lookup"><span data-stu-id="e614e-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="e614e-125">这样，便可以重新创建该对象，但该对象仍保持不可预知的状态。</span><span class="sxs-lookup"><span data-stu-id="e614e-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="e614e-126">若要使用长引用，请在 <xref:System.WeakReference> 构造函数中指定 `true`。</span><span class="sxs-lookup"><span data-stu-id="e614e-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="e614e-127">如果对象类型不包含 <xref:System.Object.Finalize%2A> 方法，应用的是短弱引用功能。弱引用只在目标被收集前有效，运行终结器后可以随时收集目标。</span><span class="sxs-lookup"><span data-stu-id="e614e-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="e614e-128">若要建立强引用并重新使用对象，请将 <xref:System.WeakReference> 的 <xref:System.WeakReference.Target%2A> 属性强制转换为对象类型。</span><span class="sxs-lookup"><span data-stu-id="e614e-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="e614e-129">如果 <xref:System.WeakReference.Target%2A> 属性返回 `null`，表示对象已被收集；否则，可继续使用对象，因为应用已重新获得对它的强引用。</span><span class="sxs-lookup"><span data-stu-id="e614e-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="e614e-130">使用弱引用的准则</span><span class="sxs-lookup"><span data-stu-id="e614e-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="e614e-131">仅在必要时使用长弱引用，因为在终结后对象的状态不可预知。</span><span class="sxs-lookup"><span data-stu-id="e614e-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="e614e-132">避免对小对象使用弱引用，因为指针本身可能和对象一样大，或者比对象还大。</span><span class="sxs-lookup"><span data-stu-id="e614e-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="e614e-133">避免将弱引用作为内存管理问题的自动解决方案，</span><span class="sxs-lookup"><span data-stu-id="e614e-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="e614e-134">而应开发一个有效的缓存策略来处理应用程序的对象。</span><span class="sxs-lookup"><span data-stu-id="e614e-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e614e-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e614e-135">See also</span></span>

- [<span data-ttu-id="e614e-136">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="e614e-136">Garbage Collection</span></span>](index.md)
