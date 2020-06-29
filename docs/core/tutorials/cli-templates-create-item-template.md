---
title: 创建 dotnet new 项模板 - .NET Core CLI
description: 了解如何创建 dotnet new 命令项模板。 项模板可以包含任意数量的文件。
author: adegeo
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 0b804d26b2f33d4d600c17de2f7f71101a0f9c98
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324380"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="be30e-104">教程：创建项模板</span><span class="sxs-lookup"><span data-stu-id="be30e-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="be30e-105">使用 .NET Core，可以创建和部署可生成项目、文件甚至资源的模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="be30e-106">本教程是系列教程的第一部分，介绍如何创建、安装和卸载用于 `dotnet new` 命令的模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="be30e-107">在本系列的这一部分中，你将了解如何：</span><span class="sxs-lookup"><span data-stu-id="be30e-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="be30e-108">为项模板创建类</span><span class="sxs-lookup"><span data-stu-id="be30e-108">Create a class for an item template</span></span>
> * <span data-ttu-id="be30e-109">创建模板配置文件夹和文件</span><span class="sxs-lookup"><span data-stu-id="be30e-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="be30e-110">从文件路径安装模板</span><span class="sxs-lookup"><span data-stu-id="be30e-110">Install a template from a file path</span></span>
> * <span data-ttu-id="be30e-111">测试项模板</span><span class="sxs-lookup"><span data-stu-id="be30e-111">Test an item template</span></span>
> * <span data-ttu-id="be30e-112">卸载项模板</span><span class="sxs-lookup"><span data-stu-id="be30e-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be30e-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="be30e-113">Prerequisites</span></span>

* <span data-ttu-id="be30e-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="be30e-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="be30e-115">阅读参考文章[为 dotnet new 自定义模板](../tools/custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="be30e-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="be30e-116">参考文章介绍了有关模板的基础知识，以及如何将它们组合在一起。</span><span class="sxs-lookup"><span data-stu-id="be30e-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="be30e-117">其中一些信息将在本文中重复出现。</span><span class="sxs-lookup"><span data-stu-id="be30e-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="be30e-118">打开终端并导航到 working\templates  文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="be30e-119">创建所需的文件夹</span><span class="sxs-lookup"><span data-stu-id="be30e-119">Create the required folders</span></span>

<span data-ttu-id="be30e-120">本系列使用包含模板源的“working 文件夹”和用于测试模板的“testing 文件夹”。</span><span class="sxs-lookup"><span data-stu-id="be30e-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="be30e-121">working 文件夹和 testing 文件夹应位于同一父文件夹下。</span><span class="sxs-lookup"><span data-stu-id="be30e-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="be30e-122">首先，创建父文件夹，名称无关紧要。</span><span class="sxs-lookup"><span data-stu-id="be30e-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="be30e-123">然后，创建一个名为“working”  的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="be30e-124">在 working  文件夹内，创建一个名为“templates”  的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="be30e-125">接下来，在名为“test”  的父文件夹下创建一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="be30e-126">文件夹结构应如下所示。</span><span class="sxs-lookup"><span data-stu-id="be30e-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="be30e-127">创建项模板</span><span class="sxs-lookup"><span data-stu-id="be30e-127">Create an item template</span></span>

<span data-ttu-id="be30e-128">项模板是包含一个或多个文件的特定类型的模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="be30e-129">当你想要生成类似于配置、代码或解决方案文件的内容时，这些类型的模板非常有用。</span><span class="sxs-lookup"><span data-stu-id="be30e-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="be30e-130">在本例中，你将创建一个类，该类将扩展方法添加到字符串类型中。</span><span class="sxs-lookup"><span data-stu-id="be30e-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="be30e-131">在终端中，导航到 working\templates  文件夹，并创建一个名为“extensions”  的新子文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="be30e-132">进入文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="be30e-133">创建一个名为“CommonExtensions.cs”  的新文件，并使用你喜爱的文本编辑器打开它。</span><span class="sxs-lookup"><span data-stu-id="be30e-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="be30e-134">此类将提供一个用于反转字符串内容的名为 `Reverse` 的扩展方法。</span><span class="sxs-lookup"><span data-stu-id="be30e-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="be30e-135">粘贴以下代码并保存文件：</span><span class="sxs-lookup"><span data-stu-id="be30e-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="be30e-136">现在你已经创建了模板的内容，需要在模板的根文件夹中创建模板配置。</span><span class="sxs-lookup"><span data-stu-id="be30e-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="be30e-137">创建模板配置</span><span class="sxs-lookup"><span data-stu-id="be30e-137">Create the template config</span></span>

<span data-ttu-id="be30e-138">模板在 .NET Core 中通过模板根目录中的特殊文件夹和配置文件进行识别。</span><span class="sxs-lookup"><span data-stu-id="be30e-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="be30e-139">在本教程中，你的模板文件夹位于 working\templates\extensions  。</span><span class="sxs-lookup"><span data-stu-id="be30e-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="be30e-140">创建模板时，除特殊配置文件夹外，模板文件夹中的所有文件和文件夹都作为模板的一部分包含在内。</span><span class="sxs-lookup"><span data-stu-id="be30e-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="be30e-141">此配置文件夹名为“.template.config”  。</span><span class="sxs-lookup"><span data-stu-id="be30e-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="be30e-142">首先，创建一个名为“.template.config”  的新子文件夹，然后进入该文件夹。</span><span class="sxs-lookup"><span data-stu-id="be30e-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="be30e-143">然后，创建一个名为“template.json”  的新文件。</span><span class="sxs-lookup"><span data-stu-id="be30e-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="be30e-144">文件夹结构应如下所示：</span><span class="sxs-lookup"><span data-stu-id="be30e-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="be30e-145">使用你喜爱的文本编辑器打开 template.json  并粘贴以下 JSON 代码，然后保存。</span><span class="sxs-lookup"><span data-stu-id="be30e-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="be30e-146">此配置文件包含模板的所有设置。</span><span class="sxs-lookup"><span data-stu-id="be30e-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="be30e-147">可以看到基本设置，例如 `name` 和 `shortName`，除此之外，还有一个设置为 `item` 的 `tags/type` 值。</span><span class="sxs-lookup"><span data-stu-id="be30e-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="be30e-148">这会将你的模板归类为项模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="be30e-149">你创建的模板类型不存在限制。</span><span class="sxs-lookup"><span data-stu-id="be30e-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="be30e-150">`item` 和 `project` 值是 .NET Core 建议使用的通用名称，便于用户轻松筛选正在搜索的模板类型。</span><span class="sxs-lookup"><span data-stu-id="be30e-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="be30e-151">`classifications` 项表示你在运行 `dotnet new` 并获取模板列表时看到的“标记”  列。</span><span class="sxs-lookup"><span data-stu-id="be30e-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="be30e-152">用户还可以根据分类标记进行搜索。</span><span class="sxs-lookup"><span data-stu-id="be30e-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="be30e-153">不要将 \*.json 文件中的 `tags` 属性与 `classifications` 标记列表混淆。</span><span class="sxs-lookup"><span data-stu-id="be30e-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="be30e-154">它们虽然具有类似的名称，但截然不同。</span><span class="sxs-lookup"><span data-stu-id="be30e-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="be30e-155">template.json  文件的完整架构位于 [JSON 架构存储](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="be30e-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="be30e-156">有关 template.json  文件的详细信息，请参阅 [dotnet 创建模板 wiki](https://github.com/dotnet/templating/wiki)。</span><span class="sxs-lookup"><span data-stu-id="be30e-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="be30e-157">现在你已有一个有效的 .template.config/template.json  文件，可以安装模板了。</span><span class="sxs-lookup"><span data-stu-id="be30e-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="be30e-158">在终端中，导航到 extensions  文件夹，并运行以下命令以安装位于当前文件夹的模板：</span><span class="sxs-lookup"><span data-stu-id="be30e-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="be30e-159">**在 Windows 上**：`dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="be30e-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="be30e-160">**在 Linux 或 macOS 上**：`dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="be30e-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="be30e-161">此命令输出安装的模板列表，其中应包括你的模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="be30e-162">测试项模板</span><span class="sxs-lookup"><span data-stu-id="be30e-162">Test the item template</span></span>

<span data-ttu-id="be30e-163">现在你已安装了项模板，可对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="be30e-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="be30e-164">导航到 test/  文件夹，使用 `dotnet new console` 创建新的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="be30e-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="be30e-165">这将生成一个可以使用 `dotnet run` 命令轻松测试的工作项目。</span><span class="sxs-lookup"><span data-stu-id="be30e-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="be30e-166">将获得类似于下面的输出。</span><span class="sxs-lookup"><span data-stu-id="be30e-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="be30e-167">运行该项目。</span><span class="sxs-lookup"><span data-stu-id="be30e-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="be30e-168">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="be30e-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="be30e-169">接下来，运行 `dotnet new stringext` 以从模板生成 CommonExtensions.cs  。</span><span class="sxs-lookup"><span data-stu-id="be30e-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="be30e-170">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="be30e-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="be30e-171">更改 Program.cs  中的代码以使用模板提供的扩展方法反转 `"Hello World"` 字符串。</span><span class="sxs-lookup"><span data-stu-id="be30e-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="be30e-172">再次运行程序，将看到结果已反转。</span><span class="sxs-lookup"><span data-stu-id="be30e-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="be30e-173">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="be30e-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="be30e-174">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="be30e-174">Congratulations!</span></span> <span data-ttu-id="be30e-175">你已使用 .NET Core 创建并部署了项模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-175">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="be30e-176">为准备学习本系列教程的下一部分，必须卸载已创建的模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="be30e-177">确保同时删除 test  文件夹中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="be30e-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="be30e-178">这将回到干净状态，为本教程的下一个主要部分做好准备。</span><span class="sxs-lookup"><span data-stu-id="be30e-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="be30e-179">卸载模板</span><span class="sxs-lookup"><span data-stu-id="be30e-179">Uninstall the template</span></span>

<span data-ttu-id="be30e-180">由于模板是按文件路径安装的，因此，必须使用绝对  文件路径将其卸载。</span><span class="sxs-lookup"><span data-stu-id="be30e-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="be30e-181">可以通过运行 `dotnet new -u` 命令看到已安装的模板列表。</span><span class="sxs-lookup"><span data-stu-id="be30e-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="be30e-182">你的模板应列在最后。</span><span class="sxs-lookup"><span data-stu-id="be30e-182">Your template should be listed last.</span></span> <span data-ttu-id="be30e-183">使用列出的路径，通过执行 `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` 命令卸载模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-183">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="be30e-184">将获得类似于下面的输出。</span><span class="sxs-lookup"><span data-stu-id="be30e-184">You get output similar to the following.</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="be30e-185">若要卸载该模板，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="be30e-185">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="be30e-186">后续步骤</span><span class="sxs-lookup"><span data-stu-id="be30e-186">Next steps</span></span>

<span data-ttu-id="be30e-187">在本教程中，你创建了一个项模板。</span><span class="sxs-lookup"><span data-stu-id="be30e-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="be30e-188">若要了解如何创建项目模板，请继续学习本系列教程。</span><span class="sxs-lookup"><span data-stu-id="be30e-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be30e-189">创建项目模板</span><span class="sxs-lookup"><span data-stu-id="be30e-189">Create a project template</span></span>](cli-templates-create-project-template.md)
