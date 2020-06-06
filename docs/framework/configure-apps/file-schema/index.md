---
title: .NET Framework 的配置文件架构
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039162"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="59c98-102">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="59c98-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="59c98-103">配置文件是可用来更改应用设置并为其设置策略的标准 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="59c98-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="59c98-104">.NET Framework 配置架构由一些可在配置文件中用来控制应用行为的元素组成。</span><span class="sxs-lookup"><span data-stu-id="59c98-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="59c98-105">本节的目录反映了架构的层次结构：启动、运行时、网络和其他配置设置类型。</span><span class="sxs-lookup"><span data-stu-id="59c98-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="59c98-106">有关配置文件类型、格式和位置的信息，请参阅[配置应用](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="59c98-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="59c98-107">若要直接编辑配置文件，需要自行熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="59c98-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59c98-108">配置文件中的 XML 标记和特性区分大小写。</span><span class="sxs-lookup"><span data-stu-id="59c98-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="59c98-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="59c98-109">In this section</span></span>

<span data-ttu-id="59c98-110">[**\<configuration>** Element](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="59c98-111">所有配置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="59c98-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="59c98-113">指定配置级的程序集绑定策略。</span><span class="sxs-lookup"><span data-stu-id="59c98-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="59c98-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="59c98-115">指定要包含的配置文件。</span><span class="sxs-lookup"><span data-stu-id="59c98-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="59c98-116">[启动设置架构](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-116">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="59c98-117">指定要使用的公共语言运行时版本的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="59c98-118">[运行时设置架构](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="59c98-119">配置程序集绑定和运行时行为的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="59c98-120">[网络设置架构](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="59c98-121">指定 .NET Framework 如何连接到 internet 的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="59c98-122">[加密设置架构](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-122">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="59c98-123">将友好算法名称映射到实现密码算法的类的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="59c98-124">[配置节架构](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-124">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="59c98-125">用于创建和使用自定义设置的配置节的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="59c98-126">[跟踪和调试设置架构](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="59c98-127">用于指定跟踪开关和侦听器的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="59c98-128">[编译器和语言提供程序设置架构](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="59c98-129">指定可用语言提供程序的编译器配置的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="59c98-130">[应用程序设置架构](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-130">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="59c98-131">使 Windows 窗体或 ASP.NET 应用程序可以存储和检索应用程序范围的设置和用户范围的设置的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="59c98-132">[应用设置架构](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-132">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="59c98-133">包含自定义应用程序设置，如文件路径、XML Web service URL 或应用程序的任何其他自定义配置信息。</span><span class="sxs-lookup"><span data-stu-id="59c98-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="59c98-134">[Web 设置架构](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-134">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="59c98-135">用于配置 ASP.NET 如何与主机应用程序（如 IIS）一起工作的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="59c98-136">在 Aspnet.config\*\* 文件中使用。</span><span class="sxs-lookup"><span data-stu-id="59c98-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="59c98-137">[Windows 窗体配置架构](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-137">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="59c98-138">Windows 窗体应用程序配置部分中的所有元素，包括多监视器和高 DPI 支持等自定义。</span><span class="sxs-lookup"><span data-stu-id="59c98-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="59c98-139">[WCF 配置架构](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-139">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="59c98-140">使你能够配置 WCF 服务和客户端应用程序的所有元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="59c98-141">[WCF 指令语法](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="59c98-142">介绍 `@ServiceHost` 指令，该指令定义 .svc 编译器使用的特定于页的属性。</span><span class="sxs-lookup"><span data-stu-id="59c98-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="59c98-143">[WIF 配置架构](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="59c98-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="59c98-144">Windows Identity Foundation （WIF）配置架构的所有元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="59c98-145">相关章节</span><span class="sxs-lookup"><span data-stu-id="59c98-145">Related sections</span></span>

<span data-ttu-id="59c98-146">[远程处理设置架构](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="59c98-146">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="59c98-147">描述对实现远程处理的客户端和服务器应用程序进行配置的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="59c98-148">[ASP.NET 设置架构](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="59c98-148">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="59c98-149">描述控制 ASP.NET Web 应用程序的行为的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="59c98-150">[Web 服务设置架构](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="59c98-150">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="59c98-151">描述控制 ASP.NET Web 服务以及它们的客户端的行为的元素。</span><span class="sxs-lookup"><span data-stu-id="59c98-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="59c98-152">[配置 .NET Framework 应用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="59c98-152">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="59c98-153">描述如何在 .NET Framework 中配置安全性、程序集绑定和远程处理。</span><span class="sxs-lookup"><span data-stu-id="59c98-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
