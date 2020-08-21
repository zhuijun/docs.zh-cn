---
title: 其他工具
description: 概述了可安装的支持和扩展 .NET Core 功能的其他工具。
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: f7bfa660f7521adf4950d5bbdd59628bb88cca4d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557927"
---
# <a name="net-core-additional-tools-overview"></a><span data-ttu-id="278a7-103">.NET Core 附加工具概述</span><span class="sxs-lookup"><span data-stu-id="278a7-103">.NET Core additional tools overview</span></span>

<span data-ttu-id="278a7-104">本节除了 .NET Core CLI 外，还编译了可支持和扩展 .NET Core 功能的工具列表。</span><span class="sxs-lookup"><span data-stu-id="278a7-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the .NET Core CLI.</span></span>

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="278a7-105">.NET Core 卸载工具</span><span class="sxs-lookup"><span data-stu-id="278a7-105">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="278a7-106">使用 [.NET Core 卸载工具](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`)，可清理系统上的 .NET Core SDK 和运行时，以便仅保留指定的版本。</span><span class="sxs-lookup"><span data-stu-id="278a7-106">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you clean up .NET Core SDKs and Runtimes on a system such that only the specified versions remain.</span></span> <span data-ttu-id="278a7-107">可使用选项集合来指定要卸载的版本。</span><span class="sxs-lookup"><span data-stu-id="278a7-107">A collection of options is available to specify which versions are uninstalled.</span></span>

## <a name="net-core-diagnostic-tools"></a><span data-ttu-id="278a7-108">.NET Core 诊断工具</span><span class="sxs-lookup"><span data-stu-id="278a7-108">.NET Core diagnostic tools</span></span>

<span data-ttu-id="278a7-109">[dotnet-counters](../diagnostics/dotnet-counters.md) 是一个性能监视工具，用于初级运行状况监视和性能调查。</span><span class="sxs-lookup"><span data-stu-id="278a7-109">[dotnet-counters](../diagnostics/dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span>

<span data-ttu-id="278a7-110">通过 [dotnet-dump](../diagnostics/dotnet-dump.md)，可在不使用本机调试器的情况下收集和分析 Windows 和 Linux 核心转储。</span><span class="sxs-lookup"><span data-stu-id="278a7-110">[dotnet-dump](../diagnostics/dotnet-dump.md) provides a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

<span data-ttu-id="278a7-111">[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) 提供为活动 .NET 进程收集 GC（垃圾回收器）转储的方式。</span><span class="sxs-lookup"><span data-stu-id="278a7-111">[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) provides a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

<span data-ttu-id="278a7-112">[dotnet-trace](../diagnostics/dotnet-trace.md) 会从你的应用收集分析数据，这些数据可帮助你了解应用运行速度缓慢的原因。</span><span class="sxs-lookup"><span data-stu-id="278a7-112">[dotnet-trace](../diagnostics/dotnet-trace.md) collects profiling data from your app that can help in scenarios where you need to find out what causes an app to run slow.</span></span>

## <a name="wcf-web-service-reference-tool"></a><span data-ttu-id="278a7-113">WCF Web Service Reference 工具</span><span class="sxs-lookup"><span data-stu-id="278a7-113">WCF Web Service Reference tool</span></span>

<span data-ttu-id="278a7-114">WCF (Windows Communication Foundation) [Web ervice Reference 工具](wcf-web-service-reference-guide.md)是一个 Visual Studio 连接服务提供程序，首次推出是在 [Visual Studio 2017 版本 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools) 中。</span><span class="sxs-lookup"><span data-stu-id="278a7-114">The WCF (Windows Communication Foundation) [Web Service Reference tool](wcf-web-service-reference-guide.md) is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools).</span></span> <span data-ttu-id="278a7-115">此工具可从网络位置上当前解决方案的 Web 服务中，或从 WSDL 文件中检索元数据。</span><span class="sxs-lookup"><span data-stu-id="278a7-115">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file.</span></span> <span data-ttu-id="278a7-116">还可生成与 .NET Core 兼容的源文件并使用可用于访问 Web 服务操作的方法定义 WCF 代理类。</span><span class="sxs-lookup"><span data-stu-id="278a7-116">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tool"></a><span data-ttu-id="278a7-117">WCF dotnet-svcutil 工具</span><span class="sxs-lookup"><span data-stu-id="278a7-117">WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="278a7-118">WCF [dotnet-svcutil 工具](dotnet-svcutil-guide.md)是一个 .NET 工具，可从网络位置上的 Web 服务中或从 WSDL 文件中检索元数据。</span><span class="sxs-lookup"><span data-stu-id="278a7-118">The WCF [dotnet-svcutil tool](dotnet-svcutil-guide.md) is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file.</span></span> <span data-ttu-id="278a7-119">还可生成与 .NET Core 兼容的源文件并使用可用于访问 Web 服务操作的方法定义 WCF 代理类。</span><span class="sxs-lookup"><span data-stu-id="278a7-119">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

<span data-ttu-id="278a7-120">dotnet-svcutil 工具是 [WCF Web Service Reference](wcf-web-service-reference-guide.md) Visual Studio 连接服务提供程序（随 Visual Studio 2017 版本 15.5 首次推出）的替代产品\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="278a7-120">The **dotnet-svcutil** tool is an alternative to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider, which first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="278a7-121">dotnet-svcutil\*\*\*\* 工具作为一种 .NET 工具，可用于 Linux、macOS 和 Windows。</span><span class="sxs-lookup"><span data-stu-id="278a7-121">The **dotnet-svcutil** tool, as a .NET tool, is available on Linux, macOS, and Windows.</span></span>

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a><span data-ttu-id="278a7-122">WCF dotnet-svcutil.xmlserializer 工具</span><span class="sxs-lookup"><span data-stu-id="278a7-122">WCF dotnet-svcutil.xmlserializer tool</span></span>

<span data-ttu-id="278a7-123">在 .NET Framework 中，可以使用 svcutil 工具预生成序列化程序集。</span><span class="sxs-lookup"><span data-stu-id="278a7-123">On the .NET Framework, you can pre-generate a serialization assembly using the svcutil tool.</span></span> <span data-ttu-id="278a7-124">WCF [dotnet-svcutil.xmlserializer 工具](dotnet-svcutil.xmlserializer-guide.md)在 .NET Core 上提供类似的功能。</span><span class="sxs-lookup"><span data-stu-id="278a7-124">The WCF [dotnet-svcutil.xmlserializer tool](dotnet-svcutil.xmlserializer-guide.md) provides similar functionality on .NET Core.</span></span> <span data-ttu-id="278a7-125">它为客户端应用程序中 WCF 服务协定使用且可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化的类型预生成 C# 序列化代码。</span><span class="sxs-lookup"><span data-stu-id="278a7-125">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="278a7-126">当序列化或反序列化这些类型的对象时，这会提高 XML 序列化的启动性能。</span><span class="sxs-lookup"><span data-stu-id="278a7-126">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="xml-serializer-generator"></a><span data-ttu-id="278a7-127">XML 序列化程序生成器</span><span class="sxs-lookup"><span data-stu-id="278a7-127">XML Serializer Generator</span></span>

<span data-ttu-id="278a7-128">正如 [XML 序列化程序生成器工具 (Sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) 适用于 .NET Framework，[Microsoft.XmlSerializer.Generator NuGet 包](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) 是适用于 .NET Core 和 .NET 标准库的解决方案。</span><span class="sxs-lookup"><span data-stu-id="278a7-128">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="278a7-129">它为程序集中包含的类型创建 XML 序列化程序集，从而提高使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化或反序列化这些类型对象时，XML 序列化的启动性能。</span><span class="sxs-lookup"><span data-stu-id="278a7-129">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>
