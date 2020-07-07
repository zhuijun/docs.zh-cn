---
title: 复制和锁定
description: 查看互操作封送拆收器可以如何复制或锁定正在封送的数据。 复制数据会将数据副本从一个内存位置放到另一个位置。
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
ms.openlocfilehash: b7931813cd5254375eda81515f388c85c78fa284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618774"
---
# <a name="copying-and-pinning"></a><span data-ttu-id="d5ac1-104">复制和锁定</span><span class="sxs-lookup"><span data-stu-id="d5ac1-104">Copying and Pinning</span></span>

<span data-ttu-id="d5ac1-105">封送数据时，互操作封送拆收器可以复制或锁定正在封送的数据。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-105">When marshaling data, the interop marshaler can copy or pin the data being marshaled.</span></span> <span data-ttu-id="d5ac1-106">复制数据会将数据副本放置从一个内存位置放到另一个内存位置。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-106">Copying the data places a copy of data from one memory location in another memory location.</span></span> <span data-ttu-id="d5ac1-107">下图显示从托管内存向非托管内存复制值类型和复制按引用传递的类型之间的差异。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-107">The following illustration shows the differences between copying a value type and copying a type passed by reference from managed to unmanaged memory.</span></span>

![展示如何复制值和引用类型的图。](./media/copying-and-pinning/interop-marshal-copy.gif)

<span data-ttu-id="d5ac1-109">按值传递的方法参数作为堆栈上的值封送到非托管代码。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-109">Method arguments passed by value are marshaled to unmanaged code as values on the stack.</span></span> <span data-ttu-id="d5ac1-110">直接进行复制。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-110">The copying process is direct.</span></span> <span data-ttu-id="d5ac1-111">按引用传递的参数作为堆栈上的指针传递。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-111">Arguments passed by reference are passed as pointers on the stack.</span></span> <span data-ttu-id="d5ac1-112">引用类型也按值和按引用传递。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-112">Reference types are also passed by value and by reference.</span></span> <span data-ttu-id="d5ac1-113">如下图所示，按值传递的引用类型被复制或锁定：</span><span class="sxs-lookup"><span data-stu-id="d5ac1-113">As the following illustration shows, reference types passed by value are either copied or pinned:</span></span>

![展示按值和按引用传递的引用类型的图。](./media/copying-and-pinning/interop-marshal-reference-pin.gif)

<span data-ttu-id="d5ac1-115">锁定操作将数据暂时锁定在其当前内存位置，从而阻止公共语言运行时的垃圾回收器将其重定位。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-115">Pinning temporarily locks the data in its current memory location, thus keeping it from being relocated by the common language runtime's garbage collector.</span></span> <span data-ttu-id="d5ac1-116">封送拆收器锁定数据可减小复制的开销并提高性能。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-116">The marshaler pins data to reduce the overhead of copying and enhance performance.</span></span> <span data-ttu-id="d5ac1-117">数据的类型确定在封送处理过程中是复制数据，还是锁定数据。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-117">The type of the data determines whether it is copied or pinned during the marshaling process.</span></span>  <span data-ttu-id="d5ac1-118">在封送 <xref:System.String> 等对象的过程中自动执行锁定操作；然而，也可使用 <xref:System.Runtime.InteropServices.GCHandle> 类手动锁定内存。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-118">Pinning is automatically performed during marshaling for objects such as <xref:System.String>, however you can also manually pin memory using the <xref:System.Runtime.InteropServices.GCHandle> class.</span></span>

## <a name="formatted-blittable-classes"></a><span data-ttu-id="d5ac1-119">已设置格式的 Blittable 类</span><span class="sxs-lookup"><span data-stu-id="d5ac1-119">Formatted Blittable Classes</span></span>

<span data-ttu-id="d5ac1-120">在托管和非托管内存中，已设置格式的 [blittable](blittable-and-non-blittable-types.md) 类具有固定布局（已设置格式）以及通用数据表示形式。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-120">Formatted [blittable](blittable-and-non-blittable-types.md) classes have fixed layout (formatted) and common data representation in both managed and unmanaged memory.</span></span> <span data-ttu-id="d5ac1-121">当这些类型需要封送处理时，指向堆中对象的指针被直接传递给被调用方。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-121">When these types require marshaling, a pointer to the object in the heap is passed to the callee directly.</span></span> <span data-ttu-id="d5ac1-122">被调用方可以更改该指针所引用的内存位置的内容。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-122">The callee can change the contents of the memory location being referenced by the pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="d5ac1-123">如果参数标记为 Out 或 In/Out，则被调用方可以更改内存内容。相反，当参数设置为作为 In（已设置格式的 blittable 类型的默认值）封送时，被调用方应当避免更改内存内容。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-123">The callee can change the memory contents if the parameter is marked Out or In/Out. In contrast, the callee should avoid changing the contents when the parameter is set to marshal as In, which is the default for formatted blittable types.</span></span> <span data-ttu-id="d5ac1-124">在将同一类导出到类型库并用于进行跨单元调用时，修改 In 对象将产生问题。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-124">Modifying an In object generates problems when the same class is exported to a type library and used to make cross-apartment calls.</span></span>

## <a name="formatted-non-blittable-classes"></a><span data-ttu-id="d5ac1-125">已设置格式的非 Blittable 类</span><span class="sxs-lookup"><span data-stu-id="d5ac1-125">Formatted Non-Blittable Classes</span></span>

<span data-ttu-id="d5ac1-126">在托管和非托管内存中，已设置格式的[ blittable](blittable-and-non-blittable-types.md) 类具有固定布局（已设置格式），但数据表示形式不同。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-126">Formatted [non-blittable](blittable-and-non-blittable-types.md) classes have fixed layout (formatted) but the data representation is different in managed and unmanaged memory.</span></span> <span data-ttu-id="d5ac1-127">在以下情况下，数据可能需要转换：</span><span class="sxs-lookup"><span data-stu-id="d5ac1-127">The data can require transformation under the following conditions:</span></span>

- <span data-ttu-id="d5ac1-128">如果按值封送非 blittable 类，则被调用方接收指向该数据结构副本的指针。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-128">If a non-blittable class is marshaled by value, the callee receives a pointer to a copy of the data structure.</span></span>

- <span data-ttu-id="d5ac1-129">如果按引用封送非 blittable 类，则被调用方接收指向数据结构副本的指针的指针。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-129">If a non-blittable class is marshaled by reference, the callee receives a pointer to a pointer to a copy of the data structure.</span></span>

- <span data-ttu-id="d5ac1-130">如果设置了 <xref:System.Runtime.InteropServices.InAttribute> 属性，则始终通过实例的状态初始化此副本，并在必要时进行封送处理。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-130">If the <xref:System.Runtime.InteropServices.InAttribute> attribute is set, this copy is always initialized with the instance's state, marshaling as necessary.</span></span>

- <span data-ttu-id="d5ac1-131">如果设置了 <xref:System.Runtime.InteropServices.OutAttribute> 属性，则始终在返回时将状态复制回实例，并在必要时进行封送处理。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-131">If the <xref:System.Runtime.InteropServices.OutAttribute> attribute is set, the state is always copied back to the instance on return, marshaling as necessary.</span></span>

- <span data-ttu-id="d5ac1-132">如果同时设置了 InAttribute 和 OutAttribute，则两个副本都需要 。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-132">If both **InAttribute** and **OutAttribute** are set, both copies are required.</span></span> <span data-ttu-id="d5ac1-133">如果省略了其中任一个属性，则封送拆收器可以通过删掉其中一个副本进行优化。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-133">If either attribute is omitted, the marshaler can optimize by eliminating either copy.</span></span>

## <a name="reference-types"></a><span data-ttu-id="d5ac1-134">引用类型</span><span class="sxs-lookup"><span data-stu-id="d5ac1-134">Reference Types</span></span>

<span data-ttu-id="d5ac1-135">可按值或按引用传递引用类型。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-135">Reference types can be passed by value or by reference.</span></span> <span data-ttu-id="d5ac1-136">按值传递时，在堆栈上传递指向类型的指针。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-136">When they are passed by value, a pointer to the type is passed on the stack.</span></span> <span data-ttu-id="d5ac1-137">按引用传递时，在堆栈上传递指向类型指针的指针。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-137">When passed by reference, a pointer to a pointer to the type is passed on the stack.</span></span>

<span data-ttu-id="d5ac1-138">引用类型具有以下条件性行为：</span><span class="sxs-lookup"><span data-stu-id="d5ac1-138">Reference types have the following conditional behavior:</span></span>

- <span data-ttu-id="d5ac1-139">如果引用类型按值传递且具有非 blittable 类型的成员，则将类型转换两次：</span><span class="sxs-lookup"><span data-stu-id="d5ac1-139">If a reference type is passed by value and it has members of non-blittable types, the types are converted twice:</span></span>

  - <span data-ttu-id="d5ac1-140">参数传递到非托管端时转换一次。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-140">When an argument is passed to the unmanaged side.</span></span>

  - <span data-ttu-id="d5ac1-141">从调用返回时转换一次。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-141">On return from the call.</span></span>

  <span data-ttu-id="d5ac1-142">为避免不必要的复制和转换，将这些类型作为 In 参数封送。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-142">To avoid unnecessarily copying and conversion, these types are marshaled as In parameters.</span></span> <span data-ttu-id="d5ac1-143">若要使调用方能够看见被调用方所做的更改，必须将 InAttribute 和 OutAttribute 属性显式应用于参数 。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-143">You must explicitly apply the **InAttribute** and **OutAttribute** attributes to an argument for the caller to see changes made by the callee.</span></span>

- <span data-ttu-id="d5ac1-144">如果引用类型按值传递且只具有 blittable 类型的成员，则可在封送处理期间将其锁定，且调用方可看见被调用方对类型成员所做的所有更改。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-144">If a reference type is passed by value and it has only members of blittable types, it can be pinned during marshaling and any changes made to the members of the type by the callee are seen by the caller.</span></span> <span data-ttu-id="d5ac1-145">如果需要该行为，请显式应用 InAttribute 和 OutAttribute 。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-145">Apply **InAttribute** and **OutAttribute** explicitly if you want this behavior.</span></span> <span data-ttu-id="d5ac1-146">如果没有这些方向属性，互操作封送拆收器就不会将方向信息导出到类型库（默认情况下作为 In 导出），这会造成 COM 跨单元封送处理方面的问题。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-146">Without these directional attributes, the interop marshaler does not export directional information to the type library (it exports as In, which is the default) and this can cause problems with COM cross-apartment marshaling.</span></span>

- <span data-ttu-id="d5ac1-147">如果引用类型按引用传递，则默认将它作为 In/Out 封送。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-147">If a reference type is passed by reference, it will be marshaled as In/Out by default.</span></span>

## <a name="systemstring-and-systemtextstringbuilder"></a><span data-ttu-id="d5ac1-148">System.String 和 System.Text.StringBuilder</span><span class="sxs-lookup"><span data-stu-id="d5ac1-148">System.String and System.Text.StringBuilder</span></span>

<span data-ttu-id="d5ac1-149">按值或按引用将数据封送到非托管代码时，封送拆收器通常将数据复制到辅助缓冲区（可能在复制期间转换字符集），并将对缓冲区的引用传递给被调用方。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-149">When data is marshaled to unmanaged code by value or by reference, the marshaler typically copies the data to a secondary buffer (possibly converting character sets during the copy) and passes a reference to the buffer to the callee.</span></span> <span data-ttu-id="d5ac1-150">除非引用是用 SysAllocString 分配的 BSTR，否则将始终用 CoTaskMemAlloc 分配引用  。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-150">Unless the reference is a **BSTR** allocated with **SysAllocString**, the reference is always allocated with **CoTaskMemAlloc**.</span></span>

<span data-ttu-id="d5ac1-151">作为其中一个字符串类型按值（如 Unicode 字符串）封送时的一种优化，封送拆收器将指向内部 Unicode 缓冲区中托管字符串的直接指针传递给被调用方，而不是将其复制到新缓冲区。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-151">As an optimization when either string type is marshaled by value (such as a Unicode character string), the marshaler passes the callee a direct pointer to managed strings in the internal Unicode buffer instead of copying it to a new buffer.</span></span>

> [!CAUTION]
> <span data-ttu-id="d5ac1-152">按值传递字符串时，被调用方绝不能改变封送拆收器传递的引用。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-152">When a string is passed by value, the callee must never alter the reference passed by the marshaler.</span></span> <span data-ttu-id="d5ac1-153">这样做会损坏托管堆。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-153">Doing so can corrupt the managed heap.</span></span>

<span data-ttu-id="d5ac1-154">按引用传递 <xref:System.String?displayProperty=nameWithType> 时，封送拆收器将字符串内容复制到辅助缓冲区，再进行调用。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-154">When a <xref:System.String?displayProperty=nameWithType> is passed by reference, the marshaler copies the contents the string to a secondary buffer before making the call.</span></span> <span data-ttu-id="d5ac1-155">在从调用返回时，再将该缓冲区内容复制到新字符串中。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-155">It then copies the contents of the buffer into a new string on return from the call.</span></span> <span data-ttu-id="d5ac1-156">这种技术确保不可变托管字符串保持不变。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-156">This technique ensures that the immutable managed string remains unaltered.</span></span>

<span data-ttu-id="d5ac1-157">按值传递 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 时，封送拆收器将对 StringBuilder 的内部缓冲区的引用直接传递给调用方。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-157">When a <xref:System.Text.StringBuilder?displayProperty=nameWithType> is passed by value, the marshaler passes a reference to the internal buffer of the **StringBuilder** directly to the caller.</span></span> <span data-ttu-id="d5ac1-158">调用方和被调用方必须就缓冲区大小达成一致。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-158">The caller and callee must agree on the size of the buffer.</span></span> <span data-ttu-id="d5ac1-159">调用方负责创建具有足够长度的 StringBuilder。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-159">The caller is responsible for creating a **StringBuilder** of adequate length.</span></span> <span data-ttu-id="d5ac1-160">被调用方必须采取必要措施确保不溢出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-160">The callee must take the necessary precautions to ensure that the buffer is not overrun.</span></span> <span data-ttu-id="d5ac1-161">对于默认将按值传递的引用类型作为 In 参数传递的规则，StringBuilder 是一个例外。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-161">**StringBuilder** is an exception to the rule that reference types passed by value are passed as In parameters by default.</span></span> <span data-ttu-id="d5ac1-162">它始终作为 In/Out 传递。</span><span class="sxs-lookup"><span data-stu-id="d5ac1-162">It is always passed as In/Out.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ac1-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="d5ac1-163">See also</span></span>

- [<span data-ttu-id="d5ac1-164">默认封送处理行为</span><span class="sxs-lookup"><span data-stu-id="d5ac1-164">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- <span data-ttu-id="d5ac1-165">[方向特性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d5ac1-165">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="d5ac1-166">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="d5ac1-166">Interop Marshaling</span></span>](interop-marshaling.md)
