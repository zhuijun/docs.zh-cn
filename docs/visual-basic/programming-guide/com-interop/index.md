---
title: COM 互操作
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: 66762d4551e458b36b70fb0831bf17ade70aa8cb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083223"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="a6e29-102">COM 互操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6e29-102">COM Interop (Visual Basic)</span></span>

<span data-ttu-id="a6e29-103">组件对象模型 (COM) 允许对象向其他组件和主机应用公开自己的功能。</span><span class="sxs-lookup"><span data-stu-id="a6e29-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="a6e29-104">如今的大部分软件都包含 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="a6e29-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="a6e29-105">尽管 .NET 程序集是新应用的最佳选择，有时也建议使用 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="a6e29-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="a6e29-106">本部分介绍与 Visual Basic 创建和使用 COM 对象相关的一些问题。</span><span class="sxs-lookup"><span data-stu-id="a6e29-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6e29-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="a6e29-107">In This Section</span></span>  

 [<span data-ttu-id="a6e29-108">COM 互操作介绍</span><span class="sxs-lookup"><span data-stu-id="a6e29-108">Introduction to COM Interop</span></span>](introduction-to-com-interop.md)  
 <span data-ttu-id="a6e29-109">概述了 COM 互操作性。</span><span class="sxs-lookup"><span data-stu-id="a6e29-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="a6e29-110">如何：从 Visual Basic 中引用 COM 对象</span><span class="sxs-lookup"><span data-stu-id="a6e29-110">How to: Reference COM Objects from Visual Basic</span></span>](how-to-reference-com-objects.md)  
 <span data-ttu-id="a6e29-111">介绍了如何添加对包含类型库的 COM 对象的引用。</span><span class="sxs-lookup"><span data-stu-id="a6e29-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="a6e29-112">如何：使用 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="a6e29-112">How to: Work with ActiveX Controls</span></span>](how-to-work-with-activex-controls.md)  
 <span data-ttu-id="a6e29-113">演示如何使用现有 ActiveX 控件将功能添加到 Visual Studio "工具箱"。</span><span class="sxs-lookup"><span data-stu-id="a6e29-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="a6e29-114">演练：调用 Windows API</span><span class="sxs-lookup"><span data-stu-id="a6e29-114">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="a6e29-115">逐步介绍了如何调用属于 Windows 操作系统的 API。</span><span class="sxs-lookup"><span data-stu-id="a6e29-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="a6e29-116">如何：调用 Windows API</span><span class="sxs-lookup"><span data-stu-id="a6e29-116">How to: Call Windows APIs</span></span>](how-to-call-windows-apis.md)  
 <span data-ttu-id="a6e29-117">展示了如何在 User32.dll 中定义和调用 `MessageBox` 函数。</span><span class="sxs-lookup"><span data-stu-id="a6e29-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="a6e29-118">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="a6e29-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="a6e29-119">展示了如何调用包含无符号类型参数的 Windows 函数。</span><span class="sxs-lookup"><span data-stu-id="a6e29-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="a6e29-120">演练：使用 Visual Basic 创建 COM 对象</span><span class="sxs-lookup"><span data-stu-id="a6e29-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](walkthrough-creating-com-objects.md)  
 <span data-ttu-id="a6e29-121">逐步介绍了如何使用和不使用 COM 类模板创建 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="a6e29-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="a6e29-122">互操作性疑难解答</span><span class="sxs-lookup"><span data-stu-id="a6e29-122">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)  
 <span data-ttu-id="a6e29-123">介绍了一些在使用 COM 时可能会遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="a6e29-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="a6e29-124">.NET Framework 应用程序中的 COM 互操作性</span><span class="sxs-lookup"><span data-stu-id="a6e29-124">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="a6e29-125">概述了如何在同一应用中使用 COM 对象和 .NET Framework 对象。</span><span class="sxs-lookup"><span data-stu-id="a6e29-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="a6e29-126">演练：使用 COM 对象实现继承</span><span class="sxs-lookup"><span data-stu-id="a6e29-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="a6e29-127">介绍了如何将现有 COM 对象用作新对象的基础。</span><span class="sxs-lookup"><span data-stu-id="a6e29-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6e29-128">相关章节</span><span class="sxs-lookup"><span data-stu-id="a6e29-128">Related Sections</span></span>  

 [<span data-ttu-id="a6e29-129">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="a6e29-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="a6e29-130">描述由公共语言运行时提供的互操作性服务。</span><span class="sxs-lookup"><span data-stu-id="a6e29-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="a6e29-131">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="a6e29-131">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="a6e29-132">介绍了如何通过 COM 互操作调用 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="a6e29-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="a6e29-133">向 COM 公开 .NET Framework 组件</span><span class="sxs-lookup"><span data-stu-id="a6e29-133">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="a6e29-134">介绍了如何准备和使用 COM 中的托管类型。</span><span class="sxs-lookup"><span data-stu-id="a6e29-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="a6e29-135">应用互操作属性</span><span class="sxs-lookup"><span data-stu-id="a6e29-135">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="a6e29-136">介绍了在使用非托管代码时可以使用的属性。</span><span class="sxs-lookup"><span data-stu-id="a6e29-136">Covers attributes you can use when working with unmanaged code.</span></span>
