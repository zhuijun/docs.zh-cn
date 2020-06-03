---
title: 互操作性 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e53465066cf27a5f46c66ac73ee242370be23395
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242002"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="00b9a-102">互操作性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="00b9a-102">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="00b9a-103">借助互操作性，可以保留和利用对非托管代码的现有投资工作。</span><span class="sxs-lookup"><span data-stu-id="00b9a-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="00b9a-104">在公共语言运行时 (CLR) 控制下运行的代码称为*托管代码*，不在 CLR 控制下运行的代码称为*非托管代码*。</span><span class="sxs-lookup"><span data-stu-id="00b9a-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="00b9a-105">例如，COM、COM+、C++ 组件、ActiveX 组件和 Microsoft Windows API 都是非托管代码。</span><span class="sxs-lookup"><span data-stu-id="00b9a-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="00b9a-106">借助 .NET，可通过平台调用服务、<xref:System.Runtime.InteropServices> 命名空间、C++ 互操作性和 COM 互操作性（COM 互操作）实现与非托管代码的互操作性。</span><span class="sxs-lookup"><span data-stu-id="00b9a-106">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00b9a-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="00b9a-107">In This Section</span></span>  
 [<span data-ttu-id="00b9a-108">互操作性概述</span><span class="sxs-lookup"><span data-stu-id="00b9a-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="00b9a-109">介绍了实现 C# 托管代码和非托管代码的互操作性的方法。</span><span class="sxs-lookup"><span data-stu-id="00b9a-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="00b9a-110">如何使用 C# 功能访问 Office 互操作对象</span><span class="sxs-lookup"><span data-stu-id="00b9a-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="00b9a-111">介绍了 Visual C# 为了推动 Office 编程而引入的功能 。</span><span class="sxs-lookup"><span data-stu-id="00b9a-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="00b9a-112">如何在 COM 互操作编程中使用索引属性</span><span class="sxs-lookup"><span data-stu-id="00b9a-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="00b9a-113">介绍了如何使用已编入索引的属性来访问包含参数的 COM 属性。</span><span class="sxs-lookup"><span data-stu-id="00b9a-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="00b9a-114">如何使用平台调用播放 WAV 文件</span><span class="sxs-lookup"><span data-stu-id="00b9a-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="00b9a-115">介绍了如何使用平台调用服务在 Windows 操作系统中播放 .wav 声音文件。</span><span class="sxs-lookup"><span data-stu-id="00b9a-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="00b9a-116">演练：Office 编程</span><span class="sxs-lookup"><span data-stu-id="00b9a-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="00b9a-117">展示了如何创建 Excel 工作簿和包含指向此工作簿的链接的 Word 文档。</span><span class="sxs-lookup"><span data-stu-id="00b9a-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="00b9a-118">COM 类示例</span><span class="sxs-lookup"><span data-stu-id="00b9a-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="00b9a-119">展示了如何将 C# 类公开为 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="00b9a-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="00b9a-120">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="00b9a-120">C# Language Specification</span></span>  

<span data-ttu-id="00b9a-121">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[基本概念](~/_csharplang/spec/unsafe-code.md)。</span><span class="sxs-lookup"><span data-stu-id="00b9a-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="00b9a-122">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="00b9a-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="00b9a-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="00b9a-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="00b9a-124">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="00b9a-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="00b9a-125">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="00b9a-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="00b9a-126">演练：Office 编程</span><span class="sxs-lookup"><span data-stu-id="00b9a-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
