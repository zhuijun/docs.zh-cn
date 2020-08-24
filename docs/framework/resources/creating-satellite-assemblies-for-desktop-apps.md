---
title: 创建桌面应用程序的附属程序集
description: 开始创建桌面应用的附属程序集。 可以轻松更新或替换附属程序集以提供本地化资源。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
ms.openlocfilehash: 3e515028919518cb93cdbec3417eef061a512832
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558408"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="e59d9-104">创建桌面应用程序的附属程序集</span><span class="sxs-lookup"><span data-stu-id="e59d9-104">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="e59d9-105">资源文件在本地化的应用程序中具有核心作用。</span><span class="sxs-lookup"><span data-stu-id="e59d9-105">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="e59d9-106">通过资源文件，应用程序可以使用用户自己的语言和区域性显示字符串、图像及其他数据，并且在用户自己的语言或区域性资源不可用时，提供备用数据。</span><span class="sxs-lookup"><span data-stu-id="e59d9-106">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="e59d9-107">.NET Framework 使用中心辐射型模型来查找和检索已本地化的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-107">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="e59d9-108">中心即主程序集，包含不可本地化的可执行代码和单个区域性（称作非特定区域性或默认区域性）的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-108">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="e59d9-109">默认区域性是应用程序的回退区域性；没有任何已本地化的资源可用时，则使用默认区域性。</span><span class="sxs-lookup"><span data-stu-id="e59d9-109">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="e59d9-110">使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 属性来指定应用程序默认区域性的区域性。</span><span class="sxs-lookup"><span data-stu-id="e59d9-110">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="e59d9-111">每条轮辐均连接到一个附属程序集，该附属程序集包含单个本地化区域性的资源，但不包含任何代码。</span><span class="sxs-lookup"><span data-stu-id="e59d9-111">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="e59d9-112">因为附属程序集不是主程序集的一部分，所以不必替换该应用程序的主程序集即可轻松更新或替换与特定区域性相对应的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-112">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="e59d9-113">应用程序默认区域性的资源也可以存储在附属程序集中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-113">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="e59d9-114">为此，可为 <xref:System.Resources.NeutralResourcesLanguageAttribute> 属性分配一个 <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="e59d9-114">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="e59d9-115">附属程序集名称和位置</span><span class="sxs-lookup"><span data-stu-id="e59d9-115">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="e59d9-116">中心辐射型模型要求将资源放在特定位置，以便轻松查找和使用资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-116">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="e59d9-117">如果未按预期编译和命名资源，或未将其放在正确的位置，则公共语言运行时将无法定位它们，并改为使用默认区域性的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-117">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="e59d9-118">.NET Framework 资源管理器由 <xref:System.Resources.ResourceManager> 对象表示，用于自动访问本地化的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-118">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="e59d9-119">该资源管理器的相关要求如下：</span><span class="sxs-lookup"><span data-stu-id="e59d9-119">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="e59d9-120">单个附属程序集必须包含特定区域性的所有资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-120">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="e59d9-121">换言之，应该将多个 .txt  或 .resx  文件编译成单个二进制 .resources  文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-121">In other words, you should compile multiple *.txt* or *.resx* files into a single binary *.resources* file.</span></span>

- <span data-ttu-id="e59d9-122">存储区域性资源的每个本地化区域性的应用程序目录中必须有一个单独的子目录。</span><span class="sxs-lookup"><span data-stu-id="e59d9-122">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="e59d9-123">该子目录名称必须与区域性名称相同。</span><span class="sxs-lookup"><span data-stu-id="e59d9-123">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="e59d9-124">或者，也可以将附属程序集存储在全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-124">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="e59d9-125">在这种情况下，程序集强名称的区域性信息组件必须指明其区域性。</span><span class="sxs-lookup"><span data-stu-id="e59d9-125">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="e59d9-126">（请参阅本主题后面的[在全局程序集缓存中安装附属程序集](#SN)部分。）</span><span class="sxs-lookup"><span data-stu-id="e59d9-126">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="e59d9-127">如果应用程序中包含了子区域性的资源，则将每个子区域性放在应用程序目录下的单独子目录中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-127">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="e59d9-128">不要将子区域性放在其主区域性目录下的子目录中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-128">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="e59d9-129">附属程序集的名称必须与应用程序相同，并且必须使用文件扩展名“.resources.dll”。</span><span class="sxs-lookup"><span data-stu-id="e59d9-129">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="e59d9-130">例如，如果应用程序名为 Example.exe  ，则每个附属程序集的名称应该为 Example.resources.dll  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-130">For example, if an application is named *Example.exe*, the name of each satellite assembly should be *Example.resources.dll*.</span></span> <span data-ttu-id="e59d9-131">请注意附属程序集名称不指示其资源文件的区域性。</span><span class="sxs-lookup"><span data-stu-id="e59d9-131">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="e59d9-132">但是，附属程序集会显示在不指定区域性的目录中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-132">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="e59d9-133">附属程序集的区域性的相关信息必须包括在程序集的元数据中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-133">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="e59d9-134">若要将区域性名称存储在附属程序集的元数据中，则在使用[程序集链接器](../tools/al-exe-assembly-linker.md)将资源嵌入附属程序集时指定 `/culture` 选项。</span><span class="sxs-lookup"><span data-stu-id="e59d9-134">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="e59d9-135">下图显示未安装在[全局程序集缓存](../app-domains/gac.md)中的应用程序的示例目录结构和位置要求。</span><span class="sxs-lookup"><span data-stu-id="e59d9-135">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../app-domains/gac.md).</span></span> <span data-ttu-id="e59d9-136">具有 .txt 和 .resources 扩展名的项不会随附在最终应用程序中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-136">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="e59d9-137">这些是用于创建最终附属资源程序集的中间资源文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-137">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="e59d9-138">在此示例中，可以将 .txt 文件替换为 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-138">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="e59d9-139">有关详细信息，请参阅[打包和部署资源](packaging-and-deploying-resources-in-desktop-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d9-139">For more information, see [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="e59d9-140">下图展示了附属程序集目录：</span><span class="sxs-lookup"><span data-stu-id="e59d9-140">The following image shows the satellite assembly directory:</span></span>

![包含本地化区域性子目录的附属程序集目录。](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="e59d9-142">编译附属程序集</span><span class="sxs-lookup"><span data-stu-id="e59d9-142">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="e59d9-143">使用[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 将包含资源的文本文件或 XML (.resx  ) 文件编译为二进制 .resources  文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-143">You use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to compile text files or XML (*.resx*) files that contain resources to binary *.resources* files.</span></span> <span data-ttu-id="e59d9-144">然后使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 将 .resources  文件编译到附属程序集中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-144">You then use [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile *.resources* files into satellite assemblies.</span></span> <span data-ttu-id="e59d9-145">Al.exe  从指定的 .resources  文件创建程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-145">*Al.exe* creates an assembly from the *.resources* files that you specify.</span></span> <span data-ttu-id="e59d9-146">附属程序集只能包含资源，而不能包含任何可执行代码。</span><span class="sxs-lookup"><span data-stu-id="e59d9-146">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="e59d9-147">下面的 Al.exe  命令从德语资源文件 strings.de.resources  为 `Example` 应用程序创建了一个附属程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-147">The following *Al.exe* command creates a satellite assembly for the application `Example` from the German resources file *strings.de.resources*.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="e59d9-148">下面的 Al.exe  命令也从文件 strings.de.resources  为 `Example` 应用程序创建了一个附属程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-148">The following *Al.exe* command also creates a satellite assembly for the application `Example` from the file *strings.de.resources*.</span></span> <span data-ttu-id="e59d9-149">/Template  选项会导致附属程序集从父程序集 (Example.dll  ) 继承除区域性信息之外的所有程序集元数据。</span><span class="sxs-lookup"><span data-stu-id="e59d9-149">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (*Example.dll*).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
<span data-ttu-id="e59d9-150">下表详细展示了这些命令中使用的 Al.exe  选项：</span><span class="sxs-lookup"><span data-stu-id="e59d9-150">The following table describes the *Al.exe* options used in these commands in more detail:</span></span>
  
|<span data-ttu-id="e59d9-151">选项</span><span class="sxs-lookup"><span data-stu-id="e59d9-151">Option</span></span>|<span data-ttu-id="e59d9-152">描述</span><span class="sxs-lookup"><span data-stu-id="e59d9-152">Description</span></span>|
|------------|-----------------|
|`-target:lib`|<span data-ttu-id="e59d9-153">指定将附属程序集编译成库 (.dll) 文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-153">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="e59d9-154">因为附属程序集不包含可执行代码，并且不是应用程序的主程序集，所以必须将附属程序集另存为 DLL。</span><span class="sxs-lookup"><span data-stu-id="e59d9-154">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|`-embed:strings.de.resources`|<span data-ttu-id="e59d9-155">指定在 Al.exe  编译程序集时要嵌入的资源文件名。</span><span class="sxs-lookup"><span data-stu-id="e59d9-155">Specifies the name of the resource file to embed when *Al.exe* compiles the assembly.</span></span> <span data-ttu-id="e59d9-156">可在附属程序集中嵌入多个 .resources 文件，但如果依循中心辐射模型，则必须为每个区域性编译一个附属程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-156">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="e59d9-157">但是，可以为字符串和对象创建单独的 .resources 文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-157">However, you can create separate .resources files for strings and objects.</span></span>|
|`-culture:de`|<span data-ttu-id="e59d9-158">指定要编译的资源的区域性。</span><span class="sxs-lookup"><span data-stu-id="e59d9-158">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="e59d9-159">公共语言运行时搜索特定区域性的资源时会使用此信息。</span><span class="sxs-lookup"><span data-stu-id="e59d9-159">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="e59d9-160">如果省略此选项，Al.exe  仍然会编译资源，但当用户请求资源时，运行时将无法找到该资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-160">If you omit this option, *Al.exe* will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|`-out:Example.resources.dll`|<span data-ttu-id="e59d9-161">指定输出文件的名称。</span><span class="sxs-lookup"><span data-stu-id="e59d9-161">Specifies the name of the output file.</span></span> <span data-ttu-id="e59d9-162">名称必须遵循命名标准 baseName.resources.extension，其中 baseName 是主程序集的名称，extension 是有效的文件扩展名（例如 .dll）     。</span><span class="sxs-lookup"><span data-stu-id="e59d9-162">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="e59d9-163">请注意，运行时无法根据输出文件名确定附属程序集的区域性，必须使用 /culture 选项指定  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-163">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|`-template:Example.dll`|<span data-ttu-id="e59d9-164">指定程序集，附属程序集将从该程序集继承除区域性字段之外的所有程序集元数据。</span><span class="sxs-lookup"><span data-stu-id="e59d9-164">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="e59d9-165">仅当指定了具有[强名称](../../standard/assembly/strong-named.md)的程序集时，此选项才会影响附属程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-165">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../standard/assembly/strong-named.md).</span></span>|
  
 <span data-ttu-id="e59d9-166">有关 Al.exe  可用选项的完整列表，请参阅[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d9-166">For a complete list of options available with *Al.exe*, see [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="e59d9-167">附属程序集：示例</span><span class="sxs-lookup"><span data-stu-id="e59d9-167">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="e59d9-168">下面是一个简单的“Hello world”示例，该示例展示了一个包含本地化的问候语的消息框。</span><span class="sxs-lookup"><span data-stu-id="e59d9-168">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="e59d9-169">此示例包含了英语（美国）、法语（法国）和俄语（俄罗斯）区域性的资源，并且其回退区域性为英语。</span><span class="sxs-lookup"><span data-stu-id="e59d9-169">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="e59d9-170">要创建示例，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e59d9-170">To create the example, do the following:</span></span>
  
1. <span data-ttu-id="e59d9-171">创建一个名为 Greeting.resx  或 Greeting.txt  的资源文件，使其包含默认区域性的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-171">Create a resource file named *Greeting.resx* or *Greeting.txt* to contain the resource for the default culture.</span></span> <span data-ttu-id="e59d9-172">在此文件中存储一个名为 `HelloString`，并且值为“Hello world!”的</span><span class="sxs-lookup"><span data-stu-id="e59d9-172">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="e59d9-173">单个字符串。</span><span class="sxs-lookup"><span data-stu-id="e59d9-173">in this file.</span></span>

2. <span data-ttu-id="e59d9-174">为指示英语 (en) 是该应用程序的默认区域性，请将以下 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> 属性添加到应用程序的 AssemblyInfo 文件或主源代码文件中，该文件之后会编译到应用程序的主程序集中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-174">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    ```csharp
    [assembly: NeutralResourcesLanguageAttribute("en")]
    ```

    ```vb
    <Assembly: NeutralResourcesLanguageAttribute("en")>
    ```
  
3. <span data-ttu-id="e59d9-175">向应用程序添加对其他区域性的支持（en-US、fr-FR 和 ru-RU），如下所示：</span><span class="sxs-lookup"><span data-stu-id="e59d9-175">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    - <span data-ttu-id="e59d9-176">若要支持 en-US 或英语（美国）区域性，创建一个名为 Greeting.en-US.resx  或 Greeting.en-US.txt  的资源文件，并在其中存储一个名为 `HelloString` 且值为“Hi world!”的单个字符串。</span><span class="sxs-lookup"><span data-stu-id="e59d9-176">To support the en-US or English (United States) culture, create a resource file named *Greeting.en-US.resx* or *Greeting.en-US.txt*, and store in it a single string named `HelloString` whose value is "Hi world!".</span></span>
  
    - <span data-ttu-id="e59d9-177">若要支持 fr-FR 或法语（法国）区域性，创建一个名为 Greeting.fr-FR.resx  或 Greeting.fr-FR.txt  的资源文件，并在其中存储一个名为 `HelloString` 且值为“Salut tout le monde!”的单字符串。</span><span class="sxs-lookup"><span data-stu-id="e59d9-177">To support the fr-FR or French (France) culture, create a resource file named *Greeting.fr-FR.resx* or *Greeting.fr-FR.txt*, and store in it a single string named `HelloString` whose value is "Salut tout le monde!".</span></span>
  
    - <span data-ttu-id="e59d9-178">若要支持 ru-RU 或俄语（俄罗斯）区域性，创建一个名为 Greeting.ru-RU.resx  或 Greeting.ru-RU.txt  的资源文件，并在其中存储一个名为 `HelloString` 且值为“Всем привет!”的单字符串。</span><span class="sxs-lookup"><span data-stu-id="e59d9-178">To support the ru-RU or Russian (Russia) culture, create a resource file named *Greeting.ru-RU.resx* or *Greeting.ru-RU.txt*, and store in it a single string named `HelloString` whose value is "Всем привет!".</span></span>
  
4. <span data-ttu-id="e59d9-179">使用 [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) 将每个文本文件或 XML 资源文件编译为二进制 .resources  文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-179">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary *.resources* file.</span></span> <span data-ttu-id="e59d9-180">其输出是一组与 .resx  或 .txt  文件具有相同根文件名的文件，这些文件的扩展名为 .resources  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-180">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="e59d9-181">如果使用 Visual Studio 创建该示例，将自动处理编译过程。</span><span class="sxs-lookup"><span data-stu-id="e59d9-181">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="e59d9-182">如果不使用 Visual Studio，则运行以下命令将 .resx  文件编译为 .resources  文件：</span><span class="sxs-lookup"><span data-stu-id="e59d9-182">If you aren't using Visual Studio, run the following commands to compile the *.resx* files into *.resources* files:</span></span>  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="e59d9-183">如果资源位于文本文件而非 XML 文件中，则将 .resx  扩展名替换为 .txt  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-183">If your resources are in text files instead of XML files, replace the *.resx* extension with *.txt*.</span></span>

5. <span data-ttu-id="e59d9-184">将以下源代码和默认区域性的资源编译到应用程序的主程序集中：</span><span class="sxs-lookup"><span data-stu-id="e59d9-184">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e59d9-185">如果使用的是命令行而不是 Visual Studio 来创建此示例，则应将对 <xref:System.Resources.ResourceManager> 类构造函数的调用修改为后列内容：`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="e59d9-185">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="e59d9-186">如果应用程序名为 Example，并从命令行进行编译，则适用于 C# 编译器的命令为：</span><span class="sxs-lookup"><span data-stu-id="e59d9-186">If the application is named Example and you are compiling from the command-line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="e59d9-187">相应的 Visual Basic 编译器命令为：</span><span class="sxs-lookup"><span data-stu-id="e59d9-187">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="e59d9-188">在主应用程序目录中为应用程序支持的每个本地化的区域性创建一个子目录。</span><span class="sxs-lookup"><span data-stu-id="e59d9-188">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="e59d9-189">应该创建一个 en-US、fr-FR 和 ru-RU 子目录    。</span><span class="sxs-lookup"><span data-stu-id="e59d9-189">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="e59d9-190">Visual Studio 将在编译过程中自动创建这些子目录。</span><span class="sxs-lookup"><span data-stu-id="e59d9-190">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="e59d9-191">将某个区域性特定的 .resources 文件嵌入附属程序集，并将其保存到相应的目录  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-191">Embed the individual culture-specific *.resources* files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="e59d9-192">用于为每个 .resources 文件执行此操作的命令是  ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-192">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     <span data-ttu-id="e59d9-193">其中 culture 是由附属程序集包含了资源的区域性的名称  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-193">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="e59d9-194">Visual Studio 会自动处理这一过程。</span><span class="sxs-lookup"><span data-stu-id="e59d9-194">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="e59d9-195">然后便可运行该示例。</span><span class="sxs-lookup"><span data-stu-id="e59d9-195">You can then run the example.</span></span> <span data-ttu-id="e59d9-196">它会随机将某种支持的区域性设为当前区域性，并显示本地化的问候语。</span><span class="sxs-lookup"><span data-stu-id="e59d9-196">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="e59d9-197">在全局程序集缓存中安装附属程序集</span><span class="sxs-lookup"><span data-stu-id="e59d9-197">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="e59d9-198">可以在全局程序集缓存（而不是本地应用程序子目录）中安装程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-198">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="e59d9-199">当具有供多个应用程序使用的类库和类库资源程序集时，这种方式非常有用。</span><span class="sxs-lookup"><span data-stu-id="e59d9-199">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>
  
<span data-ttu-id="e59d9-200">在全局程序集缓存中安装程序集要求程序集具有强名称。</span><span class="sxs-lookup"><span data-stu-id="e59d9-200">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="e59d9-201">具有强名称的程序集使用有效公钥/私钥对进行签名。</span><span class="sxs-lookup"><span data-stu-id="e59d9-201">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="e59d9-202">它们包含版本信息，运行时会使用这些版本信息来确定使用哪个程序集来满足绑定要求。</span><span class="sxs-lookup"><span data-stu-id="e59d9-202">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="e59d9-203">有关强名称和版本控制的详细信息，请参阅[程序集版本控制](../../standard/assembly/versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d9-203">For more information about strong names and versioning, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span> <span data-ttu-id="e59d9-204">有关强名称的详细信息，请参阅[具有强名称的程序集](../../standard/assembly/strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d9-204">For more information about strong names, see [Strong-Named Assemblies](../../standard/assembly/strong-named.md).</span></span>

<span data-ttu-id="e59d9-205">开发应用程序时，不可能具有对最终公钥/私钥对的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e59d9-205">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="e59d9-206">为在全局程序集缓存中安装附属程序集，并确保附属程序集工作正常，可使用延迟签名技术。</span><span class="sxs-lookup"><span data-stu-id="e59d9-206">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="e59d9-207">延迟为程序集签名时，生成时可在文件中保留用于强名称签名的空间。</span><span class="sxs-lookup"><span data-stu-id="e59d9-207">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="e59d9-208">实际签名将延迟到以后的某个时间进行，即当最后的公钥/私钥对可用时。</span><span class="sxs-lookup"><span data-stu-id="e59d9-208">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="e59d9-209">有关延迟签名的详细信息，请参阅[延迟为程序集签名](../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="e59d9-209">For more information about delayed signing, see [Delay Signing an Assembly](../../standard/assembly/delay-sign.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="e59d9-210">获取公钥</span><span class="sxs-lookup"><span data-stu-id="e59d9-210">Obtaining the Public Key</span></span>

<span data-ttu-id="e59d9-211">若要延迟程序集签名，必须具有公钥访问权限。</span><span class="sxs-lookup"><span data-stu-id="e59d9-211">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="e59d9-212">可以从公司中将进行最终签名的组织处获取真正的公钥，也可以使用[强名称工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 创建一个公钥。</span><span class="sxs-lookup"><span data-stu-id="e59d9-212">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="e59d9-213">下面的 Sn.exe 命令创建一个测试公钥/私钥对  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-213">The following *Sn.exe* command creates a test public/private key pair.</span></span> <span data-ttu-id="e59d9-214">–k 选项指定 Sn.exe 应新建一个密钥对，并将其保存在 TestKeyPair.snk 文件中    。</span><span class="sxs-lookup"><span data-stu-id="e59d9-214">The **–k** option specifies that *Sn.exe* should create a new key pair and save it in a file named *TestKeyPair.snk*.</span></span>
  
```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="e59d9-215">可以从包含测试密钥对的文件中提取公钥。</span><span class="sxs-lookup"><span data-stu-id="e59d9-215">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="e59d9-216">以下命令从 TestKeyPair.snk 中提取公钥，并将其保存在 PublicKey.snk 中   ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-216">The following command extracts the public key from *TestKeyPair.snk* and saves it in *PublicKey.snk*:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="e59d9-217">延迟为程序集签名</span><span class="sxs-lookup"><span data-stu-id="e59d9-217">Delay Signing an Assembly</span></span>

<span data-ttu-id="e59d9-218">获取或创建公钥后，使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 编译程序集，并指定延迟签名。</span><span class="sxs-lookup"><span data-stu-id="e59d9-218">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="e59d9-219">下面的 Al.exe 命令从 strings.ja.resources 文件为应用程序 StringLibrary 创建了一个强名称附属程序集   ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-219">The following *Al.exe* command creates a strong-named satellite assembly for the application StringLibrary from the *strings.ja.resources* file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="e59d9-220">-delay+ 选项指定程序集链接器应延迟对程序集签名  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-220">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="e59d9-221">-keyfile 选项指定密钥文件的名称，该文件包含用以延迟程序集签名的公钥  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-221">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="e59d9-222">对程序集重新签名</span><span class="sxs-lookup"><span data-stu-id="e59d9-222">Re-signing an Assembly</span></span>

<span data-ttu-id="e59d9-223">部署应用程序之前，必须使用真正的密钥对对延迟签名的附属程序集重新签名。</span><span class="sxs-lookup"><span data-stu-id="e59d9-223">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="e59d9-224">可以使用 Sn.exe 执行此操作  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-224">You can do this by using *Sn.exe*.</span></span>

<span data-ttu-id="e59d9-225">下面的 Sn.exe 命令使用 RealKeyPair.snk 文件中存储的密钥对对 StringLibrary.resources.dll 进行签名    。</span><span class="sxs-lookup"><span data-stu-id="e59d9-225">The following *Sn.exe* command signs *StringLibrary.resources.dll* with the key pair stored in the file *RealKeyPair.snk*.</span></span> <span data-ttu-id="e59d9-226">– R 选项指定对之前已签名或延迟签名的程序集进行重新签名  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-226">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="e59d9-227">在全局程序集缓存中安装附属程序集</span><span class="sxs-lookup"><span data-stu-id="e59d9-227">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="e59d9-228">运行时在资源回退进程中搜索资源时，首先会在[全局程序集缓存](../app-domains/gac.md)中查找。</span><span class="sxs-lookup"><span data-stu-id="e59d9-228">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../app-domains/gac.md) first.</span></span> <span data-ttu-id="e59d9-229">（有关详细信息，请参阅[打包和部署资源](packaging-and-deploying-resources-in-desktop-apps.md)主题中的“资源回退进程”部分。）只要使用强名称对附属程序集签名，就可以使用[全局程序集缓存工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 在全局程序集缓存中安装该程序集。</span><span class="sxs-lookup"><span data-stu-id="e59d9-229">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="e59d9-230">下面的 Gacutil.exe 命令在全局程序集缓存中安装了 StringLibrary.resources.dll   ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-230">The following *Gacutil.exe* command installs *StringLibrary.resources.dll*\* in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="e59d9-231">/I 选项指定 Gacutil.exe 应将指定的程序集安装到全局程序集缓存中   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-231">The **/i** option specifies that *Gacutil.exe* should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="e59d9-232">在缓存中安装了附属程序集之后，要使用附属程序集的应用程序便能够使用该附属程序集所包含的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-232">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="e59d9-233">全局程序集缓存中的资源：示例</span><span class="sxs-lookup"><span data-stu-id="e59d9-233">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="e59d9-234">以下示例使用 .NET Framework 类库中的方法从资源文件中提取和返回本地化的问候语。</span><span class="sxs-lookup"><span data-stu-id="e59d9-234">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="e59d9-235">在全局程序集缓存中注册库及其资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-235">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="e59d9-236">示例包括了英语（美国）、法语（法国）、俄语（俄罗斯）和英语区域性的资源。</span><span class="sxs-lookup"><span data-stu-id="e59d9-236">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="e59d9-237">英语是默认区域性；其资源存储在主程序集中。</span><span class="sxs-lookup"><span data-stu-id="e59d9-237">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="e59d9-238">此示例最初使用公钥延迟对库及其附属程序集签名，然后使用公钥/私钥对为其重新签名。</span><span class="sxs-lookup"><span data-stu-id="e59d9-238">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="e59d9-239">要创建示例，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e59d9-239">To create the example, do the following:</span></span>

1. <span data-ttu-id="e59d9-240">如果不是使用 Visual Studio，则使用以下[强名称工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 命令创建名为 ResKey.snk 的公钥/私钥对  ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-240">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named *ResKey.snk*:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="e59d9-241">如果使用的是 Visual Studio，则使用项目“属性”对话框中的“签名”选项卡生成密钥文件   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-241">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="e59d9-242">使用以下[强名称工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 命令创建名为 PublicKey.snk 的公钥文件  ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-242">Use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public key file named *PublicKey.snk*:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="e59d9-243">创建一个名为 Strings.resx 的资源文件，使其包含默认区域性的资源  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-243">Create a resource file named *Strings.resx* to contain the resource for the default culture.</span></span> <span data-ttu-id="e59d9-244">在此文件中存储一个名为 `Greeting`，并且值为“How do you do?”的</span><span class="sxs-lookup"><span data-stu-id="e59d9-244">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="e59d9-245">单个字符串。</span><span class="sxs-lookup"><span data-stu-id="e59d9-245">in that file.</span></span>

4. <span data-ttu-id="e59d9-246">为指示 "en" 是该应用程序的默认区域性，请将以下 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> 属性添加到应用程序的 AssemblyInfo 文件或主源代码文件中，该文件之后会编译到应用程序的主程序集中：</span><span class="sxs-lookup"><span data-stu-id="e59d9-246">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="e59d9-247">向应用程序添加对其他区域性的支持（en-US、fr-FR 和 ru-RU 区域性），如下所示：</span><span class="sxs-lookup"><span data-stu-id="e59d9-247">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="e59d9-248">若要支持“en-US”或英语（美国）区域性，则创建一个名为 Strings.en-US.resx 或 Strings.en-US.txt 的资源文件，并在其中存储一个名为 `Greeting` 且值为“Hello”的单个字符串   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-248">To support the "en-US" or English (United States) culture, create a resource file named *Strings.en-US.resx* or *Strings.en-US.txt*, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="e59d9-249">若要支持“fr-FR”或法语（法国）区域性，创建一个名为 Strings.fr-FR.resx 或 Strings.fr-FR.txt 的资源文件，并在其中存储一个值为“Bon jour!”的 `Greeting` 单字符串   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-249">To support the "fr-FR" or French (France) culture, create a resource file named *Strings.fr-FR.resx* or *Strings.fr-FR.txt* and store in it a single string named `Greeting` whose value is "Bon jour!".</span></span>

    - <span data-ttu-id="e59d9-250">若要支持“ru-RU”或俄语（俄罗斯）区域性，创建一个名为 Strings.ru-RU.resx 或 Strings.ru-RU.txt 的资源文件，并在其中存储一个值为“Привет”的 `Greeting` 单字符串   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-250">To support the "ru-RU" or Russian (Russia) culture, create a resource file named *Strings.ru-RU.resx* or *Strings.ru-RU.txt* and store in it a single string named `Greeting` whose value is "Привет!".</span></span>

6. <span data-ttu-id="e59d9-251">使用 [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) 将每个文本文件或 XML 资源文件编译为二进制 .resources 文件。</span><span class="sxs-lookup"><span data-stu-id="e59d9-251">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="e59d9-252">其输出是一组与 .resx  或 .txt  文件具有相同根文件名的文件，这些文件的扩展名为 .resources  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-252">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="e59d9-253">如果使用 Visual Studio 创建该示例，将自动处理编译过程。</span><span class="sxs-lookup"><span data-stu-id="e59d9-253">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="e59d9-254">如果不使用 Visual Studio，则运行以下命令将 .resx 文件编译进 .resources 文件   ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-254">If you aren't using Visual Studio, run the following command to compile the *.resx* files into *.resources* files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="e59d9-255">其中 filename 是 .resx 或文本文件的可选路径、文件名和扩展名   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-255">Where *filename* is the optional path, file name, and extension of the *.resx* or text file.</span></span>

7. <span data-ttu-id="e59d9-256">将以下 StringLibrary.vb 或 StringLibrary.cs 的源代码连同默认区域性的资源编译到名为 StringLibrary.dll 的延迟签名库程序集中    ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-256">Compile the following source code for *StringLibrary.vb* or *StringLibrary.cs* along with the resources for the default culture into a delay signed library assembly named *StringLibrary.dll*:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e59d9-257">如果使用命令行而不是 Visual Studio 来创建此示例，则将对 <xref:System.Resources.ResourceManager> 类构造函数的调用修改为 `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`。</span><span class="sxs-lookup"><span data-stu-id="e59d9-257">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="e59d9-258">适用于 C# 编译器的命令：</span><span class="sxs-lookup"><span data-stu-id="e59d9-258">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="e59d9-259">相应的 Visual Basic 编译器命令为：</span><span class="sxs-lookup"><span data-stu-id="e59d9-259">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="e59d9-260">在主应用程序目录中为应用程序支持的每个本地化的区域性创建一个子目录。</span><span class="sxs-lookup"><span data-stu-id="e59d9-260">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="e59d9-261">应该创建一个 en-US、fr-FR 和 ru-RU 子目录    。</span><span class="sxs-lookup"><span data-stu-id="e59d9-261">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="e59d9-262">Visual Studio 将在编译过程中自动创建这些子目录。</span><span class="sxs-lookup"><span data-stu-id="e59d9-262">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="e59d9-263">由于所有附属程序集都具有相同的文件名，所以使用子目录存储单个区域性特定的附属程序集，直到使用公钥/私钥对为附属程序集签名为止。</span><span class="sxs-lookup"><span data-stu-id="e59d9-263">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="e59d9-264">将某个特定区域性的 .resources 文件嵌入延迟签名的附属程序集，并将其保存到相应的目录  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-264">Embed the individual culture-specific *.resources* files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="e59d9-265">用于为每个 .resources 文件执行此操作的命令是  ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-265">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="e59d9-266">其中 culture 是区域性的名称  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-266">where *culture* is the name of a culture.</span></span> <span data-ttu-id="e59d9-267">在此示例中，区域性名称是 en-US、fr-FR 和 ru-RU。</span><span class="sxs-lookup"><span data-stu-id="e59d9-267">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="e59d9-268">使用[强名称工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 对 StringLibrary.dll  重新签名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e59d9-268">Re-sign *StringLibrary.dll* by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="e59d9-269">对单个附属程序集重新签名。</span><span class="sxs-lookup"><span data-stu-id="e59d9-269">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="e59d9-270">要执行此操作，请按如下所示对每个附属程序集使用[强名称工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md)：</span><span class="sxs-lookup"><span data-stu-id="e59d9-270">To do this, use the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="e59d9-271">使用以下命令在全局程序集缓存中注册 StringLibrary.dll 及其每个附属程序集  ：</span><span class="sxs-lookup"><span data-stu-id="e59d9-271">Register *StringLibrary.dll* and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="e59d9-272">其中 filename 是要注册的文件的名称  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-272">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="e59d9-273">如果使用的是 Visual Studio，则新建一个名为 `Example` 的控制台应用程序项目，向其添加对 StringLibrary.dll 的引用和以下源代码，然后进行编译   。</span><span class="sxs-lookup"><span data-stu-id="e59d9-273">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to *StringLibrary.dll* and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="e59d9-274">若要通过命令行进行编译，请在 C# 编译器中使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e59d9-274">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="e59d9-275">适用于 Visual Basic 编译器的命令行为：</span><span class="sxs-lookup"><span data-stu-id="e59d9-275">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="e59d9-276">运行 Example.exe  。</span><span class="sxs-lookup"><span data-stu-id="e59d9-276">Run *Example.exe*.</span></span>

## <a name="see-also"></a><span data-ttu-id="e59d9-277">请参阅</span><span class="sxs-lookup"><span data-stu-id="e59d9-277">See also</span></span>

- [<span data-ttu-id="e59d9-278">打包和部署资源</span><span class="sxs-lookup"><span data-stu-id="e59d9-278">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="e59d9-279">延迟签发程序集</span><span class="sxs-lookup"><span data-stu-id="e59d9-279">Delay Signing an Assembly</span></span>](../../standard/assembly/delay-sign.md)
- [<span data-ttu-id="e59d9-280">Al.exe（程序集链接器）</span><span class="sxs-lookup"><span data-stu-id="e59d9-280">Al.exe (Assembly Linker)</span></span>](../tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="e59d9-281">Sn.exe（强名称工具）</span><span class="sxs-lookup"><span data-stu-id="e59d9-281">Sn.exe (Strong Name Tool)</span></span>](../tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="e59d9-282">Gacutil.exe（全局程序集缓存工具）</span><span class="sxs-lookup"><span data-stu-id="e59d9-282">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="e59d9-283">桌面应用中的资源</span><span class="sxs-lookup"><span data-stu-id="e59d9-283">Resources in Desktop Apps</span></span>](index.md)
