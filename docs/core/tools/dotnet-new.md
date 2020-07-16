---
title: dotnet new 命令
description: dotnet new 命令可根据指定模板新建 .NET Core 项目。
no-loc:
- Blazor
- WebAssembly
ms.date: 04/10/2020
ms.openlocfilehash: ec41b3b79ed5eded7c9124d3e4d95c658ee39580
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173115"
---
# <a name="dotnet-new"></a><span data-ttu-id="9c777-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9c777-103">dotnet new</span></span>

<span data-ttu-id="9c777-104">本文适用于： ✔️ .NET Core 2.0 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="9c777-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9c777-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="9c777-105">Name</span></span>

<span data-ttu-id="9c777-106">`dotnet new` - 根据指定的模板，创建新的项目、配置文件或解决方案。</span><span class="sxs-lookup"><span data-stu-id="9c777-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9c777-107">摘要</span><span class="sxs-lookup"><span data-stu-id="9c777-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="9c777-108">描述</span><span class="sxs-lookup"><span data-stu-id="9c777-108">Description</span></span>

<span data-ttu-id="9c777-109">`dotnet new` 命令基于模板创建 .NET Core 项目或其他项目。</span><span class="sxs-lookup"><span data-stu-id="9c777-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="9c777-110">命令调用[模板引擎](https://github.com/dotnet/templating)，以根据指定的模板和选项在磁盘上创建项目。</span><span class="sxs-lookup"><span data-stu-id="9c777-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="9c777-111">隐式还原</span><span class="sxs-lookup"><span data-stu-id="9c777-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="9c777-112">自变量</span><span class="sxs-lookup"><span data-stu-id="9c777-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="9c777-113">调用命令时要实例化的模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="9c777-114">每个模板可能具有可传递的特定选项。</span><span class="sxs-lookup"><span data-stu-id="9c777-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="9c777-115">有关详细信息，请参阅[模板选项](#template-options)。</span><span class="sxs-lookup"><span data-stu-id="9c777-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="9c777-116">可以运行 `dotnet new --list` 或 `dotnet new -l` 以查看所有已安装模板的列表。</span><span class="sxs-lookup"><span data-stu-id="9c777-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="9c777-117">如果 `TEMPLATE` 值与返回表中的“模板”或“短名称”列中的文本不完全匹配，则会对这两列执行 substring 匹配。</span><span class="sxs-lookup"><span data-stu-id="9c777-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="9c777-118">从 .NET Core 3.0 SDK 开始，当你在以下情况下调用 `dotnet new` 命令时，CLI 将在 NuGet.org 中搜索模板：</span><span class="sxs-lookup"><span data-stu-id="9c777-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="9c777-119">如果在调用 `dotnet new` 时 CLI 找不到模板匹配项，即使是部分匹配也不行。</span><span class="sxs-lookup"><span data-stu-id="9c777-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="9c777-120">如果有较新版本的模板可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="9c777-121">在这种情况下，将创建项目或工件，但 CLI 会就模板的更新版本发出警告。</span><span class="sxs-lookup"><span data-stu-id="9c777-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="9c777-122">下表显示了随 .NET Core SDK 一起预安装的模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="9c777-123">模板的默认语言显示在括号内。</span><span class="sxs-lookup"><span data-stu-id="9c777-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="9c777-124">单击短名称链接可查看特定的模板选项。</span><span class="sxs-lookup"><span data-stu-id="9c777-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="9c777-125">模板</span><span class="sxs-lookup"><span data-stu-id="9c777-125">Templates</span></span>                                    | <span data-ttu-id="9c777-126">短名称</span><span class="sxs-lookup"><span data-stu-id="9c777-126">Short name</span></span>                      | <span data-ttu-id="9c777-127">语言</span><span class="sxs-lookup"><span data-stu-id="9c777-127">Language</span></span>     | <span data-ttu-id="9c777-128">Tags</span><span class="sxs-lookup"><span data-stu-id="9c777-128">Tags</span></span>                                  | <span data-ttu-id="9c777-129">已引入</span><span class="sxs-lookup"><span data-stu-id="9c777-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="9c777-130">控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="9c777-130">Console Application</span></span>                          | [<span data-ttu-id="9c777-131">控制台</span><span class="sxs-lookup"><span data-stu-id="9c777-131">console</span></span>](#console)             | <span data-ttu-id="9c777-132">[C#]、F#、VB</span><span class="sxs-lookup"><span data-stu-id="9c777-132">[C#], F#, VB</span></span> | <span data-ttu-id="9c777-133">常用/控制台</span><span class="sxs-lookup"><span data-stu-id="9c777-133">Common/Console</span></span>                        | <span data-ttu-id="9c777-134">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-134">1.0</span></span>        |
| <span data-ttu-id="9c777-135">类库</span><span class="sxs-lookup"><span data-stu-id="9c777-135">Class library</span></span>                                | [<span data-ttu-id="9c777-136">classlib</span><span class="sxs-lookup"><span data-stu-id="9c777-136">classlib</span></span>](#classlib)           | <span data-ttu-id="9c777-137">[C#]、F#、VB</span><span class="sxs-lookup"><span data-stu-id="9c777-137">[C#], F#, VB</span></span> | <span data-ttu-id="9c777-138">常用/库</span><span class="sxs-lookup"><span data-stu-id="9c777-138">Common/Library</span></span>                        | <span data-ttu-id="9c777-139">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-139">1.0</span></span>        |
| <span data-ttu-id="9c777-140">WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="9c777-140">WPF Application</span></span>                              | [<span data-ttu-id="9c777-141">wpf</span><span class="sxs-lookup"><span data-stu-id="9c777-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="9c777-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-142">[C#]</span></span>         | <span data-ttu-id="9c777-143">常用/WPF</span><span class="sxs-lookup"><span data-stu-id="9c777-143">Common/WPF</span></span>                            | <span data-ttu-id="9c777-144">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-144">3.0</span></span>        |
| <span data-ttu-id="9c777-145">WPF 类库</span><span class="sxs-lookup"><span data-stu-id="9c777-145">WPF Class library</span></span>                            | [<span data-ttu-id="9c777-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="9c777-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="9c777-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-147">[C#]</span></span>         | <span data-ttu-id="9c777-148">常用/WPF</span><span class="sxs-lookup"><span data-stu-id="9c777-148">Common/WPF</span></span>                            | <span data-ttu-id="9c777-149">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-149">3.0</span></span>        |
| <span data-ttu-id="9c777-150">WPF 自定义控件库</span><span class="sxs-lookup"><span data-stu-id="9c777-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="9c777-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="9c777-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="9c777-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-152">[C#]</span></span>         | <span data-ttu-id="9c777-153">常用/WPF</span><span class="sxs-lookup"><span data-stu-id="9c777-153">Common/WPF</span></span>                            | <span data-ttu-id="9c777-154">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-154">3.0</span></span>        |
| <span data-ttu-id="9c777-155">WPF 用户控件库</span><span class="sxs-lookup"><span data-stu-id="9c777-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="9c777-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="9c777-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="9c777-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-157">[C#]</span></span>         | <span data-ttu-id="9c777-158">常用/WPF</span><span class="sxs-lookup"><span data-stu-id="9c777-158">Common/WPF</span></span>                            | <span data-ttu-id="9c777-159">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-159">3.0</span></span>        |
| <span data-ttu-id="9c777-160">Windows 窗体 (WinForms) 应用程序</span><span class="sxs-lookup"><span data-stu-id="9c777-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="9c777-161">winforms</span><span class="sxs-lookup"><span data-stu-id="9c777-161">winforms</span></span>](#winforms)           | <span data-ttu-id="9c777-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-162">[C#]</span></span>         | <span data-ttu-id="9c777-163">常用/WinForms</span><span class="sxs-lookup"><span data-stu-id="9c777-163">Common/WinForms</span></span>                       | <span data-ttu-id="9c777-164">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-164">3.0</span></span>        |
| <span data-ttu-id="9c777-165">Windows 窗体 (WinForms) 类库</span><span class="sxs-lookup"><span data-stu-id="9c777-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="9c777-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="9c777-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="9c777-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-167">[C#]</span></span>         | <span data-ttu-id="9c777-168">常用/WinForms</span><span class="sxs-lookup"><span data-stu-id="9c777-168">Common/WinForms</span></span>                       | <span data-ttu-id="9c777-169">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-169">3.0</span></span>        |
| <span data-ttu-id="9c777-170">Worker Service</span><span class="sxs-lookup"><span data-stu-id="9c777-170">Worker Service</span></span>                               | [<span data-ttu-id="9c777-171">worker</span><span class="sxs-lookup"><span data-stu-id="9c777-171">worker</span></span>](#web-others)           | <span data-ttu-id="9c777-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-172">[C#]</span></span>         | <span data-ttu-id="9c777-173">常用/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="9c777-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="9c777-174">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-174">3.0</span></span>        |
| <span data-ttu-id="9c777-175">单元测试项目</span><span class="sxs-lookup"><span data-stu-id="9c777-175">Unit Test Project</span></span>                            | [<span data-ttu-id="9c777-176">mstest</span><span class="sxs-lookup"><span data-stu-id="9c777-176">mstest</span></span>](#test)                 | <span data-ttu-id="9c777-177">[C#]、F#、VB</span><span class="sxs-lookup"><span data-stu-id="9c777-177">[C#], F#, VB</span></span> | <span data-ttu-id="9c777-178">测试/MSTest</span><span class="sxs-lookup"><span data-stu-id="9c777-178">Test/MSTest</span></span>                           | <span data-ttu-id="9c777-179">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-179">1.0</span></span>        |
| <span data-ttu-id="9c777-180">NUnit 3 测试项目</span><span class="sxs-lookup"><span data-stu-id="9c777-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="9c777-181">nunit</span><span class="sxs-lookup"><span data-stu-id="9c777-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="9c777-182">[C#]、F#、VB</span><span class="sxs-lookup"><span data-stu-id="9c777-182">[C#], F#, VB</span></span> | <span data-ttu-id="9c777-183">测试/NUnit</span><span class="sxs-lookup"><span data-stu-id="9c777-183">Test/NUnit</span></span>                            | <span data-ttu-id="9c777-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="9c777-184">2.1.400</span></span>    |
| <span data-ttu-id="9c777-185">NUnit 3 测试项</span><span class="sxs-lookup"><span data-stu-id="9c777-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="9c777-186">[C#]、F#、VB</span><span class="sxs-lookup"><span data-stu-id="9c777-186">[C#], F#, VB</span></span> | <span data-ttu-id="9c777-187">测试/NUnit</span><span class="sxs-lookup"><span data-stu-id="9c777-187">Test/NUnit</span></span>                            | <span data-ttu-id="9c777-188">2.2</span><span class="sxs-lookup"><span data-stu-id="9c777-188">2.2</span></span>        |
| <span data-ttu-id="9c777-189">xUnit 测试项目</span><span class="sxs-lookup"><span data-stu-id="9c777-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="9c777-190">xunit</span><span class="sxs-lookup"><span data-stu-id="9c777-190">xunit</span></span>](#test)                  | <span data-ttu-id="9c777-191">[C#]、F#、VB</span><span class="sxs-lookup"><span data-stu-id="9c777-191">[C#], F#, VB</span></span> | <span data-ttu-id="9c777-192">测试/xUnit</span><span class="sxs-lookup"><span data-stu-id="9c777-192">Test/xUnit</span></span>                            | <span data-ttu-id="9c777-193">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-193">1.0</span></span>        |
| <span data-ttu-id="9c777-194">Razor 组件</span><span class="sxs-lookup"><span data-stu-id="9c777-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="9c777-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-195">[C#]</span></span>         | <span data-ttu-id="9c777-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9c777-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="9c777-197">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-197">3.0</span></span>        |
| <span data-ttu-id="9c777-198">Razor 页</span><span class="sxs-lookup"><span data-stu-id="9c777-198">Razor Page</span></span>                                   | [<span data-ttu-id="9c777-199">page</span><span class="sxs-lookup"><span data-stu-id="9c777-199">page</span></span>](#page)                   | <span data-ttu-id="9c777-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-200">[C#]</span></span>         | <span data-ttu-id="9c777-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9c777-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="9c777-202">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-202">2.0</span></span>        |
| <span data-ttu-id="9c777-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="9c777-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="9c777-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="9c777-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="9c777-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-205">[C#]</span></span>         | <span data-ttu-id="9c777-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9c777-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="9c777-207">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-207">2.0</span></span>        |
| <span data-ttu-id="9c777-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="9c777-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="9c777-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-209">[C#]</span></span>         | <span data-ttu-id="9c777-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9c777-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="9c777-211">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-211">2.0</span></span>        |
| Blazor<span data-ttu-id="9c777-212"> 服务器应用</span><span class="sxs-lookup"><span data-stu-id="9c777-212"> Server App</span></span>                            | [<span data-ttu-id="9c777-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="9c777-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="9c777-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-214">[C#]</span></span>         | <span data-ttu-id="9c777-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="9c777-215">Web/Blazor</span></span>                            | <span data-ttu-id="9c777-216">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-216">3.0</span></span>        |
| Blazor<span data-ttu-id="9c777-217"> WebAssembly 应用</span><span class="sxs-lookup"><span data-stu-id="9c777-217"> WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="9c777-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-218">[C#]</span></span>         | <span data-ttu-id="9c777-219">Web/Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="9c777-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="9c777-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="9c777-220">3.1.300</span></span>    |
| <span data-ttu-id="9c777-221">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="9c777-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="9c777-222">web</span><span class="sxs-lookup"><span data-stu-id="9c777-222">web</span></span>](#web)                     | <span data-ttu-id="9c777-223">[C#]，F#</span><span class="sxs-lookup"><span data-stu-id="9c777-223">[C#], F#</span></span>     | <span data-ttu-id="9c777-224">Web/空</span><span class="sxs-lookup"><span data-stu-id="9c777-224">Web/Empty</span></span>                             | <span data-ttu-id="9c777-225">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-225">1.0</span></span>        |
| <span data-ttu-id="9c777-226">ASP.NET Core Web 应用程序 (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="9c777-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="9c777-227">mvc</span><span class="sxs-lookup"><span data-stu-id="9c777-227">mvc</span></span>](#web-options)             | <span data-ttu-id="9c777-228">[C#]，F#</span><span class="sxs-lookup"><span data-stu-id="9c777-228">[C#], F#</span></span>     | <span data-ttu-id="9c777-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="9c777-229">Web/MVC</span></span>                               | <span data-ttu-id="9c777-230">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-230">1.0</span></span>        |
| <span data-ttu-id="9c777-231">ASP.NET Core Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="9c777-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="9c777-232">webapp、razor</span><span class="sxs-lookup"><span data-stu-id="9c777-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="9c777-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-233">[C#]</span></span>         | <span data-ttu-id="9c777-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="9c777-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="9c777-235">2.2、2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="9c777-236">含 Angular 的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c777-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="9c777-237">angular</span><span class="sxs-lookup"><span data-stu-id="9c777-237">angular</span></span>](#spa)                 | <span data-ttu-id="9c777-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-238">[C#]</span></span>         | <span data-ttu-id="9c777-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9c777-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="9c777-240">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-240">2.0</span></span>        |
| <span data-ttu-id="9c777-241">含 React.js 的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c777-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="9c777-242">react</span><span class="sxs-lookup"><span data-stu-id="9c777-242">react</span></span>](#spa)                   | <span data-ttu-id="9c777-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-243">[C#]</span></span>         | <span data-ttu-id="9c777-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9c777-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="9c777-245">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-245">2.0</span></span>        |
| <span data-ttu-id="9c777-246">含 React.js 和 Redux 的 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c777-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="9c777-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="9c777-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="9c777-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-248">[C#]</span></span>         | <span data-ttu-id="9c777-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9c777-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="9c777-250">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-250">2.0</span></span>        |
| <span data-ttu-id="9c777-251">Razor 类库</span><span class="sxs-lookup"><span data-stu-id="9c777-251">Razor Class Library</span></span>                          | [<span data-ttu-id="9c777-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="9c777-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="9c777-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-253">[C#]</span></span>         | <span data-ttu-id="9c777-254">Web/Razor/库/Razor 类库</span><span class="sxs-lookup"><span data-stu-id="9c777-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="9c777-255">2.1</span><span class="sxs-lookup"><span data-stu-id="9c777-255">2.1</span></span>        |
| <span data-ttu-id="9c777-256">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="9c777-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="9c777-257">webapi</span><span class="sxs-lookup"><span data-stu-id="9c777-257">webapi</span></span>](#webapi)               | <span data-ttu-id="9c777-258">[C#]，F#</span><span class="sxs-lookup"><span data-stu-id="9c777-258">[C#], F#</span></span>     | <span data-ttu-id="9c777-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="9c777-259">Web/WebAPI</span></span>                            | <span data-ttu-id="9c777-260">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-260">1.0</span></span>        |
| <span data-ttu-id="9c777-261">ASP.NET Core gRPC 服务</span><span class="sxs-lookup"><span data-stu-id="9c777-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="9c777-262">grpc</span><span class="sxs-lookup"><span data-stu-id="9c777-262">grpc</span></span>](#web-others)             | <span data-ttu-id="9c777-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="9c777-263">[C#]</span></span>         | <span data-ttu-id="9c777-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="9c777-264">Web/gRPC</span></span>                              | <span data-ttu-id="9c777-265">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-265">3.0</span></span>        |
| <span data-ttu-id="9c777-266">dotnet gitignore 文件</span><span class="sxs-lookup"><span data-stu-id="9c777-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="9c777-267">配置</span><span class="sxs-lookup"><span data-stu-id="9c777-267">Config</span></span>                                | <span data-ttu-id="9c777-268">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-268">3.0</span></span>        |
| <span data-ttu-id="9c777-269">global.json 文件</span><span class="sxs-lookup"><span data-stu-id="9c777-269">global.json file</span></span>                             | [<span data-ttu-id="9c777-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="9c777-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="9c777-271">配置</span><span class="sxs-lookup"><span data-stu-id="9c777-271">Config</span></span>                                | <span data-ttu-id="9c777-272">2.0</span><span class="sxs-lookup"><span data-stu-id="9c777-272">2.0</span></span>        |
| <span data-ttu-id="9c777-273">NuGet 配置</span><span class="sxs-lookup"><span data-stu-id="9c777-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="9c777-274">配置</span><span class="sxs-lookup"><span data-stu-id="9c777-274">Config</span></span>                                | <span data-ttu-id="9c777-275">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-275">1.0</span></span>        |
| <span data-ttu-id="9c777-276">Dotnet 本地工具清单文件</span><span class="sxs-lookup"><span data-stu-id="9c777-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="9c777-277">配置</span><span class="sxs-lookup"><span data-stu-id="9c777-277">Config</span></span>                                | <span data-ttu-id="9c777-278">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-278">3.0</span></span>        |
| <span data-ttu-id="9c777-279">Web 配置</span><span class="sxs-lookup"><span data-stu-id="9c777-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="9c777-280">配置</span><span class="sxs-lookup"><span data-stu-id="9c777-280">Config</span></span>                                | <span data-ttu-id="9c777-281">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-281">1.0</span></span>        |
| <span data-ttu-id="9c777-282">解决方案文件</span><span class="sxs-lookup"><span data-stu-id="9c777-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="9c777-283">解决方案</span><span class="sxs-lookup"><span data-stu-id="9c777-283">Solution</span></span>                              | <span data-ttu-id="9c777-284">1.0</span><span class="sxs-lookup"><span data-stu-id="9c777-284">1.0</span></span>        |
| <span data-ttu-id="9c777-285">协议缓冲区文件</span><span class="sxs-lookup"><span data-stu-id="9c777-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="9c777-286">proto</span><span class="sxs-lookup"><span data-stu-id="9c777-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="9c777-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="9c777-287">Web/gRPC</span></span>                              | <span data-ttu-id="9c777-288">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="9c777-289">选项</span><span class="sxs-lookup"><span data-stu-id="9c777-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="9c777-290">显示有关以下内容的摘要：给定命令运行导致模板创建时发生的情况。</span><span class="sxs-lookup"><span data-stu-id="9c777-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="9c777-291">自 .NET Core 2.2 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="9c777-292">强制生成内容，即使会更改现有文件，也不例外。</span><span class="sxs-lookup"><span data-stu-id="9c777-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9c777-293">当选择的模板将覆盖输出目录中的现有文件时，需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9c777-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9c777-294">打印命令帮助。</span><span class="sxs-lookup"><span data-stu-id="9c777-294">Prints out help for the command.</span></span> <span data-ttu-id="9c777-295">可针对 `dotnet new` 命令本身或任何模板调用它。</span><span class="sxs-lookup"><span data-stu-id="9c777-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="9c777-296">例如 `dotnet new mvc --help`。</span><span class="sxs-lookup"><span data-stu-id="9c777-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="9c777-297">从提供的 `PATH` 或 `NUGET_ID` 安装模板包。</span><span class="sxs-lookup"><span data-stu-id="9c777-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9c777-298">若要安装模板包的预发布版本，需要以 `<package-name>::<package-version>` 格式指定该版本。</span><span class="sxs-lookup"><span data-stu-id="9c777-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9c777-299">默认情况下，`dotnet new` 为该版本传递 \*，它表示最新的稳定包版本。</span><span class="sxs-lookup"><span data-stu-id="9c777-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="9c777-300">请在[示例](#examples)部分查看示例。</span><span class="sxs-lookup"><span data-stu-id="9c777-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="9c777-301">如果在运行此命令时已经安装了模板的某个版本，则该模板将更新到指定版本，如果没有指定版本，则将更新到最新的稳定版本。</span><span class="sxs-lookup"><span data-stu-id="9c777-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="9c777-302">若要了解如何创建自定义模板，请参阅 [dotnet new 自定义模板](custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="9c777-303">列出包含指定名称的模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="9c777-304">如果未指定名称，则列出所有模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="9c777-305">要创建的模板的语言。</span><span class="sxs-lookup"><span data-stu-id="9c777-305">The language of the template to create.</span></span> <span data-ttu-id="9c777-306">接受的语言因模板而异（请参阅[参数](#arguments)部分中的默认值）。</span><span class="sxs-lookup"><span data-stu-id="9c777-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9c777-307">对于某些模板无效。</span><span class="sxs-lookup"><span data-stu-id="9c777-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9c777-308">某些 shell 将 `#` 解释为特殊字符。</span><span class="sxs-lookup"><span data-stu-id="9c777-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9c777-309">在这些情况下，请将语言参数值括在引号中。</span><span class="sxs-lookup"><span data-stu-id="9c777-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="9c777-310">例如 `dotnet new console -lang "F#"`。</span><span class="sxs-lookup"><span data-stu-id="9c777-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="9c777-311">所创建的输出的名称。</span><span class="sxs-lookup"><span data-stu-id="9c777-311">The name for the created output.</span></span> <span data-ttu-id="9c777-312">如果未指定名称，使用的是当前目录的名称。</span><span class="sxs-lookup"><span data-stu-id="9c777-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="9c777-313">指定在安装期间要使用的 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="9c777-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="9c777-314">自 .NET Core 2.1 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9c777-315">用于放置生成的输出的位置。</span><span class="sxs-lookup"><span data-stu-id="9c777-315">Location to place the generated output.</span></span> <span data-ttu-id="9c777-316">默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="9c777-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="9c777-317">根据可用类型筛选模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-317">Filters templates based on available types.</span></span> <span data-ttu-id="9c777-318">预定义的值为 `project`、`item` 和 `other`。</span><span class="sxs-lookup"><span data-stu-id="9c777-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="9c777-319">在提供的 `PATH` 或 `NUGET_ID` 中卸载模板包。</span><span class="sxs-lookup"><span data-stu-id="9c777-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9c777-320">如果未指定 `<PATH|NUGET_ID>` 值，将显示所有当前安装的模板包及其关联的模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="9c777-321">指定 `NUGET_ID` 时，请勿包含版本号。</span><span class="sxs-lookup"><span data-stu-id="9c777-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="9c777-322">如果未指定此选项的参数，该命令将列出已安装的模板及其详细信息。</span><span class="sxs-lookup"><span data-stu-id="9c777-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9c777-323">若要使用 `PATH` 卸载模板，需要完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="9c777-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9c777-324">例如，C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp 有效，但是包含文件夹中的 ./GarciaSoftware.ConsoleTemplate.CSharp 无效 。</span><span class="sxs-lookup"><span data-stu-id="9c777-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="9c777-325">模板路径中不要包含最后的终止目录斜杠。</span><span class="sxs-lookup"><span data-stu-id="9c777-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="9c777-326">检查是否有可用于当前安装的模板包的更新并安装这些更新。</span><span class="sxs-lookup"><span data-stu-id="9c777-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="9c777-327">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="9c777-328">检查是否有可用于当前安装的模板包的更新。</span><span class="sxs-lookup"><span data-stu-id="9c777-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="9c777-329">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="9c777-330">模板选项</span><span class="sxs-lookup"><span data-stu-id="9c777-330">Template options</span></span>

<span data-ttu-id="9c777-331">每个项目模板都可能有附加选项。</span><span class="sxs-lookup"><span data-stu-id="9c777-331">Each project template may have additional options available.</span></span> <span data-ttu-id="9c777-332">核心模板有以下附加选项：</span><span class="sxs-lookup"><span data-stu-id="9c777-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="9c777-333">控制台</span><span class="sxs-lookup"><span data-stu-id="9c777-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-334">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-335">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="9c777-336">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-337">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-337">SDK version</span></span> | <span data-ttu-id="9c777-338">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-339">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-340">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9c777-341">在已创建的项目文件中设置 `LangVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="9c777-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9c777-342">例如，使用 `--langVersion 7.3` 以使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9c777-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="9c777-343">不支持 F#。</span><span class="sxs-lookup"><span data-stu-id="9c777-343">Not supported for F#.</span></span> <span data-ttu-id="9c777-344">自 .NET Core 2.2 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9c777-345">有关默认的 C# 版本列表，请参阅[默认](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9c777-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-346">如已指定，则在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="9c777-347">自 .NET Core 2.2 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="9c777-348">classlib</span><span class="sxs-lookup"><span data-stu-id="9c777-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-349">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-350">值：`netcoreapp<version>`（要创建 .NET Core 类库的话）或 `netstandard<version>`（要创建 .NET Standard 类库的话）。</span><span class="sxs-lookup"><span data-stu-id="9c777-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9c777-351">默认值为 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="9c777-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9c777-352">在已创建的项目文件中设置 `LangVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="9c777-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9c777-353">例如，使用 `--langVersion 7.3` 以使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9c777-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="9c777-354">不支持 F#。</span><span class="sxs-lookup"><span data-stu-id="9c777-354">Not supported for F#.</span></span> <span data-ttu-id="9c777-355">自 .NET Core 2.2 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9c777-356">有关默认的 C# 版本列表，请参阅[默认](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9c777-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-357">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="9c777-358">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="9c777-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-359">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-360">默认值为 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="9c777-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="9c777-361">自 .NET Core 3.1 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9c777-362">在已创建的项目文件中设置 `LangVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="9c777-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9c777-363">例如，使用 `--langVersion 7.3` 以使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9c777-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="9c777-364">有关默认的 C# 版本列表，请参阅[默认](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9c777-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-365">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="9c777-366">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="9c777-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="9c777-367">在已创建的项目文件中设置 `LangVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="9c777-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9c777-368">例如，使用 `--langVersion 7.3` 以使用 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="9c777-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="9c777-369">有关默认的 C# 版本列表，请参阅[默认](../../csharp/language-reference/configure-language-version.md#defaults)。</span><span class="sxs-lookup"><span data-stu-id="9c777-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-370">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="9c777-371">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="9c777-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-372">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-373">默认值为 `netcoreapp3.1`。</span><span class="sxs-lookup"><span data-stu-id="9c777-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="9c777-374">自 .NET Core 3.1 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-375">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-376">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="9c777-377">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="9c777-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-378">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-379">自 .NET Core 3.0 SDK 起可用的选项。</span><span class="sxs-lookup"><span data-stu-id="9c777-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="9c777-380">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-381">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-381">SDK version</span></span> | <span data-ttu-id="9c777-382">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-383">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-384">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="9c777-385">允许使用 [dotnet pack](dotnet-pack.md) 为项目打包。</span><span class="sxs-lookup"><span data-stu-id="9c777-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-386">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="9c777-387">nunit</span><span class="sxs-lookup"><span data-stu-id="9c777-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-388">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="9c777-389">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-390">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-390">SDK version</span></span> | <span data-ttu-id="9c777-391">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-392">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-393">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9c777-394">2.2</span><span class="sxs-lookup"><span data-stu-id="9c777-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="9c777-395">2.1</span><span class="sxs-lookup"><span data-stu-id="9c777-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="9c777-396">允许使用 [dotnet pack](dotnet-pack.md) 为项目打包。</span><span class="sxs-lookup"><span data-stu-id="9c777-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-397">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="9c777-398">页</span><span class="sxs-lookup"><span data-stu-id="9c777-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="9c777-399">已生成代码的命名空间。</span><span class="sxs-lookup"><span data-stu-id="9c777-399">Namespace for the generated code.</span></span> <span data-ttu-id="9c777-400">默认值为 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9c777-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="9c777-401">创建不含 PageModel 的页。</span><span class="sxs-lookup"><span data-stu-id="9c777-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="9c777-402">viewimports、proto</span><span class="sxs-lookup"><span data-stu-id="9c777-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="9c777-403">已生成代码的命名空间。</span><span class="sxs-lookup"><span data-stu-id="9c777-403">Namespace for the generated code.</span></span> <span data-ttu-id="9c777-404">默认值为 `MyApp.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="9c777-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="9c777-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="9c777-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="9c777-406">要使用的身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="9c777-406">The type of authentication to use.</span></span> <span data-ttu-id="9c777-407">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="9c777-407">The possible values are:</span></span>

  - <span data-ttu-id="9c777-408">`None` - 不进行身份验证（默认）。</span><span class="sxs-lookup"><span data-stu-id="9c777-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9c777-409">`Individual` - 个人身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="9c777-410">`IndividualB2C` - 使用 Azure AD B2C 进行个人身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9c777-411">`SingleOrg` - 对一个租户进行组织身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="9c777-412">`MultiOrg` - 对多个租户进行组织身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="9c777-413">`Windows` - Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9c777-414">要连接到的 Azure Active Directory B2C 实例。</span><span class="sxs-lookup"><span data-stu-id="9c777-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9c777-415">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-416">默认值为 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9c777-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9c777-417">此项目的登录和注册策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9c777-418">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="9c777-419">此项目的重置密码策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="9c777-420">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="9c777-421">此项目的编辑配置文件策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="9c777-422">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9c777-423">要连接到的 Azure Active Directory 实例。</span><span class="sxs-lookup"><span data-stu-id="9c777-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9c777-424">与 `SingleOrg` 或 `MultiOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9c777-425">默认值为 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9c777-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9c777-426">此项目的客户端 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-426">The Client ID for this project.</span></span> <span data-ttu-id="9c777-427">与 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9c777-428">默认值为 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9c777-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9c777-429">目录租户的域。</span><span class="sxs-lookup"><span data-stu-id="9c777-429">The domain for the directory tenant.</span></span> <span data-ttu-id="9c777-430">与 `SingleOrg` 或 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-431">默认值为 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9c777-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9c777-432">要连接到的目录的 TenantId ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9c777-433">与 `SingleOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9c777-434">默认值为 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9c777-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="9c777-435">重定向 URI 的应用程序基路径中的请求路径。</span><span class="sxs-lookup"><span data-stu-id="9c777-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9c777-436">与 `SingleOrg` 或 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-437">默认值为 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="9c777-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9c777-438">允许此应用程序对目录进行读取访问。</span><span class="sxs-lookup"><span data-stu-id="9c777-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9c777-439">仅适用于 `SingleOrg` 或 `MultiOrg` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-440">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="9c777-441">关闭 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c777-441">Turns off HTTPS.</span></span> <span data-ttu-id="9c777-442">此选项仅适用于 `Individual`、`IndividualB2C`、`SingleOrg` 和 `MultiOrg` 未用于 `--auth` 的情况。</span><span class="sxs-lookup"><span data-stu-id="9c777-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9c777-443">指定应使用 LocalDB，而不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9c777-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9c777-444">仅适用于 `Individual` 或 `IndividualB2C` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-445">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="9c777-446">Web</span><span class="sxs-lookup"><span data-stu-id="9c777-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-447">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-448">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-449">选项在 .NET Core 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9c777-450">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-451">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-451">SDK version</span></span> | <span data-ttu-id="9c777-452">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-453">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-454">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9c777-455">2.1</span><span class="sxs-lookup"><span data-stu-id="9c777-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="9c777-456">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="9c777-457">关闭 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c777-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="9c777-458">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="9c777-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="9c777-459">要使用的身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="9c777-459">The type of authentication to use.</span></span> <span data-ttu-id="9c777-460">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="9c777-460">The possible values are:</span></span>

  - <span data-ttu-id="9c777-461">`None` - 不进行身份验证（默认）。</span><span class="sxs-lookup"><span data-stu-id="9c777-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9c777-462">`Individual` - 个人身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="9c777-463">`IndividualB2C` - 使用 Azure AD B2C 进行个人身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9c777-464">`SingleOrg` - 对一个租户进行组织身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="9c777-465">`MultiOrg` - 对多个租户进行组织身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="9c777-466">`Windows` - Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9c777-467">要连接到的 Azure Active Directory B2C 实例。</span><span class="sxs-lookup"><span data-stu-id="9c777-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9c777-468">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-469">默认值为 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9c777-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9c777-470">此项目的登录和注册策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9c777-471">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="9c777-472">此项目的重置密码策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="9c777-473">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="9c777-474">此项目的编辑配置文件策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="9c777-475">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9c777-476">要连接到的 Azure Active Directory 实例。</span><span class="sxs-lookup"><span data-stu-id="9c777-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9c777-477">与 `SingleOrg` 或 `MultiOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9c777-478">默认值为 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9c777-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9c777-479">此项目的客户端 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-479">The Client ID for this project.</span></span> <span data-ttu-id="9c777-480">与 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9c777-481">默认值为 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9c777-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9c777-482">目录租户的域。</span><span class="sxs-lookup"><span data-stu-id="9c777-482">The domain for the directory tenant.</span></span> <span data-ttu-id="9c777-483">与 `SingleOrg` 或 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-484">默认值为 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9c777-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9c777-485">要连接到的目录的 TenantId ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9c777-486">与 `SingleOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9c777-487">默认值为 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9c777-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="9c777-488">重定向 URI 的应用程序基路径中的请求路径。</span><span class="sxs-lookup"><span data-stu-id="9c777-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9c777-489">与 `SingleOrg` 或 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-490">默认值为 `/signin-oidc`。</span><span class="sxs-lookup"><span data-stu-id="9c777-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9c777-491">允许此应用程序对目录进行读取访问。</span><span class="sxs-lookup"><span data-stu-id="9c777-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9c777-492">仅适用于 `SingleOrg` 或 `MultiOrg` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-493">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="9c777-494">关闭 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c777-494">Turns off HTTPS.</span></span> <span data-ttu-id="9c777-495">此选项仅适用于未使用 `Individual`、`IndividualB2C`、`SingleOrg` 和 `MultiOrg` 的情况。</span><span class="sxs-lookup"><span data-stu-id="9c777-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9c777-496">指定应使用 LocalDB，而不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9c777-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9c777-497">仅适用于 `Individual` 或 `IndividualB2C` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-498">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-499">自 .NET Core 3.0 SDK 起可用的选项。</span><span class="sxs-lookup"><span data-stu-id="9c777-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="9c777-500">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-501">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-501">SDK version</span></span> | <span data-ttu-id="9c777-502">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-503">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-504">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="9c777-505">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="9c777-506">在项目中添加 BrowserLink。</span><span class="sxs-lookup"><span data-stu-id="9c777-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="9c777-507">选项在 .NET Core 2.2 和 3.1 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="9c777-508">确定项目是否配置为在调试生成中使用 [Razor 运行时编译](/aspnet/core/mvc/views/view-compilation#runtime-compilation)。</span><span class="sxs-lookup"><span data-stu-id="9c777-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="9c777-509">自 .NET Core 3.1.201 SDK 起可用的选项。</span><span class="sxs-lookup"><span data-stu-id="9c777-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="9c777-510">angular、react</span><span class="sxs-lookup"><span data-stu-id="9c777-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="9c777-511">要使用的身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="9c777-511">The type of authentication to use.</span></span> <span data-ttu-id="9c777-512">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="9c777-513">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="9c777-513">The possible values are:</span></span>

  - <span data-ttu-id="9c777-514">`None` - 不进行身份验证（默认）。</span><span class="sxs-lookup"><span data-stu-id="9c777-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9c777-515">`Individual` - 个人身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-516">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-517">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="9c777-518">关闭 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c777-518">Turns off HTTPS.</span></span> <span data-ttu-id="9c777-519">仅当身份验证为 `None` 时，此选项才适用。</span><span class="sxs-lookup"><span data-stu-id="9c777-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9c777-520">指定应使用 LocalDB，而不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9c777-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9c777-521">仅适用于 `Individual` 或 `IndividualB2C` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-522">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-523">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-524">选项在 .NET Core 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9c777-525">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-526">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-526">SDK version</span></span> | <span data-ttu-id="9c777-527">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-528">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-529">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9c777-530">2.1</span><span class="sxs-lookup"><span data-stu-id="9c777-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="9c777-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="9c777-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-532">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-533">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-534">选项在 .NET Core 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9c777-535">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-536">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-536">SDK version</span></span> | <span data-ttu-id="9c777-537">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-538">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-539">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9c777-540">2.1</span><span class="sxs-lookup"><span data-stu-id="9c777-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="9c777-541">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="9c777-542">关闭 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c777-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="9c777-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="9c777-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c777-544">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="9c777-545">除了将组件添加到此库以外，还支持添加传统的 Razor 页面和视图。</span><span class="sxs-lookup"><span data-stu-id="9c777-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="9c777-546">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="9c777-547">webapi</span><span class="sxs-lookup"><span data-stu-id="9c777-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="9c777-548">要使用的身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="9c777-548">The type of authentication to use.</span></span> <span data-ttu-id="9c777-549">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="9c777-549">The possible values are:</span></span>

  - <span data-ttu-id="9c777-550">`None` - 不进行身份验证（默认）。</span><span class="sxs-lookup"><span data-stu-id="9c777-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="9c777-551">`IndividualB2C` - 使用 Azure AD B2C 进行个人身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="9c777-552">`SingleOrg` - 对一个租户进行组织身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="9c777-553">`Windows` - Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="9c777-554">要连接到的 Azure Active Directory B2C 实例。</span><span class="sxs-lookup"><span data-stu-id="9c777-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9c777-555">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9c777-556">默认值为 `https://login.microsoftonline.com/tfp/`。</span><span class="sxs-lookup"><span data-stu-id="9c777-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="9c777-557">此项目的登录和注册策略 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9c777-558">与 `IndividualB2C` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="9c777-559">要连接到的 Azure Active Directory 实例。</span><span class="sxs-lookup"><span data-stu-id="9c777-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9c777-560">与 `SingleOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9c777-561">默认值为 `https://login.microsoftonline.com/`。</span><span class="sxs-lookup"><span data-stu-id="9c777-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="9c777-562">此项目的客户端 ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-562">The Client ID for this project.</span></span> <span data-ttu-id="9c777-563">与 `IndividualB2C` 或 `SingleOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9c777-564">默认值为 `11111111-1111-1111-11111111111111111`。</span><span class="sxs-lookup"><span data-stu-id="9c777-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="9c777-565">目录租户的域。</span><span class="sxs-lookup"><span data-stu-id="9c777-565">The domain for the directory tenant.</span></span> <span data-ttu-id="9c777-566">与 `IndividualB2C` 或 `SingleOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9c777-567">默认值为 `qualified.domain.name`。</span><span class="sxs-lookup"><span data-stu-id="9c777-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="9c777-568">要连接到的目录的 TenantId ID。</span><span class="sxs-lookup"><span data-stu-id="9c777-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9c777-569">与 `SingleOrg` 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c777-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9c777-570">默认值为 `22222222-2222-2222-2222-222222222222`。</span><span class="sxs-lookup"><span data-stu-id="9c777-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="9c777-571">允许此应用程序对目录进行读取访问。</span><span class="sxs-lookup"><span data-stu-id="9c777-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="9c777-572">仅适用于 `SingleOrg` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="9c777-573">从生成的模板中排除 launchSettings.json。</span><span class="sxs-lookup"><span data-stu-id="9c777-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="9c777-574">关闭 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c777-574">Turns off HTTPS.</span></span> <span data-ttu-id="9c777-575">`app.UseHsts` 和 `app.UseHttpsRedirection` 未添加到 `Startup.Configure` 中。</span><span class="sxs-lookup"><span data-stu-id="9c777-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="9c777-576">此选项仅适用于 `IndividualB2C` 或 `SingleOrg` 未用于身份验证的情况。</span><span class="sxs-lookup"><span data-stu-id="9c777-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="9c777-577">指定应使用 LocalDB，而不使用 SQLite。</span><span class="sxs-lookup"><span data-stu-id="9c777-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9c777-578">仅适用于 `IndividualB2C` 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9c777-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c777-579">指定目标[框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9c777-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9c777-580">选项在 .NET Core 2.2 SDK 中不可用。</span><span class="sxs-lookup"><span data-stu-id="9c777-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="9c777-581">下表根据所使用的 SDK 版本号列出了默认值：</span><span class="sxs-lookup"><span data-stu-id="9c777-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="9c777-582">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="9c777-582">SDK version</span></span> | <span data-ttu-id="9c777-583">默认值</span><span class="sxs-lookup"><span data-stu-id="9c777-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="9c777-584">3.1</span><span class="sxs-lookup"><span data-stu-id="9c777-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="9c777-585">3.0</span><span class="sxs-lookup"><span data-stu-id="9c777-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="9c777-586">2.1</span><span class="sxs-lookup"><span data-stu-id="9c777-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="9c777-587">在项目创建期间不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="9c777-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="9c777-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="9c777-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="9c777-589">指定要在 global.json 文件中使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9c777-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="9c777-590">示例</span><span class="sxs-lookup"><span data-stu-id="9c777-590">Examples</span></span>

- <span data-ttu-id="9c777-591">通过指定模板名称，创建 C# 控制台应用程序项目：</span><span class="sxs-lookup"><span data-stu-id="9c777-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="9c777-592">在当前目录中创建 F# 控制台应用程序项目：</span><span class="sxs-lookup"><span data-stu-id="9c777-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="9c777-593">在指定的目录中创建 .NET Standard 类库项目：</span><span class="sxs-lookup"><span data-stu-id="9c777-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="9c777-594">在当前目录中新建没有设置身份验证的 ASP.NET Core C# MVC 项目：</span><span class="sxs-lookup"><span data-stu-id="9c777-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="9c777-595">创建新的 xUnit 项目：</span><span class="sxs-lookup"><span data-stu-id="9c777-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="9c777-596">列出可用于单页应用程序 (SPA) 模板的所有模板：</span><span class="sxs-lookup"><span data-stu-id="9c777-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="9c777-597">列出与“we”子字符串匹配的所有模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="9c777-598">找不到完全匹配，因此子字符串匹配针对短名称和名称列运行。</span><span class="sxs-lookup"><span data-stu-id="9c777-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="9c777-599">尝试调用与 ng 匹配的模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="9c777-600">如果无法确定单个匹配项，请列出部分匹配项的模板。</span><span class="sxs-lookup"><span data-stu-id="9c777-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="9c777-601">安装 ASP.NET Core 的 SPA 模板 2.0 版：</span><span class="sxs-lookup"><span data-stu-id="9c777-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="9c777-602">列出已安装的模板及其详细信息，包括如何卸载它们：</span><span class="sxs-lookup"><span data-stu-id="9c777-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="9c777-603">在当前目录中创建 global.json，将 SDK 版本设置为 3.1.101：</span><span class="sxs-lookup"><span data-stu-id="9c777-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="9c777-604">请参阅</span><span class="sxs-lookup"><span data-stu-id="9c777-604">See also</span></span>

- [<span data-ttu-id="9c777-605">dotnet new 自定义模板</span><span class="sxs-lookup"><span data-stu-id="9c777-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="9c777-606">创建 dotnet new 自定义模板</span><span class="sxs-lookup"><span data-stu-id="9c777-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="9c777-607">dotnet/dotnet-template-samples GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="9c777-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="9c777-608">dotnet new 可用模板</span><span class="sxs-lookup"><span data-stu-id="9c777-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
