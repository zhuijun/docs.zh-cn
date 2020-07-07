---
title: 标识 DLL 中的函数
description: 标识 DLL 中的函数。 DLL 函数的标识包括函数名称或序号，以及可在其中找到实现的 DLL 文件名。
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
ms.openlocfilehash: 054d1351a9ee6adab17117c9f423aa26d0d9ed59
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622726"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="b0df0-104">标识 DLL 中的函数</span><span class="sxs-lookup"><span data-stu-id="b0df0-104">Identifying Functions in DLLs</span></span>
<span data-ttu-id="b0df0-105">DLL 函数的标识由以下元素组成：</span><span class="sxs-lookup"><span data-stu-id="b0df0-105">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="b0df0-106">函数名称或序号</span><span class="sxs-lookup"><span data-stu-id="b0df0-106">Function name or ordinal</span></span>  
  
- <span data-ttu-id="b0df0-107">可以找到实现的 DLL 文件的名称</span><span class="sxs-lookup"><span data-stu-id="b0df0-107">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="b0df0-108">例如，指定 User32.dll 中的 MessageBox 函数可标识函数 (MessageBox) 及其位置（User32.dll、 User32 或 user32）。</span><span class="sxs-lookup"><span data-stu-id="b0df0-108">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="b0df0-109">Microsoft Windows 应用程序编程接口 (Windows API) 可以包含每个处理字符和字符串的函数的两个版本：1 字节字符 ANSI 版本和 2 字节字符 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="b0df0-109">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="b0df0-110">未指定时，由 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 字段表示的字符集默认为 ANSI。</span><span class="sxs-lookup"><span data-stu-id="b0df0-110">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="b0df0-111">某些函数可以具有两个以上的版本。</span><span class="sxs-lookup"><span data-stu-id="b0df0-111">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="b0df0-112">MessageBoxA 是 MessageBox 函数的 ANSI 入口点；MessageBoxW 是 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="b0df0-112">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="b0df0-113">可以通过运行多种命令行工具列出特定 DLL（如 user32.dll）的函数名称。</span><span class="sxs-lookup"><span data-stu-id="b0df0-113">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="b0df0-114">例如，可以使用 `dumpbin /exports user32.dll` 或 `link /dump /exports user32.dll` 来获取函数名称。</span><span class="sxs-lookup"><span data-stu-id="b0df0-114">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="b0df0-115">可以将非托管函数重命名为代码内的任意名称，只要将新名称映射到 DLL 中的原始入口点。</span><span class="sxs-lookup"><span data-stu-id="b0df0-115">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="b0df0-116">有关重命名托管源代码中的非托管 DLL 函数的说明，请参见[指定入口点](specifying-an-entry-point.md)。</span><span class="sxs-lookup"><span data-stu-id="b0df0-116">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="b0df0-117">借助平台调用，可以通过调用 Windows API 和其他 DLL 中的函数来控制操作系统的重要部分。</span><span class="sxs-lookup"><span data-stu-id="b0df0-117">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="b0df0-118">除了 Windows API，还可通过平台调用获取许多其他 API 和 DLL。</span><span class="sxs-lookup"><span data-stu-id="b0df0-118">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="b0df0-119">下表描述了 Windows API 中的多个常用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="b0df0-119">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="b0df0-120">DLL</span><span class="sxs-lookup"><span data-stu-id="b0df0-120">DLL</span></span>|<span data-ttu-id="b0df0-121">内容描述</span><span class="sxs-lookup"><span data-stu-id="b0df0-121">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="b0df0-122">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="b0df0-122">GDI32.dll</span></span>|<span data-ttu-id="b0df0-123">图形设备接口 (GDI) 函数，用于设备输出，例如用于绘图和字体管理。</span><span class="sxs-lookup"><span data-stu-id="b0df0-123">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="b0df0-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b0df0-124">Kernel32.dll</span></span>|<span data-ttu-id="b0df0-125">低级别的操作系统函数，用于内存管理和资源处理。</span><span class="sxs-lookup"><span data-stu-id="b0df0-125">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="b0df0-126">User32.dll</span><span class="sxs-lookup"><span data-stu-id="b0df0-126">User32.dll</span></span>|<span data-ttu-id="b0df0-127">Windows 管理函数，用于消息处理、计时器、菜单和通信。</span><span class="sxs-lookup"><span data-stu-id="b0df0-127">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="b0df0-128">有关 Windows API 的完整文档，请参阅平台 SDK。</span><span class="sxs-lookup"><span data-stu-id="b0df0-128">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="b0df0-129">有关演示如何构造要用于平台调用、基于 .NET 的声明的示例，请参阅[用平台调用封送数据](marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="b0df0-129">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0df0-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="b0df0-130">See also</span></span>

- [<span data-ttu-id="b0df0-131">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="b0df0-131">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="b0df0-132">指定入口点</span><span class="sxs-lookup"><span data-stu-id="b0df0-132">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="b0df0-133">创建用于容纳 DLL 函数的类</span><span class="sxs-lookup"><span data-stu-id="b0df0-133">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="b0df0-134">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="b0df0-134">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="b0df0-135">调用 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="b0df0-135">Calling a DLL Function</span></span>](calling-a-dll-function.md)
