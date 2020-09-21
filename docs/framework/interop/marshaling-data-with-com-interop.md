---
title: 用 COM 互操作对数据进行封送处理
description: 请参阅涵盖用 COM 互操作对数据进行封送处理的文章。 Tlbimp.exe 和 Tlbexp.exe 工具在 COM 类型库和互操作程序集之间转换。
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: 94149e0c444cad7e32f959eaedd55bf14acb1ecb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547839"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="16f95-104">用 COM 互操作对数据进行封送处理</span><span class="sxs-lookup"><span data-stu-id="16f95-104">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="16f95-105">COM 互操作同时对在托管代码中使用 COM 对象和向 COM 公开托管对象提供支持。</span><span class="sxs-lookup"><span data-stu-id="16f95-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="16f95-106">对于将数据封送到 COM 和从 COM 中封送数据的支持是广泛的，并几乎总是提供正确的封送行为。</span><span class="sxs-lookup"><span data-stu-id="16f95-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="16f95-107">Windows SDK 包括以下 COM 互操作工具：</span><span class="sxs-lookup"><span data-stu-id="16f95-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="16f95-108">[类型库导入程序 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)，它将 COM 类型库转换为互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="16f95-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="16f95-109">从该程序集中，互操作封送处理服务生成包装器，该包装器在托管内存和非托管内存之间执行数据封送。</span><span class="sxs-lookup"><span data-stu-id="16f95-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="16f95-110">[类型库导出程序 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)，它从程序集产生 COM 类型库，并生成在方法调用期间执行封送的包装器。</span><span class="sxs-lookup"><span data-stu-id="16f95-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="16f95-111">以下部分链接到特定主题，这些主题描述在能够（或必须）为封送拆收器提供附加类型信息时自定义互操作包装器的过程。</span><span class="sxs-lookup"><span data-stu-id="16f95-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16f95-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="16f95-112">In This Section</span></span>  
<span data-ttu-id="16f95-113">[如何：手动创建包装器](how-to-create-wrappers-manually.md)描述如何在托管源代码中手动创建 COM 包装器。</span><span class="sxs-lookup"><span data-stu-id="16f95-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="16f95-114">如何：将托管代码 DCOM 迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="16f95-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="16f95-115">描述如何将托管 DCOM 代码迁移到 WCF，以得到最安全的解决方案。</span><span class="sxs-lookup"><span data-stu-id="16f95-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16f95-116">相关章节</span><span class="sxs-lookup"><span data-stu-id="16f95-116">Related Sections</span></span>  
 <span data-ttu-id="16f95-117">[COM 数据类型](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-117">[COM Data Types](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-118">提供相应的托管和非托管数据类型。</span><span class="sxs-lookup"><span data-stu-id="16f95-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="16f95-119">[自定义 COM 可调用包装器](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-119">[Customizing COM Callable Wrappers](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-120">描述如何在设计时使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性显式封送数据类型。</span><span class="sxs-lookup"><span data-stu-id="16f95-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="16f95-121">[自定义运行时可调用包装器](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-121">[Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-122">描述如何调整互操作程序集中类型的封送行为以及如何以手动方式定义 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="16f95-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="16f95-123">[高级 COM 互操作性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-123">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-124">提供一些链接，指向关于将 COM 组件并入 .NET Framework 应用程序中的详细信息。</span><span class="sxs-lookup"><span data-stu-id="16f95-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="16f95-125">[有关从程序集转换到类型库的摘要](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-125">[Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-126">描述从程序集到类型库的导出转换过程。</span><span class="sxs-lookup"><span data-stu-id="16f95-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="16f95-127">[有关从类型库转换到程序集的摘要](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-127">[Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-128">描述从类型库到程序集的导入转换过程。</span><span class="sxs-lookup"><span data-stu-id="16f95-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="16f95-129">[使用泛型类型进行交互操作](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16f95-129">[Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="16f95-130">描述在使用用于 COM 互操作性的泛型类型时，哪些操作受支持。</span><span class="sxs-lookup"><span data-stu-id="16f95-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
