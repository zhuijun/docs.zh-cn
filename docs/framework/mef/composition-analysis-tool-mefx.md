---
title: 结构分析工具 (Mefx)
description: 了解组合分析工具 (Mefx)，该工具用于分析包含 .NET 中的 Managed Extensibility Framework (MEF) 部件的 DLL 和 EXE 文件。
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: abb1459afc5aeb2d39ee553c62fe382bb7af58d5
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281272"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="b9bea-103">结构分析工具 (Mefx)</span><span class="sxs-lookup"><span data-stu-id="b9bea-103">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="b9bea-104">组合分析工具 (Mefx) 是一款命令行应用程序，用于分析包含 Managed Extensibility Framework (MEF) 部件的库 (.dll) 和应用程序 (.exe) 文件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-104">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="b9bea-105">Mefx 的主要用途是为开发人员提供一种无需向应用程序本身添加繁琐的跟踪代码即可诊断其 MEF 应用程序中组合失败情况的方法。</span><span class="sxs-lookup"><span data-stu-id="b9bea-105">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="b9bea-106">它还可用于帮助你了解第三方所提供库中的部件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-106">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="b9bea-107">本主题介绍如何使用 Mefx，并提供其语法参考。</span><span class="sxs-lookup"><span data-stu-id="b9bea-107">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a><span data-ttu-id="b9bea-108">获取 Mefx</span><span class="sxs-lookup"><span data-stu-id="b9bea-108">Getting Mefx</span></span>  
 <span data-ttu-id="b9bea-109">可在 GitHub 的 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0) 上获取 Mefx。</span><span class="sxs-lookup"><span data-stu-id="b9bea-109">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="b9bea-110">只需下载并解压缩该工具。</span><span class="sxs-lookup"><span data-stu-id="b9bea-110">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a><span data-ttu-id="b9bea-111">基本语法</span><span class="sxs-lookup"><span data-stu-id="b9bea-111">Basic Syntax</span></span>  
 <span data-ttu-id="b9bea-112">采用以下格式从命令行调用 Mefx：</span><span class="sxs-lookup"><span data-stu-id="b9bea-112">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="b9bea-113">第一组参数指定要从其加载部件进行分析的文件和目录。</span><span class="sxs-lookup"><span data-stu-id="b9bea-113">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="b9bea-114">使用 `/file:` 开关指定文件，使用 `/directory:` 开关指定目录。</span><span class="sxs-lookup"><span data-stu-id="b9bea-114">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="b9bea-115">你可以指定多个文件或目录，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="b9bea-115">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="b9bea-116">每个 .dll 或 .exe 应仅加载一次。</span><span class="sxs-lookup"><span data-stu-id="b9bea-116">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="b9bea-117">如果多次加载文件，则该工具可能返回错误信息。</span><span class="sxs-lookup"><span data-stu-id="b9bea-117">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="b9bea-118">列出文件和目录后，必须指定一个命令并为该命令指定一个选项。</span><span class="sxs-lookup"><span data-stu-id="b9bea-118">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a><span data-ttu-id="b9bea-119">列出可用部件</span><span class="sxs-lookup"><span data-stu-id="b9bea-119">Listing Available Parts</span></span>  
 <span data-ttu-id="b9bea-120">使用 `/parts` 操作列出所加载文件中声明的所有部件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-120">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="b9bea-121">此时将显示一个简单的部件名称列表。</span><span class="sxs-lookup"><span data-stu-id="b9bea-121">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="b9bea-122">有关部件的详细信息，请使用 `/verbose` 选项。</span><span class="sxs-lookup"><span data-stu-id="b9bea-122">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="b9bea-123">这将输出所有可用部件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b9bea-123">This will output more information for all available parts.</span></span> <span data-ttu-id="b9bea-124">若要获取有关单个部件的详细信息，请使用 `/type` 操作，而不是 `/parts`。</span><span class="sxs-lookup"><span data-stu-id="b9bea-124">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a><span data-ttu-id="b9bea-125">列出导入和导出的部件</span><span class="sxs-lookup"><span data-stu-id="b9bea-125">Listing Imports and Exports</span></span>  
 <span data-ttu-id="b9bea-126">`/imports` 和 `/exports` 操作分别将列出所有导入的部件和所有导出的部件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-126">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="b9bea-127">你还可以通过使用 `/importers` 或 `/exporters` 操作列出导入或导出特殊类型的部件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-127">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="b9bea-128">你还可以向这些操作应用 `/verbose` 选项。</span><span class="sxs-lookup"><span data-stu-id="b9bea-128">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a><span data-ttu-id="b9bea-129">查找拒绝的部件</span><span class="sxs-lookup"><span data-stu-id="b9bea-129">Finding Rejected Parts</span></span>  
 <span data-ttu-id="b9bea-130">一旦加载可用部件，Mefx 将使用 MEF 组合引擎将它们组合起来。</span><span class="sxs-lookup"><span data-stu-id="b9bea-130">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="b9bea-131">不能成功组合的部件称为 *“拒绝的部件”* 。</span><span class="sxs-lookup"><span data-stu-id="b9bea-131">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="b9bea-132">若要列出所有拒绝的部件，请使用 `/rejected` 操作。</span><span class="sxs-lookup"><span data-stu-id="b9bea-132">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="b9bea-133">你可以结合使用 `/verbose` 选项和 `/rejected` 选项打印关于拒绝的部件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b9bea-133">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="b9bea-134">在下面的示例中， `ClassLibrary1` DLL 包含 `AddIn` 部件，该部件导入 `MemberPart` 和 `ChainOne` 部件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-134">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="b9bea-135">`ChainOne` 导入 `ChainTwo`，但 `ChainTwo` 不存在。</span><span class="sxs-lookup"><span data-stu-id="b9bea-135">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="b9bea-136">这意味着， `ChainOne` 被拒绝，这将导致 `AddIn` 被拒绝。</span><span class="sxs-lookup"><span data-stu-id="b9bea-136">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="b9bea-137">下面的示例显示上一条命令的完整输出：</span><span class="sxs-lookup"><span data-stu-id="b9bea-137">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="b9bea-138">相关信息包含在 `[Exception]` 和 `[Unsuitable]` 结果中。</span><span class="sxs-lookup"><span data-stu-id="b9bea-138">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="b9bea-139">`[Exception]` 结果提供有关部件为何被拒绝的信息。</span><span class="sxs-lookup"><span data-stu-id="b9bea-139">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="b9bea-140">`[Unsuitable]` 结果指示以其他方式匹配的部件为何不能填充导入；在本例中，是因为该部件本身被拒绝而不能导入。</span><span class="sxs-lookup"><span data-stu-id="b9bea-140">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a><span data-ttu-id="b9bea-141">分析主要原因</span><span class="sxs-lookup"><span data-stu-id="b9bea-141">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="b9bea-142">如果多个部件位于一个长的依赖关系链中，则关系链底部涉及部件的问题可能会导致整个关系链被拒绝。</span><span class="sxs-lookup"><span data-stu-id="b9bea-142">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="b9bea-143">由于失败的根源并不总是显而易见的，诊断这些问题可能很困难。</span><span class="sxs-lookup"><span data-stu-id="b9bea-143">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="b9bea-144">若要帮助解决问题，可以使用 `/causes` 操作，该操作将尝试查找任何级联拒绝的根源。</span><span class="sxs-lookup"><span data-stu-id="b9bea-144">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="b9bea-145">在前面的示例中使用 `/causes` 操作将仅列出 `ChainOne`的信息，其未填充导入是 `AddIn`被拒的根源。</span><span class="sxs-lookup"><span data-stu-id="b9bea-145">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="b9bea-146">`/causes` 操作可在正常选项和 `/verbose` 选项中使用。</span><span class="sxs-lookup"><span data-stu-id="b9bea-146">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9bea-147">在大多数情况下，Mefx 将能够诊断级联失败的根源。</span><span class="sxs-lookup"><span data-stu-id="b9bea-147">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="b9bea-148">但是，在以编程方式将部件添加到容器的情况下，在涉及层次结构容器的情况下，或者在涉及自定义 `ExportProvider` 实现的情况下，Mefx 将不能诊断原因。</span><span class="sxs-lookup"><span data-stu-id="b9bea-148">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="b9bea-149">一般情况下，因尽可能避免前面所述的各种情况，因为失败原因通常很难诊断。</span><span class="sxs-lookup"><span data-stu-id="b9bea-149">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>
## <a name="white-lists"></a><span data-ttu-id="b9bea-150">白名单</span><span class="sxs-lookup"><span data-stu-id="b9bea-150">White Lists</span></span>  
 <span data-ttu-id="b9bea-151">使用 `/whitelist` 选项可以指定一个文本文件，其中列出预期将被拒绝的部件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-151">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="b9bea-152">意外的拒绝则将被标记出来。</span><span class="sxs-lookup"><span data-stu-id="b9bea-152">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="b9bea-153">在分析不完整的库或分析缺少某些依赖关系的子库时，这将很有帮助。</span><span class="sxs-lookup"><span data-stu-id="b9bea-153">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="b9bea-154">`/whitelist` 选项可应用于 `/rejected` 或 `/causes` 操作。</span><span class="sxs-lookup"><span data-stu-id="b9bea-154">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="b9bea-155">请考虑名为 test.txt 且包含文本“ClassLibrary1.ChainOne”的文件。</span><span class="sxs-lookup"><span data-stu-id="b9bea-155">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="b9bea-156">如果在前面的示例中将 `/rejected` 操作用于 `/whitelist` 选项，它将生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="b9bea-156">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
