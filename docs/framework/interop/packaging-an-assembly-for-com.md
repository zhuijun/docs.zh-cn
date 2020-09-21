---
title: 打包用于 COM 的 .NET Framework 程序集
description: 打包用于 COM 的 .NET 程序集。 收集 COM 应用程序可使用的类型列表、版本控制和部署说明以及类型库。
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 5fde7f7f00aadf4d941d4ffe522453970b67e9e2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554125"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="9aaf1-104">打包用于 COM 的 .NET Framework 程序集</span><span class="sxs-lookup"><span data-stu-id="9aaf1-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="9aaf1-105">COM 开发人员可从其计划纳入应用程序的托管类型相关信息中受益：</span><span class="sxs-lookup"><span data-stu-id="9aaf1-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="9aaf1-106">COM 应用程序可使用的类型列表</span><span class="sxs-lookup"><span data-stu-id="9aaf1-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="9aaf1-107">某些托管类型对 COM 不可见；某些可见但不可创建；某些既可见又可创建。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="9aaf1-108">程序集可以包括不可见、可见、不可创建和可创建类型的任何组合。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="9aaf1-109">为实现完整性，请确定打算公开到 COM 的程序集中的类型，尤其是当这些类型是公开到 .NET framework 中类型的子集时。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="9aaf1-110">有关其他信息，请参阅[为互操作限定 .NET 类型](../../standard/native-interop/qualify-net-types-for-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="9aaf1-111">版本控制说明</span><span class="sxs-lookup"><span data-stu-id="9aaf1-111">Versioning instructions</span></span>

  <span data-ttu-id="9aaf1-112">实现类接口（COM 互操作生成的接口）的托管类受版本控制限制。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="9aaf1-113">有关如何使用类接口的指南，请参阅[类接口简介](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="9aaf1-114">部署说明</span><span class="sxs-lookup"><span data-stu-id="9aaf1-114">Deployment instructions</span></span>

  <span data-ttu-id="9aaf1-115">发布者签名的具有强名称的程序集可安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="9aaf1-116">未签名程序集必须作为专用程序集安装在用户计算机上。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="9aaf1-117">有关其他信息，请参阅[程序集安全注意事项](../../standard/assembly/security-considerations.md)。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="9aaf1-118">类型库所含内容</span><span class="sxs-lookup"><span data-stu-id="9aaf1-118">Type library inclusion</span></span>

  <span data-ttu-id="9aaf1-119">大多数类型在由 COM 应用程序使用时都需要类型库。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="9aaf1-120">可生成类型库或使 COM 开发人员执行此任务。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="9aaf1-121">Windows SDK 为生成类型库提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="9aaf1-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="9aaf1-122">类型库导出程序</span><span class="sxs-lookup"><span data-stu-id="9aaf1-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="9aaf1-123">TypeLibConverter 类</span><span class="sxs-lookup"><span data-stu-id="9aaf1-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="9aaf1-124">程序集注册工具</span><span class="sxs-lookup"><span data-stu-id="9aaf1-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="9aaf1-125">.NET 服务安装工具</span><span class="sxs-lookup"><span data-stu-id="9aaf1-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="9aaf1-126">无论选择的机制如何，生成的类型库中仅包含所提供程序集中定义的公共类型。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="9aaf1-127">有关说明，请参阅[如何：将类型库作为 Win32 资源嵌入基于 .NET 的应用程序](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="9aaf1-128">类型库导出程序</span><span class="sxs-lookup"><span data-stu-id="9aaf1-128">Type Library Exporter</span></span>

<span data-ttu-id="9aaf1-129">[类型库导出程序 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 是命令行工具，可将程序集中包含的类和接口转换为 COM 类型库。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="9aaf1-130">一旦类的类型信息可用，COM 客户端就可创建 .NET 类的实例，并调用实例的方法，就像它是 COM 对象一样。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="9aaf1-131">Tlbexp.exe 一次转换整个程序集。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="9aaf1-132">不能使用 Tlbexp.exe 生成程序集中定义的类型子集的类型信息。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="9aaf1-133">TypeLibConverter 类</span><span class="sxs-lookup"><span data-stu-id="9aaf1-133">TypeLibConverter Class</span></span>

<span data-ttu-id="9aaf1-134">位于 System.Runtime.Interop 命名空间中的 <xref:System.Runtime.InteropServices.TypeLibConverter> 类将程序集中包含的类和接口转换为 COM 类型库。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="9aaf1-135">此 API 生成与类型库导出程序相同的类型信息，如上节所述。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="9aaf1-136">TypeLibConverter 类实现 <xref:System.Runtime.InteropServices.ITypeLibConverter>。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="9aaf1-137">程序集注册工具</span><span class="sxs-lookup"><span data-stu-id="9aaf1-137">Assembly Registration Tool</span></span>

<span data-ttu-id="9aaf1-138">[程序集注册工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 可在应用 /tlb: 选项时生成并注册类型库。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="9aaf1-139">COM 客户端要求在 Windows 注册表中安装类型库。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="9aaf1-140">如果不使用此选项，Regasm.exe 仅在程序集而非类型库中注册类型。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="9aaf1-141">在程序集中注册类型和注册类型库是不同的活动。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="9aaf1-142">.NET 服务安装工具</span><span class="sxs-lookup"><span data-stu-id="9aaf1-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="9aaf1-143">[.NET 服务安装工具 (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) 将托管类添加到 Windows 2000 组件服务，并在单个工具中组合多个任务。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="9aaf1-144">除加载和注册程序集外，Regsvcs.exe 还可将类型库生成、注册和安装到现有 COM+ 1.0 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9aaf1-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="9aaf1-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="9aaf1-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="9aaf1-146">向 COM 公开 .NET Framework 组件</span><span class="sxs-lookup"><span data-stu-id="9aaf1-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="9aaf1-147">为互操作限定 .NET 类型</span><span class="sxs-lookup"><span data-stu-id="9aaf1-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="9aaf1-148">类接口简介</span><span class="sxs-lookup"><span data-stu-id="9aaf1-148">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="9aaf1-149">程序集安全注意事项</span><span class="sxs-lookup"><span data-stu-id="9aaf1-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="9aaf1-150">Tlbexp.exe（类型库导出程序）</span><span class="sxs-lookup"><span data-stu-id="9aaf1-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="9aaf1-151">向 COM 注册程序集</span><span class="sxs-lookup"><span data-stu-id="9aaf1-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="9aaf1-152">[如何：将类型库作为 Win32 资源嵌入应用程序](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9aaf1-152">[How to: Embed Type Libraries as Win32 Resources in Applications](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
