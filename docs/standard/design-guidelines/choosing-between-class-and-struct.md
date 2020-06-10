---
title: 在类和结构之间选择
description: 了解如何确定是将类型设计为类，还是将类型设计为结构。 了解引用类型和值类型在 .NET 中的不同之处。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
ms.openlocfilehash: 9d757e77292c1226fbe2328cce082033ae8f7003
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662597"
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="e1d0c-104">在类和结构之间选择</span><span class="sxs-lookup"><span data-stu-id="e1d0c-104">Choosing Between Class and Struct</span></span>
<span data-ttu-id="e1d0c-105">每个框架设计器所面临的一项基本设计决策是：将类型设计为类（引用类型）还是结构（值类型）。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-105">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="e1d0c-106">充分了解引用类型和值类型的行为差异对于做出此选择至关重要。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-106">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>

 <span data-ttu-id="e1d0c-107">引用类型和值类型的第一个区别在于，引用类型在堆上分配并进行垃圾回收，而值类型则在堆栈上分配，或在包含类型中以内联方式分配，在堆栈展开或其包含类型释放时释放。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-107">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="e1d0c-108">因此，值类型的分配和释放通常比引用类型的分配和释放更便宜。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-108">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>

 <span data-ttu-id="e1d0c-109">接下来，将对引用类型的数组进行内嵌分配，也就是说，数组元素只是引用驻留在堆上的引用类型的实例。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-109">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="e1d0c-110">值类型数组是以内联方式分配的，这意味着数组元素是值类型的实际实例。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-110">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="e1d0c-111">因此，值类型阵列的分配和释放比引用类型阵列的分配和释放更便宜。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-111">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="e1d0c-112">此外，在大多数情况下，值类型数组表现出更好的引用位置。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-112">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>

 <span data-ttu-id="e1d0c-113">下一个差异与内存使用情况相关。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-113">The next difference is related to memory usage.</span></span> <span data-ttu-id="e1d0c-114">值类型在转换为引用类型或其实现的接口之一时获得装箱。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-114">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="e1d0c-115">它们会在转换回值类型时进行取消装箱。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-115">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="e1d0c-116">因为框是在堆上分配并进行垃圾回收的对象，所以太多装箱和取消装箱会对堆、垃圾回收器和最终性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-116">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="e1d0c-117">与此相反，引用类型不会被强制转换。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-117">In contrast, no such boxing occurs as reference types are cast.</span></span> <span data-ttu-id="e1d0c-118">（有关详细信息，请参阅[装箱和取消装箱](../../csharp/programming-guide/types/boxing-and-unboxing.md)）。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-118">(For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).</span></span>

 <span data-ttu-id="e1d0c-119">接下来，引用类型分配复制引用，而值类型分配则复制整个值。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-119">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="e1d0c-120">因此，大型引用类型的分配比大值类型的分配更便宜。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-120">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>

 <span data-ttu-id="e1d0c-121">最后，引用类型通过引用传递，而值类型通过值传递。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-121">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="e1d0c-122">对引用类型的实例所做的更改将影响指向该实例的所有引用。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-122">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="e1d0c-123">值类型实例在按值传递时复制。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-123">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="e1d0c-124">当值类型的实例发生更改时，它不会影响它的任何副本。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-124">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="e1d0c-125">由于这些副本不是由用户显式创建的，而是在传递参数或返回值时隐式创建的，因此，可以更改的值类型可能会给许多用户造成混淆。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-125">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="e1d0c-126">因此，值类型应是不可变的。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-126">Therefore, value types should be immutable.</span></span>

 <span data-ttu-id="e1d0c-127">作为经验法则，框架中的大部分类型都应为类。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-127">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="e1d0c-128">但在某些情况下，值类型的特征使其更适合使用结构。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-128">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>

 <span data-ttu-id="e1d0c-129">✔️考虑定义结构而不是类的实例，如果该类型的实例较小且通常为短生存期，或者通常嵌入到其他对象中。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-129">✔️ CONSIDER defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>

 <span data-ttu-id="e1d0c-130">❌避免定义结构，除非该类型具有以下所有特性：</span><span class="sxs-lookup"><span data-stu-id="e1d0c-130">❌ AVOID defining a struct unless the type has all of the following characteristics:</span></span>

- <span data-ttu-id="e1d0c-131">它以逻辑方式表示单个值，类似于基元类型（ `int` 、等 `double` ）。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-131">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>

- <span data-ttu-id="e1d0c-132">它的实例大小为16字节。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-132">It has an instance size under 16 bytes.</span></span>

- <span data-ttu-id="e1d0c-133">它是不可变的。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-133">It is immutable.</span></span>

- <span data-ttu-id="e1d0c-134">它不需要频繁装箱。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-134">It will not have to be boxed frequently.</span></span>

 <span data-ttu-id="e1d0c-135">在所有其他情况下，应将类型定义为类。</span><span class="sxs-lookup"><span data-stu-id="e1d0c-135">In all other cases, you should define your types as classes.</span></span>

 <span data-ttu-id="e1d0c-136">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="e1d0c-136">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e1d0c-137">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="e1d0c-137">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e1d0c-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1d0c-138">See also</span></span>

- [<span data-ttu-id="e1d0c-139">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="e1d0c-139">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="e1d0c-140">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="e1d0c-140">Framework Design Guidelines</span></span>](index.md)
