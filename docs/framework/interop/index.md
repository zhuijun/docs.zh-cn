---
title: 与非托管代码进行交互操作
description: 查看与非托管代码的互操作。 CLR 对客户端和服务器隐藏 .NET 组件对象模型与非托管代码的区别。
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: 1cebd75907fd202715cb337593186d248107bdbb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621868"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="465f3-104">与非托管代码进行交互操作</span><span class="sxs-lookup"><span data-stu-id="465f3-104">Interoperating with unmanaged code</span></span>

<span data-ttu-id="465f3-105">.NET Framework 提升与 COM 组件、COM+ 服务、外部类型库和许多操作系统服务的交互。</span><span class="sxs-lookup"><span data-stu-id="465f3-105">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="465f3-106">托管和非托管对象模型之间的数据类型、方法签名和错误处理机制有所不同。</span><span class="sxs-lookup"><span data-stu-id="465f3-106">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="465f3-107">要简化 .NET Framework 组件和非托管代码之间的互操作并简化迁移路径，公共语言运行时需对客户端和服务器隐藏这些对象模型中的差异。</span><span class="sxs-lookup"><span data-stu-id="465f3-107">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="465f3-108">在运行时控制下执行的代码称为托管代码。</span><span class="sxs-lookup"><span data-stu-id="465f3-108">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="465f3-109">反之，在运行时以外运行的代码称为非托管代码。</span><span class="sxs-lookup"><span data-stu-id="465f3-109">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="465f3-110">COM 组件、ActiveX 接口和 Windows API 函数都是非托管代码的示例。</span><span class="sxs-lookup"><span data-stu-id="465f3-110">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="465f3-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="465f3-111">In this section</span></span>

[<span data-ttu-id="465f3-112">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="465f3-112">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="465f3-113">描述如何使用 .NET Framework 应用程序的 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="465f3-113">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="465f3-114">向 COM 公开 .NET Framework 组件</span><span class="sxs-lookup"><span data-stu-id="465f3-114">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="465f3-115">描述如何使用 COM 应用程序的 .NET Framework 组件。</span><span class="sxs-lookup"><span data-stu-id="465f3-115">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="465f3-116">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="465f3-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="465f3-117">描述如何使用平台调用调用非托管 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="465f3-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="465f3-118">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="465f3-118">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="465f3-119">描述 COM 互操作和平台调用的封送处理。</span><span class="sxs-lookup"><span data-stu-id="465f3-119">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="465f3-120">如何：映射 HRESULT 和异常</span><span class="sxs-lookup"><span data-stu-id="465f3-120">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="465f3-121">描述异常和 HRESULT 之间的映射。</span><span class="sxs-lookup"><span data-stu-id="465f3-121">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="465f3-122">类型等效性和嵌入的互操作类型</span><span class="sxs-lookup"><span data-stu-id="465f3-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="465f3-123">介绍如何在程序集中嵌入 COM 类型的类型信息，以及公共语言运行时如何确定嵌入的 COM 类型的等效性。</span><span class="sxs-lookup"><span data-stu-id="465f3-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="465f3-124">如何：使用 Tlbimp.exe 生成主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="465f3-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="465f3-125">介绍如何使用 Tlbimp.exe （类型库导入程序）生成主要互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="465f3-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="465f3-126">如何：注册主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="465f3-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="465f3-127">介绍如何注册主互操作程序集，然后才能在项目中引用它们。</span><span class="sxs-lookup"><span data-stu-id="465f3-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="465f3-128">免注册 COM 互操作</span><span class="sxs-lookup"><span data-stu-id="465f3-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="465f3-129">介绍 COM 互操作如何在不使用 Windows 注册表的情况下激活组件。</span><span class="sxs-lookup"><span data-stu-id="465f3-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="465f3-130">如何：配置基于 .NET Framework 的 COM 组件以进行免注册激活</span><span class="sxs-lookup"><span data-stu-id="465f3-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="465f3-131">介绍如何创建应用程序清单以及如何创建并嵌入组件清单。</span><span class="sxs-lookup"><span data-stu-id="465f3-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="465f3-132">相关章节</span><span class="sxs-lookup"><span data-stu-id="465f3-132">Related sections</span></span>

[<span data-ttu-id="465f3-133">COM 包装</span><span class="sxs-lookup"><span data-stu-id="465f3-133">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="465f3-134">介绍 COM 互操作提供的包装器。</span><span class="sxs-lookup"><span data-stu-id="465f3-134">Describes the wrappers provided by COM interop.</span></span>
