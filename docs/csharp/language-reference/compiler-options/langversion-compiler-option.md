---
title: -langversion（C# 编译器选项）
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: fd05802008a20267fea54f14bae4c8deb0e21c65
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656199"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="4bc10-102">-langversion（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="4bc10-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="4bc10-103">使编译器仅接受包含在所选 C# 语言规范中的语法。</span><span class="sxs-lookup"><span data-stu-id="4bc10-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bc10-104">语法</span><span class="sxs-lookup"><span data-stu-id="4bc10-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="4bc10-105">自变量</span><span class="sxs-lookup"><span data-stu-id="4bc10-105">Arguments</span></span>

`option`

<span data-ttu-id="4bc10-106">以下为有效值：</span><span class="sxs-lookup"><span data-stu-id="4bc10-106">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="4bc10-107">默认语言版本依赖于应用程序的目标框架以及所安装的 SDK 或 Visual Studio 的版本。</span><span class="sxs-lookup"><span data-stu-id="4bc10-107">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="4bc10-108">有关这些规则的定义，请参见[配置语言版本](../configure-language-version.md#defaults)一文。</span><span class="sxs-lookup"><span data-stu-id="4bc10-108">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bc10-109">备注</span><span class="sxs-lookup"><span data-stu-id="4bc10-109">Remarks</span></span>

<span data-ttu-id="4bc10-110">C# 应用程序引用的元数据不受 -langversion 编译器选项约束。</span><span class="sxs-lookup"><span data-stu-id="4bc10-110">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="4bc10-111">每个版本的 C# 编译器都包含语言规范的扩展，因此 -langversion 不提供早期版本编译器的同等功能。</span><span class="sxs-lookup"><span data-stu-id="4bc10-111">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="4bc10-112">此外，虽然 C# 版本更新通常与主要的 .NET Framework 版本一致，但新的语法和功能不一定绑定到该特定的 Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="4bc10-112">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="4bc10-113">虽然新功能肯定需要与 C# 修订版一起发布的新编译器更新，但每项具体功能都有自己的最小 .NET API 或公共语言运行时要求，这些要求通过包括 NuGet 包或其他库允许功能在下层框架上运行。</span><span class="sxs-lookup"><span data-stu-id="4bc10-113">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="4bc10-114">无论使用哪一项 -langversion 设置，请使用当前版本的公共语言运行时来创建 .exe 或 .dll。</span><span class="sxs-lookup"><span data-stu-id="4bc10-114">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="4bc10-115">友元程序集和 [-moduleassemblyname（C# 编译器选项）](./moduleassemblyname-compiler-option.md)是一个例外，它们在 -langversion:ISO-1 下工作。</span><span class="sxs-lookup"><span data-stu-id="4bc10-115">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="4bc10-116">如需了解指定 C# 语言版本的其他方式，请参阅[选择 C# 语言版本](../configure-language-version.md)一文。</span><span class="sxs-lookup"><span data-stu-id="4bc10-116">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="4bc10-117">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="4bc10-117">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4bc10-118">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="4bc10-118">C# language specification</span></span>

| <span data-ttu-id="4bc10-119">Version</span><span class="sxs-lookup"><span data-stu-id="4bc10-119">Version</span></span>          | <span data-ttu-id="4bc10-120">链接</span><span class="sxs-lookup"><span data-stu-id="4bc10-120">Link</span></span>                       | <span data-ttu-id="4bc10-121">描述</span><span class="sxs-lookup"><span data-stu-id="4bc10-121">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="4bc10-122">C# 7.0 和更高版本</span><span class="sxs-lookup"><span data-stu-id="4bc10-122">C# 7.0 and later</span></span> |                            | <span data-ttu-id="4bc10-123">当前不可用</span><span class="sxs-lookup"><span data-stu-id="4bc10-123">Not currently available</span></span>                                                 |
| <span data-ttu-id="4bc10-124">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-124">C# 6.0</span></span>           | <span data-ttu-id="4bc10-125">[链接][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="4bc10-125">[Link][csharp-6]</span></span>           | <span data-ttu-id="4bc10-126">C# 语言规范版本 6 - 非官方草稿：.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="4bc10-126">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="4bc10-127">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-127">C# 5.0</span></span>           | <span data-ttu-id="4bc10-128">[下载 PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="4bc10-128">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="4bc10-129">标准 ECMA-334 第 5 版</span><span class="sxs-lookup"><span data-stu-id="4bc10-129">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="4bc10-130">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-130">C# 3.0</span></span>           | <span data-ttu-id="4bc10-131">[下载 DOC][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="4bc10-131">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="4bc10-132">C# 语言规范版本 3.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="4bc10-132">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="4bc10-133">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-133">C# 2.0</span></span>           | <span data-ttu-id="4bc10-134">[下载 PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="4bc10-134">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="4bc10-135">标准 ECMA-334 第 4 版</span><span class="sxs-lookup"><span data-stu-id="4bc10-135">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="4bc10-136">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="4bc10-136">C# 1.2</span></span>           | <span data-ttu-id="4bc10-137">[下载 DOC][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="4bc10-137">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="4bc10-138">C# 语言规范版本 1.2：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="4bc10-138">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="4bc10-139">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-139">C# 1.0</span></span>           | <span data-ttu-id="4bc10-140">[下载 DOC][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="4bc10-140">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="4bc10-141">C# 语言规范版本 1.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="4bc10-141">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="4bc10-142">支持所有语言功能所需的最低 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="4bc10-142">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="4bc10-143">下表列出了支持相应语言版本的 C# 编译器的 SDK 的最低版本：</span><span class="sxs-lookup"><span data-stu-id="4bc10-143">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="4bc10-144">C# 版本</span><span class="sxs-lookup"><span data-stu-id="4bc10-144">C# version</span></span> | <span data-ttu-id="4bc10-145">最低 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="4bc10-145">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="4bc10-146">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-146">C# 8.0</span></span>     | <span data-ttu-id="4bc10-147">Microsoft Visual Studio/生成工具 2019，版本 16.3 或 .NET Core 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="4bc10-147">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="4bc10-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4bc10-148">C# 7.3</span></span>     | <span data-ttu-id="4bc10-149">Microsoft Visual Studio/生成工具 2017，版本 15.7</span><span class="sxs-lookup"><span data-stu-id="4bc10-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="4bc10-150">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="4bc10-150">C# 7.2</span></span>     | <span data-ttu-id="4bc10-151">Microsoft Visual Studio/生成工具 2017，版本 15.5</span><span class="sxs-lookup"><span data-stu-id="4bc10-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="4bc10-152">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="4bc10-152">C# 7.1</span></span>     | <span data-ttu-id="4bc10-153">Microsoft Visual Studio/生成工具 2017，版本 15.3</span><span class="sxs-lookup"><span data-stu-id="4bc10-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="4bc10-154">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="4bc10-154">C# 7.0</span></span>     | <span data-ttu-id="4bc10-155">Microsoft Visual Studio/生成工具 2017</span><span class="sxs-lookup"><span data-stu-id="4bc10-155">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="4bc10-156">C# 6</span><span class="sxs-lookup"><span data-stu-id="4bc10-156">C# 6</span></span>       | <span data-ttu-id="4bc10-157">Microsoft Visual Studio/生成工具 2015</span><span class="sxs-lookup"><span data-stu-id="4bc10-157">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="4bc10-158">C# 5</span><span class="sxs-lookup"><span data-stu-id="4bc10-158">C# 5</span></span>       | <span data-ttu-id="4bc10-159">Microsoft Visual Studio/生成工具 2012 或捆绑的 .NET Framework 4.5 编译器</span><span class="sxs-lookup"><span data-stu-id="4bc10-159">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="4bc10-160">C# 4</span><span class="sxs-lookup"><span data-stu-id="4bc10-160">C# 4</span></span>       | <span data-ttu-id="4bc10-161">Microsoft Visual Studio/生成工具 2010 或捆绑的 .NET Framework 4.0 编译器</span><span class="sxs-lookup"><span data-stu-id="4bc10-161">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="4bc10-162">C# 3</span><span class="sxs-lookup"><span data-stu-id="4bc10-162">C# 3</span></span>       | <span data-ttu-id="4bc10-163">Microsoft Visual Studio/生成工具 2008 或捆绑的 .NET Framework 3.5 编译器</span><span class="sxs-lookup"><span data-stu-id="4bc10-163">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="4bc10-164">C# 2</span><span class="sxs-lookup"><span data-stu-id="4bc10-164">C# 2</span></span>       | <span data-ttu-id="4bc10-165">Microsoft Visual Studio/生成工具 2005 或捆绑的 .Net Framework 2.0 编译器</span><span class="sxs-lookup"><span data-stu-id="4bc10-165">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="4bc10-166">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="4bc10-166">C# 1.0/1.2</span></span> | <span data-ttu-id="4bc10-167">Microsoft Visual Studio/生成工具 .NET 2002 或捆绑的 .NET Framework 1.0 编译器</span><span class="sxs-lookup"><span data-stu-id="4bc10-167">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="4bc10-168">请参阅</span><span class="sxs-lookup"><span data-stu-id="4bc10-168">See also</span></span>

- [<span data-ttu-id="4bc10-169">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="4bc10-169">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="4bc10-170">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="4bc10-170">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
