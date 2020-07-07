---
title: 使用非托管 DLL 函数
description: 通过使用平台调用服务来使用非托管 DLL 函数，该服务允许托管代码调用 DLL 库中实现的非托管函数。
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
ms.openlocfilehash: 880cbd4701ae4aee35038f6402b3beb70e60290c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622180"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="69638-103">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="69638-103">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="69638-104">平台调用是一项服务，使托管代码能够调用动态链接库 (DLL) 中实现的非托管函数，例如 Windows API 中的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="69638-104">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="69638-105">此服务定位并调用导出的函数，并根据需要跨交互操作边界封送其自变量（整数、字符串、数组、结构等）。</span><span class="sxs-lookup"><span data-stu-id="69638-105">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="69638-106">本部分介绍了与使用非托管 DLL 函数相关的任务，并提供有关平台调用的详细信息。</span><span class="sxs-lookup"><span data-stu-id="69638-106">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="69638-107">除了以下任务，还提供了一般注意事项以及包含其他信息和示例的链接。</span><span class="sxs-lookup"><span data-stu-id="69638-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="69638-108">若要使用导出的 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="69638-108">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="69638-109">[标识 DLL 中的函数](identifying-functions-in-dlls.md)。</span><span class="sxs-lookup"><span data-stu-id="69638-109">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="69638-110">至少必须指定函数名称及其内含的 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="69638-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="69638-111">[创建用于容纳 DLL 函数的类](creating-a-class-to-hold-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="69638-111">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="69638-112">可使用现有的类为每个非托管函数创建单独的类，或创建包含一组相关的非托管函数的类。</span><span class="sxs-lookup"><span data-stu-id="69638-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="69638-113">[在托管代码中创建原型](creating-prototypes-in-managed-code.md)。</span><span class="sxs-lookup"><span data-stu-id="69638-113">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="69638-114">[Visual Basic] 使用 Declare 语句以及 Function 和 Lib 关键字  。</span><span class="sxs-lookup"><span data-stu-id="69638-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="69638-115">在极少数情况下，可以使用 DllImportAttribute 和 Shared Function 关键字 。</span><span class="sxs-lookup"><span data-stu-id="69638-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="69638-116">本节稍后会对这些情况进行说明。</span><span class="sxs-lookup"><span data-stu-id="69638-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="69638-117">[C#] 使用 DllImportAttribute 标识 DLL 和函数。</span><span class="sxs-lookup"><span data-stu-id="69638-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="69638-118">为此方法标记 static 和 extern 修饰符 。</span><span class="sxs-lookup"><span data-stu-id="69638-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="69638-119">[C++] 使用 DllImportAttribute 标识 DLL 和函数。</span><span class="sxs-lookup"><span data-stu-id="69638-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="69638-120">用 extern "C" 标记此包装方法或函数。</span><span class="sxs-lookup"><span data-stu-id="69638-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="69638-121">[调用 DLL 函数](calling-a-dll-function.md)。</span><span class="sxs-lookup"><span data-stu-id="69638-121">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="69638-122">与调用任何其他托管方法一样，在托管类上调用方法。</span><span class="sxs-lookup"><span data-stu-id="69638-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="69638-123">[传递结构](passing-structures.md)和[实现回调函数](callback-functions.md)属于特殊情况。</span><span class="sxs-lookup"><span data-stu-id="69638-123">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="69638-124">有关演示如何构造要用于平台调用、基于 .NET 的声明的示例，请参阅[用平台调用封送数据](marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="69638-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="69638-125">平台调用详解</span><span class="sxs-lookup"><span data-stu-id="69638-125">A closer look at platform invoke</span></span>  
 <span data-ttu-id="69638-126">平台调用依赖元数据定位导出的函数并在运行时封送处理它的自变量。</span><span class="sxs-lookup"><span data-stu-id="69638-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="69638-127">下图显示了此过程。</span><span class="sxs-lookup"><span data-stu-id="69638-127">The following illustration shows this process.</span></span>  
  
 ![显示平台调用的图表。](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="69638-129">平台调用调用非托管函数时，将执行以下操作序列：</span><span class="sxs-lookup"><span data-stu-id="69638-129">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="69638-130">定位包含函数的 DLL。</span><span class="sxs-lookup"><span data-stu-id="69638-130">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="69638-131">将 DLL 加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="69638-131">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="69638-132">在内存中定位函数的地址并将其参数推送到堆栈上，从而根据需要封送数据。</span><span class="sxs-lookup"><span data-stu-id="69638-132">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69638-133">定位和加载 DLL，并定位仅在首次调用函数时内存中出现的函数地址。</span><span class="sxs-lookup"><span data-stu-id="69638-133">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="69638-134">将控制转移到非托管函数。</span><span class="sxs-lookup"><span data-stu-id="69638-134">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="69638-135">平台调用将向托管调用方引发非托管函数生成的异常。</span><span class="sxs-lookup"><span data-stu-id="69638-135">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="69638-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="69638-136">See also</span></span>

- [<span data-ttu-id="69638-137">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="69638-137">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="69638-138">平台调用示例</span><span class="sxs-lookup"><span data-stu-id="69638-138">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="69638-139">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="69638-139">Interop Marshaling</span></span>](interop-marshaling.md)
