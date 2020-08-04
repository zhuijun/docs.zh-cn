---
title: 互操作性 - C# 编程指南
description: 除了在公共语言运行时下运行的代码之外，互操作性还支持非托管代码。 使用这些资源来了解互操作选项。
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: d85eb51107d50e023270fcbe1ef6e08a7788ae78
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302966"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="55b01-104">互操作性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="55b01-104">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="55b01-105">借助互操作性，可以保留和利用对非托管代码的现有投资工作。</span><span class="sxs-lookup"><span data-stu-id="55b01-105">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="55b01-106">在公共语言运行时 (CLR) 控制下运行的代码称为*托管代码*，不在 CLR 控制下运行的代码称为*非托管代码*。</span><span class="sxs-lookup"><span data-stu-id="55b01-106">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="55b01-107">例如，COM、COM+、C++ 组件、ActiveX 组件和 Microsoft Windows API 都是非托管代码。</span><span class="sxs-lookup"><span data-stu-id="55b01-107">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="55b01-108">借助 .NET，可通过平台调用服务、<xref:System.Runtime.InteropServices> 命名空间、C++ 互操作性和 COM 互操作性（COM 互操作）实现与非托管代码的互操作性。</span><span class="sxs-lookup"><span data-stu-id="55b01-108">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55b01-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="55b01-109">In This Section</span></span>  
 [<span data-ttu-id="55b01-110">互操作性概述</span><span class="sxs-lookup"><span data-stu-id="55b01-110">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="55b01-111">介绍了实现 C# 托管代码和非托管代码的互操作性的方法。</span><span class="sxs-lookup"><span data-stu-id="55b01-111">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="55b01-112">如何使用 C# 功能访问 Office 互操作对象</span><span class="sxs-lookup"><span data-stu-id="55b01-112">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="55b01-113">介绍了 Visual C# 为了推动 Office 编程而引入的功能 。</span><span class="sxs-lookup"><span data-stu-id="55b01-113">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="55b01-114">如何在 COM 互操作编程中使用索引属性</span><span class="sxs-lookup"><span data-stu-id="55b01-114">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="55b01-115">介绍了如何使用已编入索引的属性来访问包含参数的 COM 属性。</span><span class="sxs-lookup"><span data-stu-id="55b01-115">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="55b01-116">如何使用平台调用播放 WAV 文件</span><span class="sxs-lookup"><span data-stu-id="55b01-116">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="55b01-117">介绍了如何使用平台调用服务在 Windows 操作系统中播放 .wav 声音文件。</span><span class="sxs-lookup"><span data-stu-id="55b01-117">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="55b01-118">演练：Office 编程</span><span class="sxs-lookup"><span data-stu-id="55b01-118">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="55b01-119">展示了如何创建 Excel 工作簿和包含指向此工作簿的链接的 Word 文档。</span><span class="sxs-lookup"><span data-stu-id="55b01-119">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="55b01-120">COM 类示例</span><span class="sxs-lookup"><span data-stu-id="55b01-120">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="55b01-121">展示了如何将 C# 类公开为 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="55b01-121">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="55b01-122">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="55b01-122">C# Language Specification</span></span>  

<span data-ttu-id="55b01-123">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[基本概念](~/_csharplang/spec/unsafe-code.md)。</span><span class="sxs-lookup"><span data-stu-id="55b01-123">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="55b01-124">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="55b01-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55b01-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="55b01-125">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="55b01-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="55b01-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="55b01-127">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="55b01-127">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="55b01-128">演练：Office 编程</span><span class="sxs-lookup"><span data-stu-id="55b01-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
