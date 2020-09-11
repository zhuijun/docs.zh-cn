---
title: 剪裁选项
description: 了解如何控制自包含应用的剪裁。
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 42e98f9ede004f06221d2df5ecd076500061e37d
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465411"
---
# <a name="trimming-options"></a><span data-ttu-id="77d81-103">剪裁选项</span><span class="sxs-lookup"><span data-stu-id="77d81-103">Trimming options</span></span>

<span data-ttu-id="77d81-104">以下 MSBuild 属性和项会影响[剪裁的独立部署](trim-self-contained.md)行为。</span><span class="sxs-lookup"><span data-stu-id="77d81-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="77d81-105">一些选项提及 `ILLink`，这是实现剪裁的基础工具的名称。</span><span class="sxs-lookup"><span data-stu-id="77d81-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="77d81-106">有关 `ILLink` 命令行工具的详细信息，请参阅 [illink 选项](https://github.com/mono/linker/blob/master/docs/illink-options.md)。</span><span class="sxs-lookup"><span data-stu-id="77d81-106">More information about the `ILLink` command-line tool can be found at [illink options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="77d81-107">启用剪裁</span><span class="sxs-lookup"><span data-stu-id="77d81-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="77d81-108">在发布期间使用 SDK 定义的默认设置来启用剪裁。</span><span class="sxs-lookup"><span data-stu-id="77d81-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="77d81-109">使用 `Microsoft.NET.Sdk` 时，将对 netcoreapp 运行时包中的框架程序集执行程序集级剪裁。</span><span class="sxs-lookup"><span data-stu-id="77d81-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="77d81-110">而不会剪裁应用程序代码和非框架库。</span><span class="sxs-lookup"><span data-stu-id="77d81-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="77d81-111">其他 SDK 可定义不同的默认值。</span><span class="sxs-lookup"><span data-stu-id="77d81-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="77d81-112">剪裁粒度</span><span class="sxs-lookup"><span data-stu-id="77d81-112">Trimming granularity</span></span>

<span data-ttu-id="77d81-113">以下粒度设置控制如何丢弃未充分利用的 IL。</span><span class="sxs-lookup"><span data-stu-id="77d81-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="77d81-114">这可设置为属性，也可设置为[单个程序集](#trimmed-assemblies)的元数据。</span><span class="sxs-lookup"><span data-stu-id="77d81-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="77d81-115">启用程序集级剪裁；如果使用程序集的任何部分（以静态理解的方式），则将保留整个程序集。</span><span class="sxs-lookup"><span data-stu-id="77d81-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="77d81-116">启用成员级剪裁，这会从类型中删除未使用的成员。</span><span class="sxs-lookup"><span data-stu-id="77d81-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="77d81-117">具有 `<IsTrimmable>true</IsTrimmable>` 元数据但没有显式 `TrimMode` 的程序集将使用全局 `TrimMode`。</span><span class="sxs-lookup"><span data-stu-id="77d81-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="77d81-118">`Microsoft.NET.Sdk` 的默认 `TrimMode` 为 `copyused`。</span><span class="sxs-lookup"><span data-stu-id="77d81-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="77d81-119">剪裁后的程序集</span><span class="sxs-lookup"><span data-stu-id="77d81-119">Trimmed assemblies</span></span>

<span data-ttu-id="77d81-120">发布剪裁后的应用时，SDK 将计算名为 `ManagedAssemblyToLink` 的 `ItemGroup`，这表示要进行剪裁处理的文件集。</span><span class="sxs-lookup"><span data-stu-id="77d81-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="77d81-121">`ManagedAssemblyToLink` 可能具有控制每个程序集剪裁行为的元数据。</span><span class="sxs-lookup"><span data-stu-id="77d81-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="77d81-122">若要设置此元数据，请在内置的 `PrepareForILLink` 目标运行之前创建一个目标。</span><span class="sxs-lookup"><span data-stu-id="77d81-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="77d81-123">下面的示例演示如何启用 `MyAssembly` 的剪裁。</span><span class="sxs-lookup"><span data-stu-id="77d81-123">The following example shows how to enable trimming of `MyAssembly`.</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="77d81-124">请勿在 `ManagedAssemblyToLink` 中添加或移除项，因为 SDK 会在发布过程中计算此集，并期望它没有发生更改。</span><span class="sxs-lookup"><span data-stu-id="77d81-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="77d81-125">支持的元数据为：</span><span class="sxs-lookup"><span data-stu-id="77d81-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="77d81-126">控制是否剪裁给定的程序集。</span><span class="sxs-lookup"><span data-stu-id="77d81-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="77d81-127">`<TrimMode>copyused</TrimMode>` 或 `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="77d81-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="77d81-128">控制此程序集的[剪裁粒度](#trimming-granularity)。</span><span class="sxs-lookup"><span data-stu-id="77d81-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="77d81-129">这优先于全局 `TrimMode`。</span><span class="sxs-lookup"><span data-stu-id="77d81-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="77d81-130">在程序集上设置 `TrimMode` 意味着 `<IsTrimmable>true</IsTrimmable>`。</span><span class="sxs-lookup"><span data-stu-id="77d81-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="77d81-131">根程序集</span><span class="sxs-lookup"><span data-stu-id="77d81-131">Root assemblies</span></span>

<span data-ttu-id="77d81-132">所有没有 `<IsTrimmable>true</IsTrimmable>` 的程序集都被视为分析的根，这意味着将保留它们及其所有静态理解的依赖项。</span><span class="sxs-lookup"><span data-stu-id="77d81-132">All assemblies that do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="77d81-133">其他程序集的名称可能是根（无 `.dll` 扩展名）：</span><span class="sxs-lookup"><span data-stu-id="77d81-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="77d81-134">根描述符</span><span class="sxs-lookup"><span data-stu-id="77d81-134">Root descriptors</span></span>

<span data-ttu-id="77d81-135">指定分析的根的另一种方法是使用链接器[描述符格式](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="77d81-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="77d81-136">这使你可以查找特定的成员而非整个程序集。</span><span class="sxs-lookup"><span data-stu-id="77d81-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="77d81-137">例如，`MyRoots.xml` 可能会查找由应用程序动态访问的特定方法：</span><span class="sxs-lookup"><span data-stu-id="77d81-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="77d81-138">分析警告</span><span class="sxs-lookup"><span data-stu-id="77d81-138">Analysis warnings</span></span>

<span data-ttu-id="77d81-139">剪裁将删除不可静态访问的 IL。</span><span class="sxs-lookup"><span data-stu-id="77d81-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="77d81-140">使用反射或其他模式来创建动态依赖项的应用可能会因剪裁而中断。</span><span class="sxs-lookup"><span data-stu-id="77d81-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="77d81-141">警告此类模式：</span><span class="sxs-lookup"><span data-stu-id="77d81-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="77d81-142">启用剪裁分析警告。</span><span class="sxs-lookup"><span data-stu-id="77d81-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="77d81-143">这将包括有关整个应用的警告，其中包括你自己的代码、库代码以及框架代码。</span><span class="sxs-lookup"><span data-stu-id="77d81-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="77d81-144">警告版本</span><span class="sxs-lookup"><span data-stu-id="77d81-144">Warning versions</span></span>

<span data-ttu-id="77d81-145">剪裁分析使用的 [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) 属性可跨 SDK 控制分析警告版本。</span><span class="sxs-lookup"><span data-stu-id="77d81-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="77d81-146">还有一个可独立控制剪裁分析警告版本的属性（类似于编译器 `WarningLevel`）：</span><span class="sxs-lookup"><span data-stu-id="77d81-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="77d81-147">仅发出给定级别或更低级别的警告。</span><span class="sxs-lookup"><span data-stu-id="77d81-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="77d81-148">这可以是 `9999`，以包含所有警告版本。</span><span class="sxs-lookup"><span data-stu-id="77d81-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="77d81-149">取消警告</span><span class="sxs-lookup"><span data-stu-id="77d81-149">Suppressing warnings</span></span>

<span data-ttu-id="77d81-150">可以使用工具链遵循的常用 MSBuild 属性来取消单个[警告代码](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes)，包括 `NoWarn`、`WarningsAsErrors`、`WarningsNotAsErrors` 和 `TreatWarningsAsErrors`。</span><span class="sxs-lookup"><span data-stu-id="77d81-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="77d81-151">还有另一个选项，可单独控制 ILLink 警告即错误的行为：</span><span class="sxs-lookup"><span data-stu-id="77d81-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="77d81-152">请勿将 ILLink 警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="77d81-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="77d81-153">在全局将编译器警告视为错误时，这对于避免将剪裁分析警告转换为错误可能很有用。</span><span class="sxs-lookup"><span data-stu-id="77d81-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="77d81-154">删除符号</span><span class="sxs-lookup"><span data-stu-id="77d81-154">Removing symbols</span></span>

<span data-ttu-id="77d81-155">通常会对符号进行剪裁，以匹配剪裁的程序集。</span><span class="sxs-lookup"><span data-stu-id="77d81-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="77d81-156">还可以删除所有符号：</span><span class="sxs-lookup"><span data-stu-id="77d81-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="77d81-157">删除剪裁后的应用程序中的符号，包括嵌入的 PDB 和单独的 PDB 文件。</span><span class="sxs-lookup"><span data-stu-id="77d81-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="77d81-158">这同时适用于应用程序代码以及符号附带的任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="77d81-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="77d81-159">SDK 还可使用属性 `DebuggerSupport` 来禁用调试器支持。</span><span class="sxs-lookup"><span data-stu-id="77d81-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="77d81-160">禁用调试器支持时，剪裁将自动删除符号（`TrimmerRemoveSymbols` 将默认为 true）。</span><span class="sxs-lookup"><span data-stu-id="77d81-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>
