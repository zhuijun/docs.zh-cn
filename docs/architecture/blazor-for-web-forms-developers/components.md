---
title: 使用 Blazor 生成可重复使用的 UI 组件
description: 了解如何使用 Blazor 生成可重复使用的 UI 组件，以及如何将其与 ASP.NET Web 窗体控件进行比较。
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: f6528b1e68b49b6ee3949baca166f4806448718b
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051447"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="079f7-103">使用 Blazor 生成可重复使用的 UI 组件</span><span class="sxs-lookup"><span data-stu-id="079f7-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="079f7-104">有关 ASP.NET Web 窗体的一项精彩功能，就是它如何使可重用的用户界面（UI）代码块可用于可重复使用的 UI 控件。</span><span class="sxs-lookup"><span data-stu-id="079f7-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="079f7-105">可以使用 *.ascx*文件在标记中定义自定义用户控件。</span><span class="sxs-lookup"><span data-stu-id="079f7-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="079f7-106">你还可以在代码中生成具有完全设计器支持的精致服务器控件。</span><span class="sxs-lookup"><span data-stu-id="079f7-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="079f7-107">Blazor 还支持通过*组件*进行 UI 封装。</span><span class="sxs-lookup"><span data-stu-id="079f7-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="079f7-108">组件：</span><span class="sxs-lookup"><span data-stu-id="079f7-108">A component:</span></span>

- <span data-ttu-id="079f7-109">是一个独立的 UI 块区。</span><span class="sxs-lookup"><span data-stu-id="079f7-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="079f7-110">维护其自己的状态和呈现逻辑。</span><span class="sxs-lookup"><span data-stu-id="079f7-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="079f7-111">可以定义 UI 事件处理程序、绑定到输入数据，并管理其自己的生命周期。</span><span class="sxs-lookup"><span data-stu-id="079f7-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="079f7-112">通常使用 Razor 语法在*razor*文件中定义。</span><span class="sxs-lookup"><span data-stu-id="079f7-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="079f7-113">Razor 简介</span><span class="sxs-lookup"><span data-stu-id="079f7-113">An introduction to Razor</span></span>

<span data-ttu-id="079f7-114">Razor 是基于 HTML 和 c # 的轻型标记模板化语言。</span><span class="sxs-lookup"><span data-stu-id="079f7-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="079f7-115">借助 Razor，你可以在标记与 c # 代码之间无缝转换，以定义你的组件呈现逻辑。</span><span class="sxs-lookup"><span data-stu-id="079f7-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="079f7-116">在编译*razor*文件时，呈现逻辑在 .net 类中以结构化的方式捕获。</span><span class="sxs-lookup"><span data-stu-id="079f7-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="079f7-117">已编译类的名称是从*razor*文件名获取的。</span><span class="sxs-lookup"><span data-stu-id="079f7-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="079f7-118">命名空间是从项目的默认命名空间和文件夹路径获取的，或者可以使用指令显式指定命名空间 `@namespace` （下面的 Razor 指令更详细）。</span><span class="sxs-lookup"><span data-stu-id="079f7-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="079f7-119">通过使用 c # 添加的动态逻辑，使用常规 HTML 标记编写组件的呈现逻辑。</span><span class="sxs-lookup"><span data-stu-id="079f7-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="079f7-120">`@`字符用于转换为 c #。</span><span class="sxs-lookup"><span data-stu-id="079f7-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="079f7-121">Razor 通常会巧妙地了解何时切换回 HTML。</span><span class="sxs-lookup"><span data-stu-id="079f7-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="079f7-122">例如，以下组件 `<p>` 使用当前时间呈现标记：</span><span class="sxs-lookup"><span data-stu-id="079f7-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="079f7-123">若要显式指定 c # 表达式的开头和结尾，请使用括号：</span><span class="sxs-lookup"><span data-stu-id="079f7-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="079f7-124">使用 Razor 还可以轻松地在呈现逻辑中使用 c # 控件流。</span><span class="sxs-lookup"><span data-stu-id="079f7-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="079f7-125">例如，你可以有条件地呈现一些 HTML，如下所示：</span><span class="sxs-lookup"><span data-stu-id="079f7-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="079f7-126">或者，可以使用如下所示的普通 c # 循环生成项列表 `foreach` ：</span><span class="sxs-lookup"><span data-stu-id="079f7-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="079f7-127">Razor 指令（如 ASP.NET Web 窗体中的指令）控制如何编译 Razor 组件的许多方面。</span><span class="sxs-lookup"><span data-stu-id="079f7-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="079f7-128">示例包括组件的：</span><span class="sxs-lookup"><span data-stu-id="079f7-128">Examples include the component's:</span></span>

- <span data-ttu-id="079f7-129">命名空间</span><span class="sxs-lookup"><span data-stu-id="079f7-129">Namespace</span></span>
- <span data-ttu-id="079f7-130">基类</span><span class="sxs-lookup"><span data-stu-id="079f7-130">Base class</span></span>
- <span data-ttu-id="079f7-131">实现的接口</span><span class="sxs-lookup"><span data-stu-id="079f7-131">Implemented interfaces</span></span>
- <span data-ttu-id="079f7-132">泛型参数</span><span class="sxs-lookup"><span data-stu-id="079f7-132">Generic parameters</span></span>
- <span data-ttu-id="079f7-133">导入的命名空间</span><span class="sxs-lookup"><span data-stu-id="079f7-133">Imported namespaces</span></span>
- <span data-ttu-id="079f7-134">路由</span><span class="sxs-lookup"><span data-stu-id="079f7-134">Routes</span></span>

<span data-ttu-id="079f7-135">Razor 指令以字符开头 `@` ，通常在文件开头的新行的开头使用。</span><span class="sxs-lookup"><span data-stu-id="079f7-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="079f7-136">例如， `@namespace` 指令定义组件的命名空间：</span><span class="sxs-lookup"><span data-stu-id="079f7-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="079f7-137">下表汇总了 Blazor 中使用的各种 Razor 指令及其等效的 ASP.NET Web 窗体（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="079f7-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="079f7-138">指令</span><span class="sxs-lookup"><span data-stu-id="079f7-138">Directive</span></span>    |<span data-ttu-id="079f7-139">描述</span><span class="sxs-lookup"><span data-stu-id="079f7-139">Description</span></span>|<span data-ttu-id="079f7-140">示例</span><span class="sxs-lookup"><span data-stu-id="079f7-140">Example</span></span>|<span data-ttu-id="079f7-141">Web 窗体等效项</span><span class="sxs-lookup"><span data-stu-id="079f7-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="079f7-142">向组件添加类级别属性</span><span class="sxs-lookup"><span data-stu-id="079f7-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="079f7-143">None</span><span class="sxs-lookup"><span data-stu-id="079f7-143">None</span></span>|
|`@code`      |<span data-ttu-id="079f7-144">将类成员添加到组件</span><span class="sxs-lookup"><span data-stu-id="079f7-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="079f7-145">实现指定接口</span><span class="sxs-lookup"><span data-stu-id="079f7-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="079f7-146">使用代码隐藏</span><span class="sxs-lookup"><span data-stu-id="079f7-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="079f7-147">继承自指定的基类</span><span class="sxs-lookup"><span data-stu-id="079f7-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="079f7-148">将服务注入组件</span><span class="sxs-lookup"><span data-stu-id="079f7-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="079f7-149">None</span><span class="sxs-lookup"><span data-stu-id="079f7-149">None</span></span>|
|`@layout`    |<span data-ttu-id="079f7-150">指定组件的布局组件</span><span class="sxs-lookup"><span data-stu-id="079f7-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="079f7-151">设置组件的命名空间</span><span class="sxs-lookup"><span data-stu-id="079f7-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="079f7-152">None</span><span class="sxs-lookup"><span data-stu-id="079f7-152">None</span></span>|
|`@page`      |<span data-ttu-id="079f7-153">指定组件的路由</span><span class="sxs-lookup"><span data-stu-id="079f7-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="079f7-154">指定组件的泛型类型参数</span><span class="sxs-lookup"><span data-stu-id="079f7-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="079f7-155">使用代码隐藏</span><span class="sxs-lookup"><span data-stu-id="079f7-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="079f7-156">指定要引入作用域的命名空间</span><span class="sxs-lookup"><span data-stu-id="079f7-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="079f7-157">在*web.config*中添加命名空间</span><span class="sxs-lookup"><span data-stu-id="079f7-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="079f7-158">Razor 组件还广泛使用元素上的*指令属性*，以控制如何编译组件（事件处理、数据绑定、组件 & 元素引用等）的各个方面。</span><span class="sxs-lookup"><span data-stu-id="079f7-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="079f7-159">指令特性都遵循通用通用语法，其中括号中的值是可选的：</span><span class="sxs-lookup"><span data-stu-id="079f7-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="079f7-160">下表总结了 Blazor 中使用的 Razor 指令的各种属性。</span><span class="sxs-lookup"><span data-stu-id="079f7-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="079f7-161">特性</span><span class="sxs-lookup"><span data-stu-id="079f7-161">Attribute</span></span>    |<span data-ttu-id="079f7-162">说明</span><span class="sxs-lookup"><span data-stu-id="079f7-162">Description</span></span>|<span data-ttu-id="079f7-163">示例</span><span class="sxs-lookup"><span data-stu-id="079f7-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="079f7-164">呈现特性字典</span><span class="sxs-lookup"><span data-stu-id="079f7-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="079f7-165">创建双向数据绑定</span><span class="sxs-lookup"><span data-stu-id="079f7-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="079f7-166">为指定的事件添加事件处理程序</span><span class="sxs-lookup"><span data-stu-id="079f7-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="079f7-167">指定由比较算法用来保留集合中元素的键</span><span class="sxs-lookup"><span data-stu-id="079f7-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="079f7-168">捕获对组件或 HTML 元素的引用</span><span class="sxs-lookup"><span data-stu-id="079f7-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="079f7-169">Blazor （、、等）使用的各种指令特性 `@onclick` `@bind` `@ref` 都将在以下章节和更高章节中介绍。</span><span class="sxs-lookup"><span data-stu-id="079f7-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="079f7-170">*.Aspx*和 *.ascx*文件中使用的很多语法在 Razor 中具有并行语法。</span><span class="sxs-lookup"><span data-stu-id="079f7-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="079f7-171">下面是 ASP.NET Web 窗体和 Razor 语法的简单比较。</span><span class="sxs-lookup"><span data-stu-id="079f7-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="079f7-172">功能</span><span class="sxs-lookup"><span data-stu-id="079f7-172">Feature</span></span>                      |<span data-ttu-id="079f7-173">Web Forms — Web 窗体</span><span class="sxs-lookup"><span data-stu-id="079f7-173">Web Forms</span></span>           |<span data-ttu-id="079f7-174">语法</span><span class="sxs-lookup"><span data-stu-id="079f7-174">Syntax</span></span>               |<span data-ttu-id="079f7-175">Razor</span><span class="sxs-lookup"><span data-stu-id="079f7-175">Razor</span></span>         |<span data-ttu-id="079f7-176">语法</span><span class="sxs-lookup"><span data-stu-id="079f7-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="079f7-177">指令</span><span class="sxs-lookup"><span data-stu-id="079f7-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="079f7-178">代码块</span><span class="sxs-lookup"><span data-stu-id="079f7-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="079f7-179">表达式</span><span class="sxs-lookup"><span data-stu-id="079f7-179">Expressions</span></span><br><span data-ttu-id="079f7-180">（HTML 编码）</span><span class="sxs-lookup"><span data-stu-id="079f7-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="079f7-181">式`@`</span><span class="sxs-lookup"><span data-stu-id="079f7-181">Implicit: `@`</span></span><br><span data-ttu-id="079f7-182">Jre`@()`</span><span class="sxs-lookup"><span data-stu-id="079f7-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="079f7-183">注释</span><span class="sxs-lookup"><span data-stu-id="079f7-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="079f7-184">数据绑定</span><span class="sxs-lookup"><span data-stu-id="079f7-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="079f7-185">若要将成员添加到 Razor 组件类，请使用 `@code` 指令。</span><span class="sxs-lookup"><span data-stu-id="079f7-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="079f7-186">此方法类似于 `<script runat="server">...</script>` 在 ASP.NET Web 窗体用户控件或页面中使用块。</span><span class="sxs-lookup"><span data-stu-id="079f7-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="079f7-187">由于 Razor 基于 c #，因此它必须从 c # 项目（*.csproj*）中进行编译。</span><span class="sxs-lookup"><span data-stu-id="079f7-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="079f7-188">不能从 Visual Basic 项目（*. .vbproj*）编译*razor*文件。</span><span class="sxs-lookup"><span data-stu-id="079f7-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="079f7-189">你仍可以从 Blazor 项目引用 Visual Basic 项目。</span><span class="sxs-lookup"><span data-stu-id="079f7-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="079f7-190">相反的情况也是如此。</span><span class="sxs-lookup"><span data-stu-id="079f7-190">The opposite is true too.</span></span>

<span data-ttu-id="079f7-191">有关完整 Razor 语法引用，请参阅[ASP.NET Core 的 Razor 语法参考](/aspnet/core/mvc/views/razor)。</span><span class="sxs-lookup"><span data-stu-id="079f7-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="079f7-192">使用组件</span><span class="sxs-lookup"><span data-stu-id="079f7-192">Use components</span></span>

<span data-ttu-id="079f7-193">除了正常 HTML，组件还可以使用其他组件作为其呈现逻辑的一部分。</span><span class="sxs-lookup"><span data-stu-id="079f7-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="079f7-194">在 Razor 中使用组件的语法类似于在 ASP.NET Web 窗体应用程序中使用用户控件。</span><span class="sxs-lookup"><span data-stu-id="079f7-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="079f7-195">使用与组件的类型名称匹配的元素标记指定组件。</span><span class="sxs-lookup"><span data-stu-id="079f7-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="079f7-196">例如，可以添加 `Counter` 如下所示的组件：</span><span class="sxs-lookup"><span data-stu-id="079f7-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="079f7-197">与 ASP.NET Web 窗体不同，Blazor 中的组件：</span><span class="sxs-lookup"><span data-stu-id="079f7-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="079f7-198">不要使用元素前缀（例如 `asp:` ）。</span><span class="sxs-lookup"><span data-stu-id="079f7-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="079f7-199">不需要在页面或*web.config*中注册。</span><span class="sxs-lookup"><span data-stu-id="079f7-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="079f7-200">像您的 .NET 类型一样，可以像您这样做，因为这正是它们的作用。</span><span class="sxs-lookup"><span data-stu-id="079f7-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="079f7-201">如果引用包含组件的程序集，则可以使用该组件。</span><span class="sxs-lookup"><span data-stu-id="079f7-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="079f7-202">若要将组件的命名空间置于范围中，请应用 `@using` 指令：</span><span class="sxs-lookup"><span data-stu-id="079f7-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="079f7-203">如默认 Blazor 项目中所示，通常将 `@using` 指令放入 *_Imports*文件中，以便将其导入到同一目录和子目录中的所有*razor*文件中。</span><span class="sxs-lookup"><span data-stu-id="079f7-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="079f7-204">如果某个组件的命名空间不在范围内，则可以使用它的完整类型名称指定一个组件，如 c # 中所示：</span><span class="sxs-lookup"><span data-stu-id="079f7-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="079f7-205">组件参数</span><span class="sxs-lookup"><span data-stu-id="079f7-205">Component parameters</span></span>

<span data-ttu-id="079f7-206">在 ASP.NET Web 窗体中，你可以使用公共属性将参数和数据流式传输到控件。</span><span class="sxs-lookup"><span data-stu-id="079f7-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="079f7-207">可以使用特性在标记中设置这些属性，也可以在代码中直接设置这些属性。</span><span class="sxs-lookup"><span data-stu-id="079f7-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="079f7-208">Blazor 组件的工作方式与此类似，不过，组件属性还必须标记 `[Parameter]` 为要被视为组件参数的属性。</span><span class="sxs-lookup"><span data-stu-id="079f7-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="079f7-209">以下 `Counter` 组件定义了一个名为的组件参数 `IncrementAmount` ，该参数可用于指定 `Counter` 每次单击按钮时应增加的量。</span><span class="sxs-lookup"><span data-stu-id="079f7-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="079f7-210">若要在 Blazor 中指定组件参数，请使用 ASP.NET Web 窗体中的属性：</span><span class="sxs-lookup"><span data-stu-id="079f7-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="079f7-211">事件处理程序</span><span class="sxs-lookup"><span data-stu-id="079f7-211">Event handlers</span></span>

<span data-ttu-id="079f7-212">ASP.NET Web 窗体和 Blazor 都提供用于处理 UI 事件的基于事件的编程模型。</span><span class="sxs-lookup"><span data-stu-id="079f7-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="079f7-213">此类事件的示例包括按钮单击和文本输入。</span><span class="sxs-lookup"><span data-stu-id="079f7-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="079f7-214">在 ASP.NET Web 窗体中，您可以使用 HTML 服务器控件处理 DOM 公开的 UI 事件，也可以处理 Web 服务器控件公开的事件。</span><span class="sxs-lookup"><span data-stu-id="079f7-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="079f7-215">这些事件通过窗体回发请求出现在服务器上。</span><span class="sxs-lookup"><span data-stu-id="079f7-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="079f7-216">请考虑以下 Web 窗体按钮单击示例：</span><span class="sxs-lookup"><span data-stu-id="079f7-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="079f7-217">*Counter*</span><span class="sxs-lookup"><span data-stu-id="079f7-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="079f7-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="079f7-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="079f7-219">在 Blazor 中，可以使用窗体的指令特性直接注册 DOM UI 事件的处理程序 `@on{event}` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="079f7-220">`{event}`占位符表示事件的名称。</span><span class="sxs-lookup"><span data-stu-id="079f7-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="079f7-221">例如，您可以按如下所示侦听按钮单击操作：</span><span class="sxs-lookup"><span data-stu-id="079f7-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="079f7-222">事件处理程序可接受可选的特定于事件的自变量来提供有关事件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="079f7-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="079f7-223">例如，鼠标事件可以接受 `MouseEventArgs` 参数，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="079f7-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="079f7-224">您可以使用 lambda 表达式，而不是引用事件处理程序的方法组。</span><span class="sxs-lookup"><span data-stu-id="079f7-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="079f7-225">Lambda 表达式允许您关闭其他范围内的值。</span><span class="sxs-lookup"><span data-stu-id="079f7-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="079f7-226">事件处理程序可以同步执行，也可以异步执行。</span><span class="sxs-lookup"><span data-stu-id="079f7-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="079f7-227">例如，下面的 `OnClick` 事件处理程序以异步方式执行：</span><span class="sxs-lookup"><span data-stu-id="079f7-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="079f7-228">处理事件后，将呈现组件以考虑任何组件状态更改。</span><span class="sxs-lookup"><span data-stu-id="079f7-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="079f7-229">对于异步事件处理程序，该组件将在处理程序执行完成后立即呈现。</span><span class="sxs-lookup"><span data-stu-id="079f7-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="079f7-230">异步完成后，将*再次*呈现该组件 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="079f7-231">此异步执行模式提供了在异步仍在进行时呈现一些适当 UI 的机会 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="079f7-232">组件还可以通过定义类型的组件参数来定义自己的事件 `EventCallback<TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="079f7-233">事件回调支持 DOM UI 事件处理程序的所有变体：可选参数、同步或异步、方法组或 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="079f7-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="079f7-234">数据绑定</span><span class="sxs-lookup"><span data-stu-id="079f7-234">Data binding</span></span>

<span data-ttu-id="079f7-235">Blazor 提供了一种简单的机制，用于将数据从 UI 组件绑定到组件的状态。</span><span class="sxs-lookup"><span data-stu-id="079f7-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="079f7-236">此方法不同于 ASP.NET Web 窗体中的功能，可用于将数据从数据源绑定到 UI 控件。</span><span class="sxs-lookup"><span data-stu-id="079f7-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="079f7-237">在处理[数据](data.md)部分，我们将介绍如何处理来自不同数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="079f7-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="079f7-238">若要创建从 UI 组件到组件状态的双向数据绑定，请使用 `@bind` 指令特性。</span><span class="sxs-lookup"><span data-stu-id="079f7-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="079f7-239">在下面的示例中，复选框的值绑定到了 `isChecked` 字段。</span><span class="sxs-lookup"><span data-stu-id="079f7-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="079f7-240">呈现组件时，复选框的值将设置为字段的值 `isChecked` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="079f7-241">当用户切换复选框时，将 `onchange` 激发事件并将 `isChecked` 字段设置为新值。</span><span class="sxs-lookup"><span data-stu-id="079f7-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="079f7-242">`@bind`这种情况下的语法等效于以下标记：</span><span class="sxs-lookup"><span data-stu-id="079f7-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="079f7-243">若要更改用于绑定的事件，请使用 `@bind:event` 特性。</span><span class="sxs-lookup"><span data-stu-id="079f7-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="079f7-244">组件还可以支持数据绑定到其参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="079f7-245">若要进行数据绑定，请使用与可绑定参数相同的名称定义事件回调参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="079f7-246">"更改的" 后缀将添加到名称中。</span><span class="sxs-lookup"><span data-stu-id="079f7-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="079f7-247">*PasswordBox*</span><span class="sxs-lookup"><span data-stu-id="079f7-247">*PasswordBox.razor*</span></span>

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="079f7-248">若要将数据绑定链接到基础 UI 元素，请设置值并直接在 UI 元素上处理事件，而不是使用 `@bind` 属性。</span><span class="sxs-lookup"><span data-stu-id="079f7-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="079f7-249">若要绑定到组件参数，请使用 `@bind-{Parameter}` 特性来指定要绑定到的参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="079f7-250">状态更改</span><span class="sxs-lookup"><span data-stu-id="079f7-250">State changes</span></span>

<span data-ttu-id="079f7-251">如果组件的状态在正常的 UI 事件或事件回调之外发生了更改，则组件必须手动通知其需要再次呈现。</span><span class="sxs-lookup"><span data-stu-id="079f7-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="079f7-252">若要指示组件状态已更改，请对组件调用 `StateHasChanged` 方法。</span><span class="sxs-lookup"><span data-stu-id="079f7-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="079f7-253">在下面的示例中，组件显示来自服务的一条消息，该消息 `AppState` 可以由应用程序的其他部分更新。</span><span class="sxs-lookup"><span data-stu-id="079f7-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="079f7-254">组件 `StateHasChanged` 向事件注册其方法， `AppState.OnChange` 以便每当消息被更新时呈现该组件。</span><span class="sxs-lookup"><span data-stu-id="079f7-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="079f7-255">组件生命周期</span><span class="sxs-lookup"><span data-stu-id="079f7-255">Component lifecycle</span></span>

<span data-ttu-id="079f7-256">ASP.NET Web 窗体框架为模块、页和控件提供了定义完善的生命周期方法。</span><span class="sxs-lookup"><span data-stu-id="079f7-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="079f7-257">例如，下面的控件为 `Init` 、 `Load` 和 `UnLoad` 生命周期事件实现事件处理程序：</span><span class="sxs-lookup"><span data-stu-id="079f7-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="079f7-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="079f7-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="079f7-259">Blazor 组件还具有定义完善的生命周期。</span><span class="sxs-lookup"><span data-stu-id="079f7-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="079f7-260">组件的生命周期可用于初始化组件状态和实现高级组件行为。</span><span class="sxs-lookup"><span data-stu-id="079f7-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="079f7-261">所有 Blazor 的组件生命周期方法都有同步和异步版本。</span><span class="sxs-lookup"><span data-stu-id="079f7-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="079f7-262">组件呈现是同步的。</span><span class="sxs-lookup"><span data-stu-id="079f7-262">Component rendering is synchronous.</span></span> <span data-ttu-id="079f7-263">无法在呈现组件的过程中运行异步逻辑。</span><span class="sxs-lookup"><span data-stu-id="079f7-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="079f7-264">所有异步逻辑都必须作为 `async` 生命周期方法的一部分执行。</span><span class="sxs-lookup"><span data-stu-id="079f7-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="079f7-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="079f7-265">OnInitialized</span></span>

<span data-ttu-id="079f7-266">`OnInitialized`和 `OnInitializedAsync` 方法用于初始化组件。</span><span class="sxs-lookup"><span data-stu-id="079f7-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="079f7-267">通常在第一次呈现组件后对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="079f7-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="079f7-268">组件初始化后，它可能会在最终被释放之前呈现多次。</span><span class="sxs-lookup"><span data-stu-id="079f7-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="079f7-269">此 `OnInitialized` 方法类似于 `Page_Load` ASP.NET Web 窗体页和控件中的事件。</span><span class="sxs-lookup"><span data-stu-id="079f7-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="079f7-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="079f7-270">OnParametersSet</span></span>

<span data-ttu-id="079f7-271">`OnParametersSet` `OnParametersSetAsync` 当组件已从其父级接收参数并且将值分配给属性时，将调用和方法。</span><span class="sxs-lookup"><span data-stu-id="079f7-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="079f7-272">这些方法在组件初始化之后以及*每次呈现组件*时执行。</span><span class="sxs-lookup"><span data-stu-id="079f7-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="079f7-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="079f7-273">OnAfterRender</span></span>

<span data-ttu-id="079f7-274">在 `OnAfterRender` `OnAfterRenderAsync` 组件完成呈现后，调用和方法。</span><span class="sxs-lookup"><span data-stu-id="079f7-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="079f7-275">此时将填充元素和组件引用（有关这些概念的详细信息，请参阅下文）。</span><span class="sxs-lookup"><span data-stu-id="079f7-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="079f7-276">此时启用了与浏览器的交互。</span><span class="sxs-lookup"><span data-stu-id="079f7-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="079f7-277">可以安全地进行与 DOM 和 JavaScript 执行的交互。</span><span class="sxs-lookup"><span data-stu-id="079f7-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="079f7-278">`OnAfterRender`在 `OnAfterRenderAsync` *服务器上预呈现时不调用*和。</span><span class="sxs-lookup"><span data-stu-id="079f7-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="079f7-279">`firstRender`参数是 `true` 第一次呈现组件时; 否则，其值为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="079f7-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="079f7-280">IDisposable</span></span>

<span data-ttu-id="079f7-281">`IDisposable`从 UI 中删除组件时，Blazor 组件可以实现以释放资源。</span><span class="sxs-lookup"><span data-stu-id="079f7-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="079f7-282">Razor 组件可 `IDispose` 通过使用 `@implements` 指令实现：</span><span class="sxs-lookup"><span data-stu-id="079f7-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="079f7-283">捕获组件引用</span><span class="sxs-lookup"><span data-stu-id="079f7-283">Capture component references</span></span>

<span data-ttu-id="079f7-284">在 ASP.NET Web 窗体中，通常通过引用控件的 ID 来直接在代码中处理控件实例。</span><span class="sxs-lookup"><span data-stu-id="079f7-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="079f7-285">在 Blazor 中，还可以捕获和操作对组件的引用，尽管它不太常见。</span><span class="sxs-lookup"><span data-stu-id="079f7-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="079f7-286">若要在 Blazor 中捕获组件引用，请使用 `@ref` 指令特性。</span><span class="sxs-lookup"><span data-stu-id="079f7-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="079f7-287">属性的值应与所引用组件的类型相同的可设置字段的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="079f7-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="079f7-288">呈现父组件时，将用子组件实例填充字段。</span><span class="sxs-lookup"><span data-stu-id="079f7-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="079f7-289">然后，你可以对组件实例调用方法或其他操作。</span><span class="sxs-lookup"><span data-stu-id="079f7-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="079f7-290">不建议直接使用组件引用操控组件状态。</span><span class="sxs-lookup"><span data-stu-id="079f7-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="079f7-291">这样做可以防止在正确的时间自动呈现组件。</span><span class="sxs-lookup"><span data-stu-id="079f7-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="079f7-292">捕获元素引用</span><span class="sxs-lookup"><span data-stu-id="079f7-292">Capture element references</span></span>

<span data-ttu-id="079f7-293">Blazor 组件可以捕获对元素的引用。</span><span class="sxs-lookup"><span data-stu-id="079f7-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="079f7-294">与 ASP.NET Web 窗体中的 HTML 服务器控件不同，您不能直接使用 Blazor 中的元素引用来操作 DOM。</span><span class="sxs-lookup"><span data-stu-id="079f7-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="079f7-295">Blazor 使用其 DOM 比较算法处理大多数 DOM 交互。</span><span class="sxs-lookup"><span data-stu-id="079f7-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="079f7-296">Blazor 中捕获的元素引用不透明。</span><span class="sxs-lookup"><span data-stu-id="079f7-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="079f7-297">但是，它们用于在 JavaScript 互操作调用中传递特定的元素引用。</span><span class="sxs-lookup"><span data-stu-id="079f7-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="079f7-298">有关 JavaScript 互操作的详细信息，请参阅[ASP.NET Core Blazor JavaScript 互操作](/aspnet/core/blazor/javascript-interop)。</span><span class="sxs-lookup"><span data-stu-id="079f7-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="079f7-299">模板化组件</span><span class="sxs-lookup"><span data-stu-id="079f7-299">Templated components</span></span>

<span data-ttu-id="079f7-300">在 ASP.NET Web 窗体中，您可以创建*模板化控件*。</span><span class="sxs-lookup"><span data-stu-id="079f7-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="079f7-301">模板化控件使开发人员可以指定用于呈现容器控件的 HTML 部分。</span><span class="sxs-lookup"><span data-stu-id="079f7-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="079f7-302">构建模板化服务器控件的机制非常复杂，但它们可让用户以用户可自定义的方式呈现数据。</span><span class="sxs-lookup"><span data-stu-id="079f7-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="079f7-303">模板化控件的示例包括 `Repeater` 和 `DataList` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="079f7-304">还可以通过定义类型为或的组件参数，模板化 Blazor 组件 `RenderFragment` `RenderFragment<T>` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="079f7-305">`RenderFragment`表示 Razor 标记的块区，该标记随后可由组件呈现。</span><span class="sxs-lookup"><span data-stu-id="079f7-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="079f7-306">`RenderFragment<T>`是 Razor 标记的块区，它采用可在呈现呈现片段时指定的参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="079f7-307">子内容</span><span class="sxs-lookup"><span data-stu-id="079f7-307">Child content</span></span>

<span data-ttu-id="079f7-308">Blazor 组件可以将其子内容捕获为 `RenderFragment` ，并在呈现组件时呈现该内容。</span><span class="sxs-lookup"><span data-stu-id="079f7-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="079f7-309">若要捕获子内容，请定义类型为的组件参数， `RenderFragment` 并将其命名为 `ChildContent` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="079f7-310">*ChildContentComponent*</span><span class="sxs-lookup"><span data-stu-id="079f7-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="079f7-311">然后，父组件可以使用普通 Razor 语法提供子内容。</span><span class="sxs-lookup"><span data-stu-id="079f7-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="079f7-312">模板参数</span><span class="sxs-lookup"><span data-stu-id="079f7-312">Template parameters</span></span>

<span data-ttu-id="079f7-313">模板化 Blazor 组件还可以定义或类型的多个组件参数 `RenderFragment` `RenderFragment<T>` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="079f7-314">在 `RenderFragment<T>` 调用时，可以指定的参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="079f7-315">若要为组件指定泛型类型参数，请使用 `@typeparam` Razor 指令。</span><span class="sxs-lookup"><span data-stu-id="079f7-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="079f7-316">*SimpleListView*</span><span class="sxs-lookup"><span data-stu-id="079f7-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="079f7-317">使用模板化组件时，可以使用与参数名称匹配的子元素指定模板参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="079f7-318">作为元素传递的类型的组件参数 `RenderFragment<T>` 具有一个名为的隐式参数 `context` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="079f7-319">您可以使用子元素上的特性更改此实现参数的名称 `Context` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="079f7-320">可以使用与类型参数的名称匹配的特性指定任何泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="079f7-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="079f7-321">如果可能，将推断类型参数：</span><span class="sxs-lookup"><span data-stu-id="079f7-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="079f7-322">此组件的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="079f7-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="079f7-323">代码隐藏</span><span class="sxs-lookup"><span data-stu-id="079f7-323">Code-behind</span></span>

<span data-ttu-id="079f7-324">Blazor 组件通常是在单个*razor*文件中创作的。</span><span class="sxs-lookup"><span data-stu-id="079f7-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="079f7-325">不过，也可以使用代码隐藏文件来分隔代码和标记。</span><span class="sxs-lookup"><span data-stu-id="079f7-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="079f7-326">若要使用组件文件，请添加一个与组件文件的文件名相匹配的 c # 文件，但添加了 *.cs*扩展名（*Counter.razor.cs*）。</span><span class="sxs-lookup"><span data-stu-id="079f7-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="079f7-327">使用 c # 文件定义组件的基类。</span><span class="sxs-lookup"><span data-stu-id="079f7-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="079f7-328">您可以将基类命名为任何所需的名称，但通常会将类命名为与 component 类相同的名称，但会 `Base` 添加扩展（ `CounterBase` ）。</span><span class="sxs-lookup"><span data-stu-id="079f7-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="079f7-329">基于组件的类还必须派生自 `ComponentBase` 。</span><span class="sxs-lookup"><span data-stu-id="079f7-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="079f7-330">然后，在 Razor 组件文件中添加 `@inherits` 指令以指定组件的基类（ `@inherits CounterBase` ）。</span><span class="sxs-lookup"><span data-stu-id="079f7-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="079f7-331">*Counter*</span><span class="sxs-lookup"><span data-stu-id="079f7-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="079f7-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="079f7-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="079f7-333">基本类中组件成员的可见性必须为 `protected` 或 `public` 对组件类可见。</span><span class="sxs-lookup"><span data-stu-id="079f7-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="079f7-334">其他资源</span><span class="sxs-lookup"><span data-stu-id="079f7-334">Additional resources</span></span>

<span data-ttu-id="079f7-335">前面不是 Blazor 组件的所有方面的全面处理。</span><span class="sxs-lookup"><span data-stu-id="079f7-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="079f7-336">有关如何[创建和使用 ASP.NET Core Razor 组件](/aspnet/core/blazor/components)的详细信息，请参阅 Blazor 文档。</span><span class="sxs-lookup"><span data-stu-id="079f7-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="079f7-337">[上一页](app-startup.md)
>[下一页](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="079f7-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
