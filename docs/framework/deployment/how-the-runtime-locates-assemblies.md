---
title: 运行时如何定位程序集
description: 了解公共语言运行时 (CLR) 如何在 .NET 中查找并绑定到构成应用程序的程序集。
ms.date: 03/30/2017
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
ms.openlocfilehash: 4cf1e5787fe2e430d20208d8e79b610e9126c67c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622622"
---
# <a name="how-the-runtime-locates-assemblies"></a><span data-ttu-id="de5c1-103">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="de5c1-103">How the Runtime Locates Assemblies</span></span>

<span data-ttu-id="de5c1-104">若要成功部署 .NET Framework 应用程序，必须了解公共语言运行时如何查找和绑定到构成应用程序的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-104">To successfully deploy your .NET Framework application, you must understand how the common language runtime locates and binds to the assemblies that make up your application.</span></span> <span data-ttu-id="de5c1-105">默认情况下，运行时尝试与生成应用程序的程序集的准确版本绑定。</span><span class="sxs-lookup"><span data-stu-id="de5c1-105">By default, the runtime attempts to bind with the exact version of an assembly that the application was built with.</span></span> <span data-ttu-id="de5c1-106">可通过配置文件设置重写此默认行为。</span><span class="sxs-lookup"><span data-stu-id="de5c1-106">This default behavior can be overridden by configuration file settings.</span></span>

<span data-ttu-id="de5c1-107">在尝试查找程序集和解析程序集引用时，公共语言运行时会执行多个步骤。</span><span class="sxs-lookup"><span data-stu-id="de5c1-107">The common language runtime performs a number of steps when attempting to locate an assembly and resolve an assembly reference.</span></span> <span data-ttu-id="de5c1-108">以下各节将分别阐述每个步骤。</span><span class="sxs-lookup"><span data-stu-id="de5c1-108">Each step is explained in the following sections.</span></span> <span data-ttu-id="de5c1-109">描述运行时如何查找程序集时，通常使用术语“探测”；它指一套用于根据名称和区域性查找程序集的试探法。</span><span class="sxs-lookup"><span data-stu-id="de5c1-109">The term probing is often used when describing how the runtime locates assemblies; it refers to the set of heuristics used to locate the assembly based on its name and culture.</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-110">可使用 Windows SDK 中附带的[程序集绑定日志查看器 (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) 查看日志文件中的绑定信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-110">You can view binding information in the log file using the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which is included in the Windows SDK.</span></span>

## <a name="initiating-the-bind"></a><span data-ttu-id="de5c1-111">启动绑定</span><span class="sxs-lookup"><span data-stu-id="de5c1-111">Initiating the Bind</span></span>

<span data-ttu-id="de5c1-112">在运行时尝试解析其他程序集的引用时，开始查找和绑定到程序集的进程。</span><span class="sxs-lookup"><span data-stu-id="de5c1-112">The process of locating and binding to an assembly begins when the runtime attempts to resolve a reference to another assembly.</span></span> <span data-ttu-id="de5c1-113">此引用可为静态，也可为动态。</span><span class="sxs-lookup"><span data-stu-id="de5c1-113">This reference can be either static or dynamic.</span></span> <span data-ttu-id="de5c1-114">编译器在生成时记录程序集清单的元数据中的静态引用。</span><span class="sxs-lookup"><span data-stu-id="de5c1-114">The compiler records static references in the assembly manifest's metadata at build time.</span></span> <span data-ttu-id="de5c1-115">由于调用各种方法（如 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>），所以将及时构造动态引用。</span><span class="sxs-lookup"><span data-stu-id="de5c1-115">Dynamic references are constructed on the fly as a result of calling various methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="de5c1-116">引用程序集的首选方式是使用完整引用，包括程序集名称、版本、区域性和公钥标记（若有）。</span><span class="sxs-lookup"><span data-stu-id="de5c1-116">The preferred way to reference an assembly is to use a full reference, including the assembly name, version, culture, and public key token (if one exists).</span></span> <span data-ttu-id="de5c1-117">运行时按照本节稍后描述的步骤使用此信息查找程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-117">The runtime uses this information to locate the assembly, following the steps described later in this section.</span></span> <span data-ttu-id="de5c1-118">无论引用针对的程序集是静态还是动态，运行时均使用相同的解析进程。</span><span class="sxs-lookup"><span data-stu-id="de5c1-118">The runtime uses the same resolution process regardless of whether the reference is for a static or dynamic assembly.</span></span>

<span data-ttu-id="de5c1-119">还可通过仅向调用方法提供程序集的部分信息（例如，仅指定程序集名称）动态引用程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-119">You can also make a dynamic reference to an assembly by providing the calling method with only partial information about the assembly, such as specifying only the assembly name.</span></span> <span data-ttu-id="de5c1-120">在这种情况下，仅搜索程序集的应用程序目录，不进行其他检查。</span><span class="sxs-lookup"><span data-stu-id="de5c1-120">In this case, only the application directory is searched for the assembly, and no other checking occurs.</span></span> <span data-ttu-id="de5c1-121">通过使用任一方式加载程序集（ <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 或 <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>），可执行部分引用。</span><span class="sxs-lookup"><span data-stu-id="de5c1-121">You make a partial reference using any of the various methods for loading assemblies such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="de5c1-122">最后，可使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 等方法执行动态引用并仅提供部分信息；然后使用应用程序配置文件中的 [\<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) 元素限定该引用。</span><span class="sxs-lookup"><span data-stu-id="de5c1-122">Finally, you can make a dynamic reference using a method such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> and provide only partial information; you then qualify the reference using the [\<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) element in the application configuration file.</span></span> <span data-ttu-id="de5c1-123">借助此元素，你可以提供应用程序配置文件（而不是代码）中的完全引用信息（名称、版本、区域性和公钥标记（若适用））。</span><span class="sxs-lookup"><span data-stu-id="de5c1-123">This element allows you to provide the full reference information (name, version, culture and, if applicable, the public key token) in your application configuration file instead of in your code.</span></span> <span data-ttu-id="de5c1-124">如果想要完全限定应用程序目录之外的程序集引用，或者如果想要引用全局程序集缓存中的程序集且轻松指定配置文件（而不是代码）中的完全引用，可使用此技术。</span><span class="sxs-lookup"><span data-stu-id="de5c1-124">You would use this technique if you wanted to fully qualify a reference to an assembly outside the application directory, or if you wanted to reference an assembly in the global assembly cache but you wanted the convenience of specifying the full reference in the configuration file instead of in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-125">多个应用程序间共享的程序集不应使用此类型的部分引用。</span><span class="sxs-lookup"><span data-stu-id="de5c1-125">This type of partial reference should not be used with assemblies that are shared among several applications.</span></span> <span data-ttu-id="de5c1-126">因为配置设置是基于每个应用程序（而非每个程序集）应用的，所以使用此类部分引用的共享程序集需要使用共享程序集的每个应用程序的配置文件中都具有限定信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-126">Because configuration settings are applied per application and not per assembly, a shared assembly using this type of partial reference would require each application using the shared assembly to have the qualifying information in its configuration file.</span></span>

<span data-ttu-id="de5c1-127">运行时使用以下步骤解析程序集引用：</span><span class="sxs-lookup"><span data-stu-id="de5c1-127">The runtime uses the following steps to resolve an assembly reference:</span></span>

1. <span data-ttu-id="de5c1-128">通过检查适用的配置文件（包括应用程序配置文件、发布服务器策略文件和计算机配置文件）[确定正确的程序集版本](#step1) 。</span><span class="sxs-lookup"><span data-stu-id="de5c1-128">[Determines the correct assembly version](#step1) by examining applicable configuration files, including the application configuration file, publisher policy file, and machine configuration file.</span></span> <span data-ttu-id="de5c1-129">如果配置文件位于远程计算机，运行时必须首先查找并下载此应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-129">If the configuration file is located on a remote machine, the runtime must locate and download the application configuration file first.</span></span>

2. <span data-ttu-id="de5c1-130">[检查之前是否已绑定程序集名称](#step2) ，若如此，请使用先前加载的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-130">[Checks whether the assembly name has been bound to before](#step2) and, if so, uses the previously loaded assembly.</span></span> <span data-ttu-id="de5c1-131">如果加载程序集的先前请求失败，此请求会立即失败且不会尝试加载程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-131">If a previous request to load the assembly failed, the request is failed immediately without attempting to load the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="de5c1-132">程序集绑定故障缓存是 .NET Framework 2.0 版本中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="de5c1-132">The caching of assembly binding failures is new in the .NET Framework version 2.0.</span></span>

3. <span data-ttu-id="de5c1-133">[检查全局程序集缓存](#step3)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-133">[Checks the global assembly cache](#step3).</span></span> <span data-ttu-id="de5c1-134">如果此处存在程序集，则运行时使用此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-134">If the assembly is found there, the runtime uses this assembly.</span></span>

4. <span data-ttu-id="de5c1-135">使用以下步骤[探测程序集](#step4) ：</span><span class="sxs-lookup"><span data-stu-id="de5c1-135">[Probes for the assembly](#step4) using the following steps:</span></span>

    1. <span data-ttu-id="de5c1-136">如果配置和发布服务器策略均不影响原始引用且绑定请求是使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 方法创建的，运行时将检查是否存在位置提示。</span><span class="sxs-lookup"><span data-stu-id="de5c1-136">If configuration and publisher policy do not affect the original reference and if the bind request was created using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method, the runtime checks for location hints.</span></span>

    2. <span data-ttu-id="de5c1-137">如果配置文件中存在代码库，则运行时只检查此位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-137">If a codebase is found in the configuration files, the runtime checks only this location.</span></span> <span data-ttu-id="de5c1-138">如果此探测失败，运行时确定绑定请求已失败且不执行其他探测。</span><span class="sxs-lookup"><span data-stu-id="de5c1-138">If this probe fails, the runtime determines that the binding request failed and no other probing occurs.</span></span>

    3. <span data-ttu-id="de5c1-139">使用 [探测章节](#step4)中所述的试探法探测程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-139">Probes for the assembly using the heuristics described in the [probing section](#step4).</span></span> <span data-ttu-id="de5c1-140">如果探测后找不到程序集，运行时将请求 Windows Installer 提供程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-140">If the assembly is not found after probing, the runtime requests the Windows Installer to provide the assembly.</span></span> <span data-ttu-id="de5c1-141">这相当于按需安装功能。</span><span class="sxs-lookup"><span data-stu-id="de5c1-141">This acts as an install-on-demand feature.</span></span>

        > [!NOTE]
        > <span data-ttu-id="de5c1-142">不会检查未带强名称的程序集版本，运行时也不会检查全局程序集缓存中未带强名称的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-142">There is no version checking for assemblies without strong names, nor does the runtime check in the global assembly cache for assemblies without strong names.</span></span>

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a><span data-ttu-id="de5c1-143">步骤 1：检查配置文件</span><span class="sxs-lookup"><span data-stu-id="de5c1-143">Step 1: Examining the Configuration Files</span></span>

<span data-ttu-id="de5c1-144">可根据 3 个 XML 文件在不同级别上配置程序集绑定行为：</span><span class="sxs-lookup"><span data-stu-id="de5c1-144">Assembly binding behavior can be configured at different levels based on three XML files:</span></span>

- <span data-ttu-id="de5c1-145">应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-145">Application configuration file.</span></span>

- <span data-ttu-id="de5c1-146">发布服务器策略文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-146">Publisher policy file.</span></span>

- <span data-ttu-id="de5c1-147">计算机配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-147">Machine configuration file.</span></span>

<span data-ttu-id="de5c1-148">这些文件遵循相同的语法，并提供绑定重定向、代码位置和特定程序集的绑定模式等信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-148">These files follow the same syntax and provide information such as binding redirects, the location of code, and binding modes for particular assemblies.</span></span> <span data-ttu-id="de5c1-149">每个配置文件均可包含用于重定向绑定过程的 [\<assemblyBinding> 元素](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-149">Each configuration file can contain an [\<assemblyBinding> element](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) that redirects the binding process.</span></span> <span data-ttu-id="de5c1-150">[\<assemblyBinding> 元素](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)的子元素包含 [\<dependentAssembly> 元素](../configure-apps/file-schema/runtime/dependentassembly-element.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-150">The child elements of the [\<assemblyBinding> element](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) include the [\<dependentAssembly> element](../configure-apps/file-schema/runtime/dependentassembly-element.md).</span></span> <span data-ttu-id="de5c1-151">[\<dependentAssembly> 元素](../configure-apps/file-schema/runtime/dependentassembly-element.md)的子元素包含 [\<assemblyIdentity> 元素](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)、[\<bindingRedirect> 元素](../configure-apps/file-schema/runtime/bindingredirect-element.md) 和 [\<codeBase> 元素](../configure-apps/file-schema/runtime/codebase-element.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-151">The children of [\<dependentAssembly> element](../configure-apps/file-schema/runtime/dependentassembly-element.md) include the [\<assemblyIdentity> element](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), the [\<bindingRedirect> element](../configure-apps/file-schema/runtime/bindingredirect-element.md), and the [\<codeBase> element](../configure-apps/file-schema/runtime/codebase-element.md).</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-152">这 3 个配置文件中均存在配置信息；并非所有配置文件中的所有元素都有效。</span><span class="sxs-lookup"><span data-stu-id="de5c1-152">Configuration information can be found in the three configuration files; not all elements are valid in all configuration files.</span></span> <span data-ttu-id="de5c1-153">例如，绑定模式和专用路径信息仅存在于应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-153">For example, binding mode and private path information can only be in the application configuration file.</span></span> <span data-ttu-id="de5c1-154">有关包含在每个文件内的完整信息列表，请参阅 [使用配置文件配置应用](../configure-apps/index.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-154">For a complete list of the information that is contained in each file, see [Configuring Apps by Using Configuration Files](../configure-apps/index.md).</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="de5c1-155">应用程序配置文件</span><span class="sxs-lookup"><span data-stu-id="de5c1-155">Application Configuration File</span></span>

<span data-ttu-id="de5c1-156">首先，公共语言运行时检查应用程序配置文件是否存在重写调用程序集清单中存储的版本信息的相关信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-156">First, the common language runtime checks the application configuration file for information that overrides the version information stored in the calling assembly's manifest.</span></span> <span data-ttu-id="de5c1-157">可借助应用程序部署应用程序配置文件，但执行应用程序时不需要此文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-157">The application configuration file can be deployed with an application, but is not required for application execution.</span></span> <span data-ttu-id="de5c1-158">通常几乎可瞬时完成此文件的检索，但如果应用程序基位于完成计算机上（例如，在基于 Internet Explorer Web 的方案中），必须下载配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-158">Usually the retrieval of this file is almost instantaneous, but in situations where the application base is on a remote computer, such as in an Internet Explorer Web-based scenario, the configuration file must be downloaded.</span></span>

<span data-ttu-id="de5c1-159">对于客户端可执行文件，应用程序配置文件和应用程序的可执行文件驻留在同一目录中，并且它与扩展名为 .config 的可执行文件具有相同的基名称。</span><span class="sxs-lookup"><span data-stu-id="de5c1-159">For client executables, the application configuration file resides in the same directory as the application's executable and has the same base name as the executable with a .config extension.</span></span> <span data-ttu-id="de5c1-160">例如，C:\Program Files\Myapp\Myapp.exe 的配置文件是 C:\Program Files\Myapp\Myapp.exe.config。在基于浏览器的方案中，HTML 文件必须使用 \<link> 元素显式指向该配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-160">For example, the configuration file for C:\Program Files\Myapp\Myapp.exe is C:\Program Files\Myapp\Myapp.exe.config. In a browser-based scenario, the HTML file must use the **\<link>** element to explicitly point to the configuration file.</span></span>

<span data-ttu-id="de5c1-161">以下代码提供了一个有关应用程序配置文件的简单示例。</span><span class="sxs-lookup"><span data-stu-id="de5c1-161">The following code provides a simple example of an application configuration file.</span></span> <span data-ttu-id="de5c1-162">此示例将 <xref:System.Diagnostics.TextWriterTraceListener> 添加到 <xref:System.Diagnostics.Debug.Listeners%2A> 集合，以便可以将调试信息记录到文件中。</span><span class="sxs-lookup"><span data-stu-id="de5c1-162">This example adds a <xref:System.Diagnostics.TextWriterTraceListener> to the <xref:System.Diagnostics.Debug.Listeners%2A> collection to enable recording debug information to a file.</span></span>

```xml
<configuration>
   <system.diagnostics>
      <trace useGlobalLock="false" autoflush="true" indentsize="0">
         <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
         </listeners>
      </trace>
   </system.diagnostics>
</configuration>
```

### <a name="publisher-policy-file"></a><span data-ttu-id="de5c1-163">发布服务器策略文件</span><span class="sxs-lookup"><span data-stu-id="de5c1-163">Publisher Policy File</span></span>

<span data-ttu-id="de5c1-164">然后，运行时检查发布服务器策略文件（若存在）。</span><span class="sxs-lookup"><span data-stu-id="de5c1-164">Second, the runtime examines the publisher policy file, if one exists.</span></span> <span data-ttu-id="de5c1-165">组件发布服务器将发布服务器策略文件作为修复文件或更新文件分配至共享组件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-165">Publisher policy files are distributed by a component publisher as a fix or update to a shared component.</span></span> <span data-ttu-id="de5c1-166">这些文件包含共享组件的发布服务器所发布的的兼容性信息，其中此组件将程序集引用定向到新版本。</span><span class="sxs-lookup"><span data-stu-id="de5c1-166">These files contain compatibility information issued by the publisher of the shared component that directs an assembly reference to a new version.</span></span> <span data-ttu-id="de5c1-167">与应用程序和计算机配置文件不同，发布服务器策略文件位于必须在全局程序集缓存中安装的自己的程序集中。</span><span class="sxs-lookup"><span data-stu-id="de5c1-167">Unlike application and machine configuration files, publisher policy files are contained in their own assembly that must be installed in the global assembly cache.</span></span>

<span data-ttu-id="de5c1-168">以下示例阐述了发行者策略配置文件：</span><span class="sxs-lookup"><span data-stu-id="de5c1-168">The following is an example of a Publisher Policy configuration file:</span></span>

```xml
<configuration>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">

            <dependentAssembly>
                <assemblyIdentity name="asm6" publicKeyToken="c0305c36380ba429" />
                <bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0"/>
            </dependentAssembly>

        </assemblyBinding>
    </runtime>
</configuration>
```

<span data-ttu-id="de5c1-169">若要创建程序集，可使用具有如下命令的 [Al.exe（程序集链接器）](../tools/al-exe-assembly-linker.md)工具：</span><span class="sxs-lookup"><span data-stu-id="de5c1-169">To create an assembly, you can use the [Al.exe (Assembly Linker)](../tools/al-exe-assembly-linker.md) tool with a command such as the following:</span></span>

```console
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

<span data-ttu-id="de5c1-170">`compatkey.dat` 是一个强名称密钥文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-170">`compatkey.dat` is a strong-name key file.</span></span> <span data-ttu-id="de5c1-171">此命令创建可置于全局程序集缓存中的强名称程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-171">This command creates a strong-named assembly you can place in the global assembly cache.</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-172">发布服务器策略会影响所有使用共享组件的应用程序。</span><span class="sxs-lookup"><span data-stu-id="de5c1-172">Publisher policy affects all applications that use a shared component.</span></span>

<span data-ttu-id="de5c1-173">发布服务器策略配置文件会重写来自应用程序（即，来自程序集清单或应用程序配置文件）的版本信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-173">The publisher policy configuration file overrides version information that comes from the application (that is, from the assembly manifest or from the application configuration file).</span></span> <span data-ttu-id="de5c1-174">如果应用程序配置文件中不存在重定向程序集清单中指定版本的语句，发布服务器策略文件将重写程序集清单中指定的版本。</span><span class="sxs-lookup"><span data-stu-id="de5c1-174">If there is no statement in the application configuration file to redirect the version specified in the assembly manifest, the publisher policy file overrides the version specified in the assembly manifest.</span></span> <span data-ttu-id="de5c1-175">但是，如果应用程序配置文件中存在重定向语句，发布服务器策略将重写此版本（而不是清单中指定的版本）。</span><span class="sxs-lookup"><span data-stu-id="de5c1-175">However, if there is a redirecting statement in the application configuration file, publisher policy overrides that version rather than the one specified in the manifest.</span></span>

<span data-ttu-id="de5c1-176">共享组件已更新且使用此组件的所有应用程序都应选取共享组件的新版本时，使用发行者策略文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-176">A publisher policy file is used when a shared component is updated and the new version of the shared component should be picked up by all applications using that component.</span></span> <span data-ttu-id="de5c1-177">发布服务器策略文件中的设置会重写应用程序配置文件中的设置，除非应用程序配置文件强制实施了安全模式。</span><span class="sxs-lookup"><span data-stu-id="de5c1-177">The settings in the publisher policy file override settings in the application configuration file, unless the application configuration file enforces safe mode.</span></span>

#### <a name="safe-mode"></a><span data-ttu-id="de5c1-178">安全模式</span><span class="sxs-lookup"><span data-stu-id="de5c1-178">Safe Mode</span></span>
<span data-ttu-id="de5c1-179">发布服务器策略文件通常作为服务包或程序更新的一部分显式安装。</span><span class="sxs-lookup"><span data-stu-id="de5c1-179">Publisher policy files are usually explicitly installed as part of a service pack or program update.</span></span> <span data-ttu-id="de5c1-180">如果升级后的共享组件有任何问题，可使用安全模式忽略发布服务器策略文件中的重写。</span><span class="sxs-lookup"><span data-stu-id="de5c1-180">If there is any problem with the upgraded shared component, you can ignore the overrides in the publisher policy file using safe mode.</span></span> <span data-ttu-id="de5c1-181">安全模式由仅位于应用程序配置文件中的 \<publisherPolicy apply="yes**&#124;**no"/> 元素确定。</span><span class="sxs-lookup"><span data-stu-id="de5c1-181">Safe mode is determined by the **\<publisherPolicy apply="yes**&#124;**no"/>** element, located only in the application configuration file.</span></span> <span data-ttu-id="de5c1-182">它指定是否应从绑定进程删除发布服务器策略配置信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-182">It specifies whether the publisher policy configuration information should be removed from the binding process.</span></span>

<span data-ttu-id="de5c1-183">可针对整个应用程序或所选程序集设置安全模式。</span><span class="sxs-lookup"><span data-stu-id="de5c1-183">Safe mode can be set for the entire application or for selected assemblies.</span></span> <span data-ttu-id="de5c1-184">即，可关闭构成应用程序的所有程序集的策略，也可仅打开部分程序集的策略。</span><span class="sxs-lookup"><span data-stu-id="de5c1-184">That is, you can turn off the policy for all assemblies that make up the application, or turn it on for some assemblies but not others.</span></span> <span data-ttu-id="de5c1-185">若要将发布服务器策略有选择地应用于构成应用程序的程序集，请设置 \<publisherPolicy apply\=no/> 并使用 \<**dependentAssembly**> 元素指定要影响的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-185">To selectively apply publisher policy to assemblies that make up an application, set **\<publisherPolicy apply\=no/>** and specify which assemblies you want to be affected using the \<**dependentAssembly**> element.</span></span> <span data-ttu-id="de5c1-186">若要将发布服务器策略应用于构成应用程序的所有程序集，请设置 \<publisherPolicy apply\=no/>，且不包含从属程序集元素。</span><span class="sxs-lookup"><span data-stu-id="de5c1-186">To apply publisher policy to all assemblies that make up the application, set **\<publisherPolicy apply\=no/>** with no dependent assembly elements.</span></span> <span data-ttu-id="de5c1-187">有关配置的详细信息，请参阅 [使用配置文件配置应用](../configure-apps/index.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-187">For more about configuration, see [Configuring Apps by using Configuration Files](../configure-apps/index.md).</span></span>

### <a name="machine-configuration-file"></a><span data-ttu-id="de5c1-188">计算机配置文件</span><span class="sxs-lookup"><span data-stu-id="de5c1-188">Machine Configuration File</span></span>
<span data-ttu-id="de5c1-189">最后，运行时检查计算机配置文件。</span><span class="sxs-lookup"><span data-stu-id="de5c1-189">Third, the runtime examines the machine configuration file.</span></span> <span data-ttu-id="de5c1-190">此文件名为 Machine.config，驻留在本地计算机上安装有运行时的根目录的配置子目录中。</span><span class="sxs-lookup"><span data-stu-id="de5c1-190">This file, called Machine.config, resides on the local computer in the Config subdirectory of the root directory where the runtime is installed.</span></span> <span data-ttu-id="de5c1-191">管理员可使用此文件来指定此计算机本地的程序集绑定限制。</span><span class="sxs-lookup"><span data-stu-id="de5c1-191">This file can be used by administrators to specify assembly binding restrictions that are local to that computer.</span></span> <span data-ttu-id="de5c1-192">计算机配置文件中的设置优先于所有其他配置设置 ；但是，这并不意味着所有配置设置都应置于此文件中。</span><span class="sxs-lookup"><span data-stu-id="de5c1-192">The settings in the machine configuration file take precedence over all other configuration settings; however, this does not mean that all configuration settings should be put in this file.</span></span> <span data-ttu-id="de5c1-193">管理员策略文件确定的版本为最终版本，且不能重写。</span><span class="sxs-lookup"><span data-stu-id="de5c1-193">The version determined by the administrator policy file is final, and cannot be overridden.</span></span> <span data-ttu-id="de5c1-194">Machine.config 文件中指定的重写可影响所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="de5c1-194">Overrides specified in the Machine.config file affect all applications.</span></span> <span data-ttu-id="de5c1-195">有关配置文件的详细信息，请参阅 [使用配置文件配置应用](../configure-apps/index.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-195">For more information about configuration files, see [Configuring Apps by using Configuration Files](../configure-apps/index.md).</span></span>

<a name="step2"></a>

## <a name="step-2-checking-for-previously-referenced-assemblies"></a><span data-ttu-id="de5c1-196">步骤 2：检查以前引用的程序集</span><span class="sxs-lookup"><span data-stu-id="de5c1-196">Step 2: Checking for Previously Referenced Assemblies</span></span>

<span data-ttu-id="de5c1-197">如果请求的程序集已先前调用中请求过，则公共语言运行时将使用已加载的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-197">If the requested assembly has also been requested in previous calls, the common language runtime uses the assembly that is already loaded.</span></span> <span data-ttu-id="de5c1-198">命名构成应用程序的程序集时，这可能会造成影响。</span><span class="sxs-lookup"><span data-stu-id="de5c1-198">This can have ramifications when naming assemblies that make up an application.</span></span> <span data-ttu-id="de5c1-199">有关命名程序集的详细信息，请参阅 [程序集名称](../../standard/assembly/names.md)。</span><span class="sxs-lookup"><span data-stu-id="de5c1-199">For more information about naming assemblies, see [Assembly Names](../../standard/assembly/names.md).</span></span>

<span data-ttu-id="de5c1-200">如果先前的程序集请求失败，此程序集的后续请求立即失败且不会尝试加载程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-200">If a previous request for the assembly failed, subsequent requests for the assembly are failed immediately without attempting to load the assembly.</span></span> <span data-ttu-id="de5c1-201">从 .NET Framework 2.0 版开始，将缓存程序集绑定故障，且缓存的信息用于确定是否尝试加载此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-201">Starting with the .NET Framework version 2.0, assembly binding failures are cached, and the cached information is used to determine whether to attempt to load the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-202">若要还原到 .NET framework 版本 1.0 和 1.1 的行为（即，不缓存绑定故障），请将 [\<disableCachingBindingFailures> 元素](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)包括到配置文件中。</span><span class="sxs-lookup"><span data-stu-id="de5c1-202">To revert to the behavior of the .NET Framework versions 1.0 and 1.1, which did not cache binding failures, include the [\<disableCachingBindingFailures> Element](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) in your configuration file.</span></span>

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a><span data-ttu-id="de5c1-203">步骤 3：检查全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="de5c1-203">Step 3: Checking the Global Assembly Cache</span></span>

<span data-ttu-id="de5c1-204">对于强名称程序集，通过查看全局程序集缓存继续执行绑定进程。</span><span class="sxs-lookup"><span data-stu-id="de5c1-204">For strong-named assemblies, the binding process continues by looking in the global assembly cache.</span></span> <span data-ttu-id="de5c1-205">全局程序集缓存存储可由同一计算机上多个应用程序使用的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-205">The global assembly cache stores assemblies that can be used by several applications on a computer.</span></span> <span data-ttu-id="de5c1-206">全局程序集缓存中的所有程序集都必须具有强名称。</span><span class="sxs-lookup"><span data-stu-id="de5c1-206">All assemblies in the global assembly cache must have strong names.</span></span>

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a><span data-ttu-id="de5c1-207">步骤 4：通过基本代码或探测定位程序集</span><span class="sxs-lookup"><span data-stu-id="de5c1-207">Step 4: Locating the Assembly through Codebases or Probing</span></span>

<span data-ttu-id="de5c1-208">在通过使用调用程序集引用和配置文件中的信息确定正确的程序集版本，且已在全局程序集缓存中检查此版本（仅针对强名称程序集）之后，公共语言运行时将尝试查找此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-208">After the correct assembly version has been determined by using the information in the calling assembly's reference and in the configuration files, and after it has checked in the global assembly cache (only for strong-named assemblies), the common language runtime attempts to find the assembly.</span></span> <span data-ttu-id="de5c1-209">查找程序集的过程涉及以下步骤：</span><span class="sxs-lookup"><span data-stu-id="de5c1-209">The process of locating an assembly involves the following steps:</span></span>

1. <span data-ttu-id="de5c1-210">如果在应用程序配置文件中找到 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素，则运行时会检查指定的位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-210">If a [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element is found in the application configuration file, the runtime checks the specified location.</span></span> <span data-ttu-id="de5c1-211">如果找到匹配项，则使用此程序集且不执行探测。</span><span class="sxs-lookup"><span data-stu-id="de5c1-211">If a match is found, that assembly is used and no probing occurs.</span></span> <span data-ttu-id="de5c1-212">如果此处不存在程序集，则绑定请求失败。</span><span class="sxs-lookup"><span data-stu-id="de5c1-212">If the assembly is not found there, the binding request fails.</span></span>

2. <span data-ttu-id="de5c1-213">然后，运行时使用本节稍后指定的规则探测引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-213">The runtime then probes for the referenced assembly using the rules specified later in this section.</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-214">如果目录中有多个版本的程序集，并且要引用该程序集的某个特定版本，则必须使用 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素而不是 [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) 元素的 `privatePath` 特性。</span><span class="sxs-lookup"><span data-stu-id="de5c1-214">If you have multiple versions of an assembly in a directory and you want to reference a particular version of that assembly, you must use the [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element instead of the `privatePath` attribute of the [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) element.</span></span> <span data-ttu-id="de5c1-215">如果使用 [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) 元素，则运行时首次找到与引用的简单程序集名称匹配的程序集时，无论此匹配项是否正确，运行时都会停止探测。</span><span class="sxs-lookup"><span data-stu-id="de5c1-215">If you use the [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) element, the runtime stops probing the first time it finds an assembly that matches the simple assembly name referenced, whether it is a correct match or not.</span></span> <span data-ttu-id="de5c1-216">如果此匹配项正确，则使用此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-216">If it is a correct match, that assembly is used.</span></span> <span data-ttu-id="de5c1-217">如果此匹配项不正确，则停止探测且绑定失败。</span><span class="sxs-lookup"><span data-stu-id="de5c1-217">If it is not a correct match, probing stops and binding fails.</span></span>

### <a name="locating-the-assembly-through-codebases"></a><span data-ttu-id="de5c1-218">通过基本代码查找程序集</span><span class="sxs-lookup"><span data-stu-id="de5c1-218">Locating the Assembly through Codebases</span></span>

<span data-ttu-id="de5c1-219">通过使用配置文件中的 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素，可提供基本代码信息。</span><span class="sxs-lookup"><span data-stu-id="de5c1-219">Codebase information can be provided by using a [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element in a configuration file.</span></span> <span data-ttu-id="de5c1-220">在运行时尝试探测引用的程序集之前，始终检查此基本代码。</span><span class="sxs-lookup"><span data-stu-id="de5c1-220">This codebase is always checked before the runtime attempts to probe for the referenced assembly.</span></span> <span data-ttu-id="de5c1-221">如果包含最终版本重定向的发布服务器策略文件也包含 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素，则使用 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="de5c1-221">If a publisher policy file containing the final version redirect also contains a [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element, that [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element is the one that is used.</span></span> <span data-ttu-id="de5c1-222">例如，如果应用程序配置文件指定一个 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素，而重写应用程序信息的发布服务器策略文件也指定一个 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素，则使用发布服务器策略文件中的 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="de5c1-222">For example, if your application configuration file specifies a [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element, and a publisher policy file that is overriding the application information also specifies a [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element, the [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element in the publisher policy file is used.</span></span>

<span data-ttu-id="de5c1-223">如果在 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素指定的位置找不到匹配项，则绑定请求失败，且不再执行任何步骤。</span><span class="sxs-lookup"><span data-stu-id="de5c1-223">If no match is found at the location specified by the [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element, the bind request fails and no further steps are taken.</span></span> <span data-ttu-id="de5c1-224">如果运行时确定程序集与调用程序集的条件相匹配，则使用此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-224">If the runtime determines that an assembly matches the calling assembly's criteria, it uses that assembly.</span></span> <span data-ttu-id="de5c1-225">加载由给定 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素指定的文件时，运行时执行检查，确保名称、版本、区域性和公钥与调用程序集的引用相匹配。</span><span class="sxs-lookup"><span data-stu-id="de5c1-225">When the file specified by the given [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element is loaded, the runtime checks to make sure that the name, version, culture, and public key match the calling assembly's reference.</span></span>

> [!NOTE]
> <span data-ttu-id="de5c1-226">应用程序根目录外的被引用程序集必须具有强名称，并且必须安装在全局程序集缓存中，或者使用 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素指定。</span><span class="sxs-lookup"><span data-stu-id="de5c1-226">Referenced assemblies outside the application's root directory must have strong names and must either be installed in the global assembly cache or specified using the [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>

### <a name="locating-the-assembly-through-probing"></a><span data-ttu-id="de5c1-227">通过探测查找程序集</span><span class="sxs-lookup"><span data-stu-id="de5c1-227">Locating the Assembly through Probing</span></span>

<span data-ttu-id="de5c1-228">如果应用程序配置文件中没有 [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) 元素，则运行时使用以下 4 个条件来探测程序集：</span><span class="sxs-lookup"><span data-stu-id="de5c1-228">If there is no [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element in the application configuration file, the runtime probes for the assembly using four criteria:</span></span>

- <span data-ttu-id="de5c1-229">应用程序基，即正在执行应用程序的根位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-229">Application base, which is the root location where the application is being executed.</span></span>

- <span data-ttu-id="de5c1-230">区域性，即被引用的程序集的区域性属性。</span><span class="sxs-lookup"><span data-stu-id="de5c1-230">Culture, which is the culture attribute of the assembly being referenced.</span></span>

- <span data-ttu-id="de5c1-231">名称，即被引用的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="de5c1-231">Name, which is the name of the referenced assembly.</span></span>

- <span data-ttu-id="de5c1-232">[\<probing>](../configure-apps/file-schema/runtime/probing-element.md) 元素的 `privatePath` 特性，这是根位置下用户定义的子目录列表。</span><span class="sxs-lookup"><span data-stu-id="de5c1-232">The `privatePath` attribute of the [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) element, which is the user-defined list of subdirectories under the root location.</span></span> <span data-ttu-id="de5c1-233">可使用应用程序域的 <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> 属性在应用程序配置文件和托管代码中指定此位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-233">This location can be specified in the application configuration file and in managed code using the <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> property for an application domain.</span></span> <span data-ttu-id="de5c1-234">在托管代码中指定时，先探测托管代码 `privatePath` ，然后探测应用程序配置文件中指定的路径。</span><span class="sxs-lookup"><span data-stu-id="de5c1-234">When specified in managed code, the managed code `privatePath` is probed first, followed by the path specified in the application configuration file.</span></span>

#### <a name="probing-the-application-base-and-culture-directories"></a><span data-ttu-id="de5c1-235">探测应用程序基和区域性目录</span><span class="sxs-lookup"><span data-stu-id="de5c1-235">Probing the Application Base and Culture Directories</span></span>

<span data-ttu-id="de5c1-236">运行时始终先探测应用程序基，它可能是计算机的 URL 或应用程序根目录。</span><span class="sxs-lookup"><span data-stu-id="de5c1-236">The runtime always begins probing in the application's base, which can be either a URL or the application's root directory on a computer.</span></span> <span data-ttu-id="de5c1-237">如果应用程序基中不存在引用的程序集且未提供区域性信息，则运行时将搜索具有程序集名称的所有子目录。</span><span class="sxs-lookup"><span data-stu-id="de5c1-237">If the referenced assembly is not found in the application base and no culture information is provided, the runtime searches any subdirectories with the assembly name.</span></span> <span data-ttu-id="de5c1-238">探测的目录包括：</span><span class="sxs-lookup"><span data-stu-id="de5c1-238">The directories probed include:</span></span>

- <span data-ttu-id="de5c1-239">[application base] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-239">[application base] / [assembly name].dll</span></span>

- <span data-ttu-id="de5c1-240">[application base] / [assembly name] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-240">[application base] / [assembly name] / [assembly name].dll</span></span>

<span data-ttu-id="de5c1-241">如果指定了被引用程序集的区域性信息，则只探测以下目录：</span><span class="sxs-lookup"><span data-stu-id="de5c1-241">If culture information is specified for the referenced assembly, only the following directories are probed:</span></span>

- <span data-ttu-id="de5c1-242">[application base] / [culture] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-242">[application base] / [culture] / [assembly name].dll</span></span>

- <span data-ttu-id="de5c1-243">[application base] / [culture] / [assembly name] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-243">[application base] / [culture] / [assembly name] / [assembly name].dll</span></span>

#### <a name="probing-with-the-privatepath-attribute"></a><span data-ttu-id="de5c1-244">用 privatePath 属性进行探测</span><span class="sxs-lookup"><span data-stu-id="de5c1-244">Probing with the privatePath Attribute</span></span>

<span data-ttu-id="de5c1-245">除区域性子目录和为被引用程序集指定的子目录外，运行时还探测使用 [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) 元素的 `privatePath` 特性指定的目录。</span><span class="sxs-lookup"><span data-stu-id="de5c1-245">In addition to the culture subdirectories and the subdirectories named for the referenced assembly, the runtime also probes directories specified using the `privatePath` attribute of the [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) element.</span></span> <span data-ttu-id="de5c1-246">使用 `privatePath` 属性指定的目录必须是应用程序根目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="de5c1-246">The directories specified using the `privatePath` attribute must be subdirectories of the application's root directory.</span></span> <span data-ttu-id="de5c1-247">根据引用的程序集请求中是否包含区域性信息，探测的目录会所有不同。</span><span class="sxs-lookup"><span data-stu-id="de5c1-247">The directories probed vary depending on whether culture information is included in the referenced assembly request.</span></span>

<span data-ttu-id="de5c1-248">在运行时首次找到与引用的简单程序集名称相匹配的程序集时，无论此匹配项是否正确，运行时都将停止探测。</span><span class="sxs-lookup"><span data-stu-id="de5c1-248">The runtime stops probing the first time it finds an assembly that matches the simple assembly name referenced, whether it is a correct match or not.</span></span> <span data-ttu-id="de5c1-249">如果此匹配项正确，则使用此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-249">If it is a correct match, that assembly is used.</span></span> <span data-ttu-id="de5c1-250">如果此匹配项不正确，则停止探测且绑定失败。</span><span class="sxs-lookup"><span data-stu-id="de5c1-250">If it is not a correct match, probing stops and binding fails.</span></span>

<span data-ttu-id="de5c1-251">如果包括区域性，则探测以下目录：</span><span class="sxs-lookup"><span data-stu-id="de5c1-251">If culture is included, the following directories are probed:</span></span>

- <span data-ttu-id="de5c1-252">[application base] / [binpath] / [culture] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-252">[application base] / [binpath] / [culture] / [assembly name].dll</span></span>

- <span data-ttu-id="de5c1-253">[application base] / [binpath] / [culture] / [assembly name] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-253">[application base] / [binpath] / [culture] / [assembly name] / [assembly name].dll</span></span>

<span data-ttu-id="de5c1-254">如果不包括区域性信息，则探测以下目录：</span><span class="sxs-lookup"><span data-stu-id="de5c1-254">If culture information is not included, the following directories are probed:</span></span>

- <span data-ttu-id="de5c1-255">[application base] / [binpath] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-255">[application base] / [binpath] / [assembly name].dll</span></span>

- <span data-ttu-id="de5c1-256">[application base] / [binpath] / [assembly name] / [assembly name].dll</span><span class="sxs-lookup"><span data-stu-id="de5c1-256">[application base] / [binpath] / [assembly name] / [assembly name].dll</span></span>

#### <a name="probing-examples"></a><span data-ttu-id="de5c1-257">探测示例</span><span class="sxs-lookup"><span data-stu-id="de5c1-257">Probing Examples</span></span>

<span data-ttu-id="de5c1-258">给定以下信息：</span><span class="sxs-lookup"><span data-stu-id="de5c1-258">Given the following information:</span></span>

- <span data-ttu-id="de5c1-259">引用的程序集名称：myAssembly</span><span class="sxs-lookup"><span data-stu-id="de5c1-259">Referenced assembly name: myAssembly</span></span>

- <span data-ttu-id="de5c1-260">应用程序根目录：`http://www.code.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="de5c1-260">Application root directory: `http://www.code.microsoft.com`</span></span>

- <span data-ttu-id="de5c1-261">配置文件中的 [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) 元素指定：bin</span><span class="sxs-lookup"><span data-stu-id="de5c1-261">[\<probing>](../configure-apps/file-schema/runtime/probing-element.md) element in configuration file specifies: bin</span></span>

- <span data-ttu-id="de5c1-262">区域性：de</span><span class="sxs-lookup"><span data-stu-id="de5c1-262">Culture: de</span></span>

<span data-ttu-id="de5c1-263">运行时探测以下 URL：</span><span class="sxs-lookup"><span data-stu-id="de5c1-263">The runtime probes the following URLs:</span></span>

- `http://www.code.microsoft.com/de/myAssembly.dll`

- `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`

##### <a name="multiple-assemblies-with-the-same-name"></a><span data-ttu-id="de5c1-264">具有相同名称的多个程序集</span><span class="sxs-lookup"><span data-stu-id="de5c1-264">Multiple Assemblies with the Same Name</span></span>

<span data-ttu-id="de5c1-265">以下示例显示了如何配置具有相同名称的多个程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-265">The following example shows how to configure multiple assemblies with the same name.</span></span>

```xml
<dependentAssembly>
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />
   <codeBase version="1.0.0.0" href="v1/Server.dll" />
   <codeBase version="2.0.0.0" href="v2/Server.dll" />
</dependentAssembly>
```

#### <a name="other-locations-probed"></a><span data-ttu-id="de5c1-266">探测的其他位置</span><span class="sxs-lookup"><span data-stu-id="de5c1-266">Other Locations Probed</span></span>

<span data-ttu-id="de5c1-267">还可使用当前的绑定上下文来确定程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-267">Assembly location can also be determined using the current binding context.</span></span> <span data-ttu-id="de5c1-268">在 COM 互操作方案中使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 方法时，最常使用此操作。</span><span class="sxs-lookup"><span data-stu-id="de5c1-268">This most often occurs when the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method is used and in COM interop scenarios.</span></span> <span data-ttu-id="de5c1-269">如果某个程序集使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法引用其他程序集，调用程序集的位置被视为可提示引用的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-269">If an assembly uses the <xref:System.Reflection.Assembly.LoadFrom%2A> method to reference another assembly, the calling assembly's location is considered to be a hint about where to find the referenced assembly.</span></span> <span data-ttu-id="de5c1-270">如果找到匹配项，则加载此程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-270">If a match is found, that assembly is loaded.</span></span> <span data-ttu-id="de5c1-271">如果未找到匹配项，则运行时将继续执行搜索语义，然后查询 Windows Installer 以提供程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-271">If no match is found, the runtime continues with its search semantics and then queries the Windows Installer to provide the assembly.</span></span> <span data-ttu-id="de5c1-272">如果未提供与绑定请求匹配的程序集，则将引发异常。</span><span class="sxs-lookup"><span data-stu-id="de5c1-272">If no assembly is provided that matches the binding request, an exception is thrown.</span></span> <span data-ttu-id="de5c1-273">如果引用了类型，则此异常为托管代码中的 <xref:System.TypeLoadException> 如果找不到正在加载的程序集，则为 <xref:System.IO.FileNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="de5c1-273">This exception is a <xref:System.TypeLoadException> in managed code if a type was referenced, or a <xref:System.IO.FileNotFoundException> if an assembly being loaded was not found.</span></span>

<span data-ttu-id="de5c1-274">例如，如果 Assembly1 引用 Assembly2 且 Assembly1 是从 `http://www.code.microsoft.com/utils` 下载的，则此位置被视为可提示 Assembly2.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="de5c1-274">For example, if Assembly1 references Assembly2 and Assembly1 was downloaded from `http://www.code.microsoft.com/utils`, that location is considered to be a hint about where to find Assembly2.dll.</span></span> <span data-ttu-id="de5c1-275">然后运行时会在 `http://www.code.microsoft.com/utils/Assembly2.dll` 和 `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll` 中探测程序集。</span><span class="sxs-lookup"><span data-stu-id="de5c1-275">The runtime then probes for the assembly in `http://www.code.microsoft.com/utils/Assembly2.dll` and `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`.</span></span> <span data-ttu-id="de5c1-276">如果在这两个位置中均未找到 Assembly2，则运行时将查询 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="de5c1-276">If Assembly2 is not found at either of those locations, the runtime queries the Windows Installer.</span></span>

## <a name="see-also"></a><span data-ttu-id="de5c1-277">请参阅</span><span class="sxs-lookup"><span data-stu-id="de5c1-277">See also</span></span>

- [<span data-ttu-id="de5c1-278">适用于程序集加载的最佳做法</span><span class="sxs-lookup"><span data-stu-id="de5c1-278">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)
- [<span data-ttu-id="de5c1-279">部署</span><span class="sxs-lookup"><span data-stu-id="de5c1-279">Deployment</span></span>](index.md)
