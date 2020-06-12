---
title: 打包和部署自定义 My 扩展
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 6d2cc2b01b04b30bd3b1a4371352ded20ea8664b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411748"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="99bf2-102">打包和部署自定义 My 扩展 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99bf2-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="99bf2-103">Visual Basic 提供了一种简单的方法，允许你使用 Visual Studio 模板部署自定义 `My` 命名空间扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="99bf2-104">如果创建的项目模板的 `My` 扩展是新项目类型的组成部分，则可以在导出模板时将自定义 `My` 扩展代码包含在项目中。</span><span class="sxs-lookup"><span data-stu-id="99bf2-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="99bf2-105">有关导出项目模板的详细信息，请参阅[如何：创建项目模板](/visualstudio/ide/how-to-create-project-templates)。</span><span class="sxs-lookup"><span data-stu-id="99bf2-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="99bf2-106">如果自定义 `My` 扩展位于单个代码文件中，则可以将该文件作为项模板导出，用户可以将该模板添加到任何类型的 Visual Basic 项目中。</span><span class="sxs-lookup"><span data-stu-id="99bf2-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="99bf2-107">然后，你可以自定义项模板，以在 Visual Basic 项目中为自定义 `My` 扩展启用附加功能和行为。</span><span class="sxs-lookup"><span data-stu-id="99bf2-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="99bf2-108">这些功能包括：</span><span class="sxs-lookup"><span data-stu-id="99bf2-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="99bf2-109">允许用户从 Visual Basic 项目设计器的“My 扩展”页管理你的自定义 `My` 扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="99bf2-110">当向项目添加对指定程序集的引用时，将自动添加自定义 `My` 扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="99bf2-111">隐藏“添加项”对话框中的 `My` 扩展项模板，使其不包含在项目项列表中。</span><span class="sxs-lookup"><span data-stu-id="99bf2-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="99bf2-112">本主题讨论如何将自定义 `My` 扩展打包为隐藏项模板，该模板可从 Visual Basic 项目设计器的“My 扩展”页进行管理。</span><span class="sxs-lookup"><span data-stu-id="99bf2-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="99bf2-113">当向项目添加对指定程序集的引用时，还可以自动添加自定义 `My` 扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="99bf2-114">创建 My 命名空间扩展</span><span class="sxs-lookup"><span data-stu-id="99bf2-114">Create a My namespace extension</span></span>

<span data-ttu-id="99bf2-115">为自定义 `My` 扩展创建部署包的第一步是将扩展创建为单个代码文件。</span><span class="sxs-lookup"><span data-stu-id="99bf2-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="99bf2-116">有关如何创建自定义 `My` 扩展的详细信息和指南，请参阅[在Visual Basic 中扩展 My 命名空间](extending-the-my-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="99bf2-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="99bf2-117">将 My 命名空间扩展作为项模板导出</span><span class="sxs-lookup"><span data-stu-id="99bf2-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="99bf2-118">在具有包含 `My` 命名空间扩展的代码文件后，你可以将代码文件作为 Visual Studio 项模板导出。</span><span class="sxs-lookup"><span data-stu-id="99bf2-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="99bf2-119">有关如何将文件作为 Visual Studio 项模板导出的说明，请参阅[如何：创建项模板](/visualstudio/ide/how-to-create-item-templates)。</span><span class="sxs-lookup"><span data-stu-id="99bf2-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="99bf2-120">如果 `My` 命名空间扩展依赖于特定程序集，则可以自定义项模板，以便在添加对该程序集的引用时自动安装 `My` 命名空间扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="99bf2-121">因此，在将代码文件作为 Visual Studio 项模板导出时，你需要排除该程序集引用。</span><span class="sxs-lookup"><span data-stu-id="99bf2-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="99bf2-122">自定义项模板</span><span class="sxs-lookup"><span data-stu-id="99bf2-122">Customize the item template</span></span>

<span data-ttu-id="99bf2-123">可以从 Visual Basic 项目设计器的“My 扩展”页中启用项模板管理。</span><span class="sxs-lookup"><span data-stu-id="99bf2-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="99bf2-124">当向项目添加对指定程序集的引用时，还可以启用自动添加项模板。</span><span class="sxs-lookup"><span data-stu-id="99bf2-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="99bf2-125">若要启用这些自定义项，请将名为“CustomData”的新文件添加到模板，然后将新元素添加到 .vstemplate 文件中的 XML。</span><span class="sxs-lookup"><span data-stu-id="99bf2-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="99bf2-126">添加 CustomData 文件</span><span class="sxs-lookup"><span data-stu-id="99bf2-126">Add the CustomData file</span></span>

<span data-ttu-id="99bf2-127">CustomData 文件是具有文件扩展名 .CustomData 并包含 XML 的文本文件（可将文件名设置为任何有意义的模板值）。</span><span class="sxs-lookup"><span data-stu-id="99bf2-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="99bf2-128">CustomData 文件中的 XML 指示，当用户使用 Visual Basic 项目设计器的“My 扩展”页时，Visual Basic 应包含 `My` 扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="99bf2-129">可以选择将 <`AssemblyFullName>` 属性添加到 CustomData 文件 XML 中。</span><span class="sxs-lookup"><span data-stu-id="99bf2-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="99bf2-130">这将指示 Visual Basic 在将对特定程序集的引用添加到项目时，自动安装自定义 `My` 扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="99bf2-131">可以使用任何文本编辑器或 XML 编辑器创建 CustomData 文件，然后将其添加到项模板的压缩文件夹（.zip 文件）。</span><span class="sxs-lookup"><span data-stu-id="99bf2-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="99bf2-132">例如，下面的 XML 显示 CustomData 文件的内容，当向项目添加对 Microsoft.VisualBasic.PowerPacks.Vs.dll 程序集的引用时，该文件会将模板项添加到 Visual Basic 项目的“My 扩展”文件夹。</span><span class="sxs-lookup"><span data-stu-id="99bf2-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="99bf2-133">CustomData 文件包含一个 <`VBMyExtensionTemplate>` 元素，其属性如下表所示。</span><span class="sxs-lookup"><span data-stu-id="99bf2-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="99bf2-134">特性</span><span class="sxs-lookup"><span data-stu-id="99bf2-134">Attribute</span></span>|<span data-ttu-id="99bf2-135">描述</span><span class="sxs-lookup"><span data-stu-id="99bf2-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="99bf2-136">必需。</span><span class="sxs-lookup"><span data-stu-id="99bf2-136">Required.</span></span> <span data-ttu-id="99bf2-137">扩展的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="99bf2-137">A unique identifier for the extension.</span></span> <span data-ttu-id="99bf2-138">如果已将具有此 ID 的扩展添加到项目，则不会提示用户再次添加该扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="99bf2-139">必需。</span><span class="sxs-lookup"><span data-stu-id="99bf2-139">Required.</span></span> <span data-ttu-id="99bf2-140">项模板的版本号。</span><span class="sxs-lookup"><span data-stu-id="99bf2-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="99bf2-141">可选。</span><span class="sxs-lookup"><span data-stu-id="99bf2-141">Optional.</span></span> <span data-ttu-id="99bf2-142">程序集名称。</span><span class="sxs-lookup"><span data-stu-id="99bf2-142">An assembly name.</span></span> <span data-ttu-id="99bf2-143">将对此程序集的引用添加到项目时，系统将提示用户从此项模板添加 `My` 扩展。</span><span class="sxs-lookup"><span data-stu-id="99bf2-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="99bf2-144">将 \<CustomDataSignature> 元素添加到 .vstemplate 文件</span><span class="sxs-lookup"><span data-stu-id="99bf2-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="99bf2-145">若要将 Visual Studio 项模板标识为 `My` 命名空间扩展，还必须修改项模板的 .vstemplate 文件。</span><span class="sxs-lookup"><span data-stu-id="99bf2-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="99bf2-146">必须向 `<TemplateData>` 元素添加一个 `<CustomDataSignature>` 元素。</span><span class="sxs-lookup"><span data-stu-id="99bf2-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="99bf2-147">`<CustomDataSignature>` 元素必须包含文本 `Microsoft.VisualBasic.MyExtension`，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="99bf2-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="99bf2-148">不能直接修改压缩文件夹中的文件（.zip 文件）。</span><span class="sxs-lookup"><span data-stu-id="99bf2-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="99bf2-149">必须从压缩文件夹复制 .vstemplate 文件，对其进行修改，然后将压缩文件夹中的 .vstemplate 文件替换为更新后的副本。</span><span class="sxs-lookup"><span data-stu-id="99bf2-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="99bf2-150">下面的示例演示添加了 `<CustomDataSignature>` 元素的 .vstemplate 文件的内容。</span><span class="sxs-lookup"><span data-stu-id="99bf2-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a><span data-ttu-id="99bf2-151">安装模板</span><span class="sxs-lookup"><span data-stu-id="99bf2-151">Install the template</span></span>

<span data-ttu-id="99bf2-152">若要安装模板，可以将压缩文件夹（.zip 文件）复制到 Visual Basic 项模板文件夹。</span><span class="sxs-lookup"><span data-stu-id="99bf2-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="99bf2-153">默认情况下，用户项模板位于 *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*。</span><span class="sxs-lookup"><span data-stu-id="99bf2-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="99bf2-154">也可以将模板作为 Visual Studio 安装程序 (.vsi) 文件发布。</span><span class="sxs-lookup"><span data-stu-id="99bf2-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="99bf2-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="99bf2-155">See also</span></span>

- [<span data-ttu-id="99bf2-156">扩展 Visual Basic 中的 My 命名空间</span><span class="sxs-lookup"><span data-stu-id="99bf2-156">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)
- [<span data-ttu-id="99bf2-157">扩展 Visual Basic 应用程序模型</span><span class="sxs-lookup"><span data-stu-id="99bf2-157">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="99bf2-158">自定义 My 中可用的对象</span><span class="sxs-lookup"><span data-stu-id="99bf2-158">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="99bf2-159">“项目设计器”->“My 扩展”页</span><span class="sxs-lookup"><span data-stu-id="99bf2-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
