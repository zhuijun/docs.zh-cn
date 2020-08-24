---
title: .NET Framework 中的过时功能
description: 了解 .NET 类库如何将成员标记为已过时。 了解 ObsoleteAttribute 属性，并了解如何处理过时的类型和成员等。
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 188d9184476e58fb679421467cd68e2ea8a8a101
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558863"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="7b942-104">.NET Framework 类库中过时的内容</span><span class="sxs-lookup"><span data-stu-id="7b942-104">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="7b942-105">.NET 随时间变化。</span><span class="sxs-lookup"><span data-stu-id="7b942-105">.NET changes over time.</span></span> <span data-ttu-id="7b942-106">每个新版本都添加了提供新功能的新类型和类型成员。</span><span class="sxs-lookup"><span data-stu-id="7b942-106">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="7b942-107">现有类型和成员也会随着时间推移而变化。</span><span class="sxs-lookup"><span data-stu-id="7b942-107">Existing types and their members also change over time.</span></span> <span data-ttu-id="7b942-108">例如，某些类型变得不太重要，因为它们支持的技术由新技术所替代，而某些方法由在某种程度上更高级的新方法所取代。</span><span class="sxs-lookup"><span data-stu-id="7b942-108">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are superior in some way.</span></span>

<span data-ttu-id="7b942-109">.NET Framework 和公共语言运行时会努力支持向后兼容（允许使用一个版本的 .NET Framework 开发的应用程序在下一版本的 .NET Framework 上运行）。</span><span class="sxs-lookup"><span data-stu-id="7b942-109">.NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of .NET Framework to run on the next version of .NET Framework).</span></span> <span data-ttu-id="7b942-110">这便难以仅仅删除类型或类型成员。</span><span class="sxs-lookup"><span data-stu-id="7b942-110">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="7b942-111">相反，.NET 通过将类型或类型成员标记为已过时或已弃用，来指示应不再使用它。</span><span class="sxs-lookup"><span data-stu-id="7b942-111">Instead, .NET indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="7b942-112">弃用某个类型或成员涉及对它进行标记，以便开发人员知道它将消失，从而有时间来响应其删除。</span><span class="sxs-lookup"><span data-stu-id="7b942-112">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="7b942-113">但是，使用该类型或成员的现有代码会继续在新版本的 .NET 中运行。</span><span class="sxs-lookup"><span data-stu-id="7b942-113">However, existing code that uses the type or member continues to run in the new version of .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="7b942-114">术语“已过时”和“已弃用”在应用于 .NET 类型和成员时含义相同。</span><span class="sxs-lookup"><span data-stu-id="7b942-114">The terms *obsolete* and *deprecated* have the same meaning when applied to .NET types and members.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="7b942-115">ObsoleteAttribute 特性</span><span class="sxs-lookup"><span data-stu-id="7b942-115">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="7b942-116">.NET Framework 通过使用 <xref:System.ObsoleteAttribute> 特性标记类型或类型成员来指示它已过时。</span><span class="sxs-lookup"><span data-stu-id="7b942-116">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="7b942-117">将该特性应用于某个类型或成员指示该类型或成员会在将来某个版本的 .NET Framework 中删除，但不会破坏使用该成员的已编译代码。</span><span class="sxs-lookup"><span data-stu-id="7b942-117">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="7b942-118">除了指示类型或类型成员已过时之外，<xref:System.ObsoleteAttribute> 还定义编译器如何处理包含该类型或成员的源代码。</span><span class="sxs-lookup"><span data-stu-id="7b942-118">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="7b942-119">编译器可以编译代码但发出警告消息，也可以将该类型或成员的使用视为错误。</span><span class="sxs-lookup"><span data-stu-id="7b942-119">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="7b942-120">在第一种情况下，代码可以成功编译，但警告消息会指示类型或成员已过时。</span><span class="sxs-lookup"><span data-stu-id="7b942-120">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="7b942-121">在第二种情况下，编译会失败。</span><span class="sxs-lookup"><span data-stu-id="7b942-121">In the second case, compilation fails.</span></span>

<span data-ttu-id="7b942-122">即使编译生成错误而不是警告消息，<xref:System.ObsoleteAttribute> 也不会影响运行时行为。</span><span class="sxs-lookup"><span data-stu-id="7b942-122">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="7b942-123">也就是说，使用该类型或成员并且已成功编译的应用程序会始终成功运行。</span><span class="sxs-lookup"><span data-stu-id="7b942-123">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="7b942-124">只有重新编译使用该类型或成员的应用程序的尝试会失败。</span><span class="sxs-lookup"><span data-stu-id="7b942-124">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="7b942-125">如何处理已过时的类型和成员</span><span class="sxs-lookup"><span data-stu-id="7b942-125">How to handle obsolete types and members</span></span>

<span data-ttu-id="7b942-126">升级和重新编译现有代码时，使用会在应用程序中生成编译器警告的已过时类型或成员是完全可以接受的。</span><span class="sxs-lookup"><span data-stu-id="7b942-126">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="7b942-127">但是，应查看编译器警告消息，以确定是否应更改应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="7b942-127">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="7b942-128">如果该消息不指向合适的替代方法，则应执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="7b942-128">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="7b942-129">通过删除该类型或成员的使用（如果可能）来更改代码。</span><span class="sxs-lookup"><span data-stu-id="7b942-129">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="7b942-130">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7b942-130">-or-</span></span>

- <span data-ttu-id="7b942-131">查看有关此技术领域的文档，以确定如何响应弃用情况。</span><span class="sxs-lookup"><span data-stu-id="7b942-131">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="7b942-132">可以选择不针对更高版本的 .NET Framework 重新编译现有代码。</span><span class="sxs-lookup"><span data-stu-id="7b942-132">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="7b942-133">相反，可以指定针对其运行现有已编译代码的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="7b942-133">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="7b942-134">例如，假设你有一个名为 app1.exe 并且针对 .NET Framework 3.5 进行了编译的应用程序，但是希望针对 .NET Framework 4.5 运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b942-134">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="7b942-135">这需要执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7b942-135">This requires the following steps:</span></span>

1. <span data-ttu-id="7b942-136">为主可执行文件创建一个配置文件并将它命名为 *appName*.exe.config，其中 *appName* 是应用程序可执行文件的名称。</span><span class="sxs-lookup"><span data-stu-id="7b942-136">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="7b942-137">对于我们示例中名为 app1.exe 的应用程序，会创建一个名为 app1.exe.config 的配置文件。</span><span class="sxs-lookup"><span data-stu-id="7b942-137">For the application named *app1.exe* in our example, you would create a configuration file named *app1.exe.config*.</span></span>

2. <span data-ttu-id="7b942-138">向该配置文件添加以下内容：</span><span class="sxs-lookup"><span data-stu-id="7b942-138">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="7b942-139">为针对特定版本的 .NET Framework，请将下列其中一个字符串值分配给 `version` 特性：</span><span class="sxs-lookup"><span data-stu-id="7b942-139">To target a specific version of .NET Framework, assign one of the following string values to the `version` attribute:</span></span>

|<span data-ttu-id="7b942-140">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="7b942-140">.NET Framework version</span></span>|<span data-ttu-id="7b942-141">`version` 字符串</span><span class="sxs-lookup"><span data-stu-id="7b942-141">`version` string</span></span>|
|-|-|
|<span data-ttu-id="7b942-142">4.8</span><span class="sxs-lookup"><span data-stu-id="7b942-142">4.8</span></span>|<span data-ttu-id="7b942-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="7b942-143">v4.0</span></span>|
|<span data-ttu-id="7b942-144">4.7（包括 4.7.1 和 4.7.2）</span><span class="sxs-lookup"><span data-stu-id="7b942-144">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="7b942-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="7b942-145">v4.0</span></span>|
|<span data-ttu-id="7b942-146">4.6（包括 4.6.1 和 4.6.2）</span><span class="sxs-lookup"><span data-stu-id="7b942-146">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="7b942-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="7b942-147">v4.0</span></span>|
|<span data-ttu-id="7b942-148">4.5（包括 4.5.1 和 4.5.2）</span><span class="sxs-lookup"><span data-stu-id="7b942-148">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="7b942-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="7b942-149">v4.0</span></span>|
|<span data-ttu-id="7b942-150">4</span><span class="sxs-lookup"><span data-stu-id="7b942-150">4</span></span>|<span data-ttu-id="7b942-151">v4.0</span><span class="sxs-lookup"><span data-stu-id="7b942-151">v4.0</span></span>|
|<span data-ttu-id="7b942-152">3.5</span><span class="sxs-lookup"><span data-stu-id="7b942-152">3.5</span></span>|<span data-ttu-id="7b942-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="7b942-153">v2.0.50727</span></span>|
|<span data-ttu-id="7b942-154">2.0</span><span class="sxs-lookup"><span data-stu-id="7b942-154">2.0</span></span>|<span data-ttu-id="7b942-155">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="7b942-155">v2.0.50727</span></span>|
|<span data-ttu-id="7b942-156">1.1</span><span class="sxs-lookup"><span data-stu-id="7b942-156">1.1</span></span>|<span data-ttu-id="7b942-157">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="7b942-157">v1.1.4322</span></span>|
|<span data-ttu-id="7b942-158">1.0</span><span class="sxs-lookup"><span data-stu-id="7b942-158">1.0</span></span>|<span data-ttu-id="7b942-159">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="7b942-159">v1.0.3705</span></span>|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a><span data-ttu-id="7b942-160">.NET Framework 4.5 及更高版本的过时 API</span><span class="sxs-lookup"><span data-stu-id="7b942-160">Obsolete APIs for .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="7b942-161">过时类型</span><span class="sxs-lookup"><span data-stu-id="7b942-161">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="7b942-162">过时成员</span><span class="sxs-lookup"><span data-stu-id="7b942-162">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a><span data-ttu-id="7b942-163">以前版本的过时 API</span><span class="sxs-lookup"><span data-stu-id="7b942-163">Obsolete APIs for previous versions</span></span>

- <span data-ttu-id="7b942-164">[.NET Framework 4 中的已过时类型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7b942-164">[Obsolete Types in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>
- <span data-ttu-id="7b942-165">[.NET Framework 4 中的已过时成员](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7b942-165">[Obsolete Members in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>
- <span data-ttu-id="7b942-166">[.NET Framework 3.5 过时列表](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7b942-166">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>
- <span data-ttu-id="7b942-167">[.NET Framework 2.0 过时列表](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7b942-167">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="7b942-168">请参阅</span><span class="sxs-lookup"><span data-stu-id="7b942-168">See also</span></span>

- [<span data-ttu-id="7b942-169">\<supportedRuntime> 元素</span><span class="sxs-lookup"><span data-stu-id="7b942-169">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
