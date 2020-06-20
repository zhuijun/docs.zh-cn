---
title: 如何：创建发行者策略
description: 了解程序集供应商如何在 .NET 中使用升级的程序集创建发行者策略文件，以规定应用程序应使用较新版本。
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 23e9d8144ec5742e0371d566b7af59dc9dd30c9b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105403"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="38e6d-103">如何：创建发行者策略</span><span class="sxs-lookup"><span data-stu-id="38e6d-103">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="38e6d-104">程序集的供应商可以通过包括发布服务器策略文件和已升级的程序集，指出应用程序应使用较新版本的程序集。</span><span class="sxs-lookup"><span data-stu-id="38e6d-104">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="38e6d-105">发行者策略文件指定程序集重定向和基本代码设置，并使用与应用程序配置文件相同的格式。</span><span class="sxs-lookup"><span data-stu-id="38e6d-105">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="38e6d-106">发行者策略文件编译到一个程序集中并置于全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="38e6d-106">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="38e6d-107">创建发布者策略涉及三个步骤：</span><span class="sxs-lookup"><span data-stu-id="38e6d-107">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="38e6d-108">创建发布者策略文件。</span><span class="sxs-lookup"><span data-stu-id="38e6d-108">Create a publisher policy file.</span></span>

2. <span data-ttu-id="38e6d-109">创建发行者策略程序集。</span><span class="sxs-lookup"><span data-stu-id="38e6d-109">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="38e6d-110">将发行者策略程序集添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="38e6d-110">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="38e6d-111">[重定向程序集版本](redirect-assembly-versions.md)中介绍了发行者策略的架构。</span><span class="sxs-lookup"><span data-stu-id="38e6d-111">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="38e6d-112">下面的示例演示一个发行者策略文件，该文件将的一个版本重定向 `myAssembly` 到另一个版本。</span><span class="sxs-lookup"><span data-stu-id="38e6d-112">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="38e6d-113">若要了解如何指定基本代码，请参阅[指定程序集的位置](specify-assembly-location.md)。</span><span class="sxs-lookup"><span data-stu-id="38e6d-113">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="38e6d-114">创建发行者策略程序集</span><span class="sxs-lookup"><span data-stu-id="38e6d-114">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="38e6d-115">使用[程序集链接器（Al.exe）](../tools/al-exe-assembly-linker.md)创建发行者策略程序集。</span><span class="sxs-lookup"><span data-stu-id="38e6d-115">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="38e6d-116">创建发行者策略程序集</span><span class="sxs-lookup"><span data-stu-id="38e6d-116">To create a publisher policy assembly</span></span>

<span data-ttu-id="38e6d-117">在命令提示符处键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="38e6d-117">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="38e6d-118">在此命令中：</span><span class="sxs-lookup"><span data-stu-id="38e6d-118">In this command:</span></span>

- <span data-ttu-id="38e6d-119">`publisherPolicyFile`参数是发行者策略文件的名称。</span><span class="sxs-lookup"><span data-stu-id="38e6d-119">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="38e6d-120">`publisherPolicyAssemblyFile`自变量是此命令生成的发行者策略程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="38e6d-120">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="38e6d-121">程序集文件名必须采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="38e6d-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="38e6d-122">"policy.majorNumber.minorNumber.mainAssemblyName.dll"</span><span class="sxs-lookup"><span data-stu-id="38e6d-122">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="38e6d-123">`keyPairFile`参数是包含密钥对的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="38e6d-123">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="38e6d-124">必须用相同的密钥对对程序集和发行者策略程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="38e6d-124">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="38e6d-125">`processorArchitecture`参数标识特定于处理器的程序集的目标平台。</span><span class="sxs-lookup"><span data-stu-id="38e6d-125">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="38e6d-126">从 .NET Framework 2.0 开始，可以获得特定处理器体系结构的目标功能。</span><span class="sxs-lookup"><span data-stu-id="38e6d-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="38e6d-127">从 .NET Framework 2.0 开始，可以获得特定处理器体系结构的目标功能。</span><span class="sxs-lookup"><span data-stu-id="38e6d-127">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="38e6d-128">下面的命令从名为的发行者策略文件中创建一个名为的发行者策略程序集 `policy.1.0.myAssembly` `pub.config` ，使用该文件中的密钥对向程序集分配一个强名称 `sgKey.snk` ，并指定该程序集面向 x86 处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="38e6d-128">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="38e6d-129">发行者策略程序集必须与它所应用到的程序集的处理器体系结构匹配。</span><span class="sxs-lookup"><span data-stu-id="38e6d-129">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="38e6d-130">因此，如果程序集的 <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> 值为 <xref:System.Reflection.ProcessorArchitecture.MSIL> ，则该程序集的发行者策略程序集必须使用创建 `/platform:anycpu` 。</span><span class="sxs-lookup"><span data-stu-id="38e6d-130">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="38e6d-131">必须为每个处理器特定的程序集提供单独的发行者策略程序集。</span><span class="sxs-lookup"><span data-stu-id="38e6d-131">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="38e6d-132">此规则的结果是，若要更改程序集的处理器体系结构，必须更改版本号的主要或次要组件，以便可以使用正确的处理器体系结构提供新的发行者策略程序集。</span><span class="sxs-lookup"><span data-stu-id="38e6d-132">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="38e6d-133">如果程序集具有不同的处理器体系结构，则旧的发行者策略程序集无法为程序集提供服务。</span><span class="sxs-lookup"><span data-stu-id="38e6d-133">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="38e6d-134">另一个结果是版本2.0 链接器无法用于为使用早期版本的 .NET Framework 编译的程序集创建发行者策略程序集，因为它始终指定处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="38e6d-134">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="38e6d-135">将发行者策略程序集添加到全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="38e6d-135">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="38e6d-136">使用[全局程序集缓存工具（Gacutil.exe）](../tools/gacutil-exe-gac-tool.md)将发行者策略程序集添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="38e6d-136">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="38e6d-137">将发行者策略程序集添加到全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="38e6d-137">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="38e6d-138">在命令提示符处键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="38e6d-138">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="38e6d-139">下面的命令将添加 `policy.1.0.myAssembly.dll` 到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="38e6d-139">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="38e6d-140">发行者策略程序集不能添加到全局程序集缓存中，除非在该参数中指定的原始发布服务器策略文件与 `/link` 程序集位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="38e6d-140">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="38e6d-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="38e6d-141">See also</span></span>

- [<span data-ttu-id="38e6d-142">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="38e6d-142">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="38e6d-143">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="38e6d-143">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="38e6d-144">使用配置文件配置应用</span><span class="sxs-lookup"><span data-stu-id="38e6d-144">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="38e6d-145">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="38e6d-145">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="38e6d-146">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="38e6d-146">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="38e6d-147">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="38e6d-147">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
