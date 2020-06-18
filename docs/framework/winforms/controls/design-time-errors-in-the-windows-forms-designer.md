---
title: Windows 窗体设计器中的设计时错误
titleSuffix: ''
description: 了解 Windows 窗体设计器因代码、第三方组件或其他位置中的错误而无法加载时所发生的错误。
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9c3993dfce9312c3271c499b6c0cd0c11253ca8
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904385"
---
# <a name="windows-forms-designer-error-page"></a><span data-ttu-id="b5731-103">Windows 窗体设计器错误页</span><span class="sxs-lookup"><span data-stu-id="b5731-103">Windows Forms Designer error page</span></span>

<span data-ttu-id="b5731-104">如果 Windows 窗体设计器由于代码中的错误、第三方组件或其他位置无法加载，则会看到错误页，而不是设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-104">If the Windows Forms Designer fails to load due to an error in your code, in a third-party component, or elsewhere, you'll see an error page instead of the designer.</span></span> <span data-ttu-id="b5731-105">此错误页不一定表示设计器中的 bug。</span><span class="sxs-lookup"><span data-stu-id="b5731-105">This error page does not necessarily signify a bug in the designer.</span></span> <span data-ttu-id="b5731-106">Bug 可能位于名为的代码隐藏页中的某个位置 \<your-form-name> 。Designer.cs。</span><span class="sxs-lookup"><span data-stu-id="b5731-106">The bug may be somewhere in the code-behind page that's named \<your-form-name>.Designer.cs.</span></span> <span data-ttu-id="b5731-107">错误显示在可折叠的黄色栏中，其中包含一个链接，可跳转到代码页上错误的位置。</span><span class="sxs-lookup"><span data-stu-id="b5731-107">Errors appear in collapsible, yellow bars with a link to jump to the location of the error on the code page.</span></span>

![Windows 窗体设计器错误页](media/windows-forms-designer-error-page-collapsed.png)

<span data-ttu-id="b5731-109">您可以选择忽略错误，然后通过单击 "**忽略并继续**" 继续加载设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-109">You can choose to ignore the errors and continue loading the designer by clicking **Ignore and Continue**.</span></span> <span data-ttu-id="b5731-110">此操作可能会导致意外的行为，例如，控件可能不会显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="b5731-110">This action may result in unexpected behavior, for example, controls may not appear on the design surface.</span></span>

## <a name="instances-of-this-error"></a><span data-ttu-id="b5731-111">此错误的实例</span><span class="sxs-lookup"><span data-stu-id="b5731-111">Instances of this error</span></span>

<span data-ttu-id="b5731-112">展开黄色误差线时，将列出该错误的每个实例。</span><span class="sxs-lookup"><span data-stu-id="b5731-112">When the yellow error bar is expanded, each instance of the error is listed.</span></span> <span data-ttu-id="b5731-113">许多错误类型都包含采用以下格式的准确位置： *[项目名称]* *[窗体名称]* 行：*[行号]* 列：*[列号]*。</span><span class="sxs-lookup"><span data-stu-id="b5731-113">Many error types include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="b5731-114">如果调用堆栈与错误相关联，则可以单击 "**显示调用堆栈**" 链接以查看该错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-114">If a call stack is associated with the error, you can click the **Show Call Stack** link to see it.</span></span> <span data-ttu-id="b5731-115">检查调用堆栈可能会进一步帮助您解决此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-115">Examining the call stack may further help you resolve the error.</span></span>

![Windows 窗体设计器扩展错误](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - <span data-ttu-id="b5731-117">对于 Visual Basic 应用，设计时错误页不会显示多个错误，但它可能会显示同一错误的多个实例。</span><span class="sxs-lookup"><span data-stu-id="b5731-117">For Visual Basic apps, the design-time error page does not display more than one error, but it may display multiple instances of the same error.</span></span>
> - <span data-ttu-id="b5731-118">对于 c + + 应用程序，错误没有代码位置链接。</span><span class="sxs-lookup"><span data-stu-id="b5731-118">For C++ apps, errors don't have code location links.</span></span>

## <a name="help-with-this-error"></a><span data-ttu-id="b5731-119">有关此错误的帮助</span><span class="sxs-lookup"><span data-stu-id="b5731-119">Help with this error</span></span>

<span data-ttu-id="b5731-120">如果有针对错误的帮助主题，请单击**MSDN 帮助**链接，直接转到 docs.microsoft.com 上的帮助页面。</span><span class="sxs-lookup"><span data-stu-id="b5731-120">If a help topic for the error is available, click the **MSDN Help** link to navigate directly to the help page on docs.microsoft.com.</span></span>

## <a name="forum-posts-about-this-error"></a><span data-ttu-id="b5731-121">有关此错误的论坛帖子</span><span class="sxs-lookup"><span data-stu-id="b5731-121">Forum posts about this error</span></span>

<span data-ttu-id="b5731-122">单击 "在**MSDN 论坛中搜索与此错误相关的帖子**" 链接以导航到 Microsoft 开发人员网络论坛。</span><span class="sxs-lookup"><span data-stu-id="b5731-122">Click the **Search the MSDN Forums for posts related to this error** link to navigate to the Microsoft Developer Network forums.</span></span> <span data-ttu-id="b5731-123">你可能想要专门搜索[Windows 窗体设计器](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)或[Windows 窗体](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)论坛。</span><span class="sxs-lookup"><span data-stu-id="b5731-123">You may want to specifically search the [Windows Forms Designer](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) or [Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) forums.</span></span>

## <a name="design-time-errors"></a><span data-ttu-id="b5731-124">设计时错误</span><span class="sxs-lookup"><span data-stu-id="b5731-124">Design-time errors</span></span>

<span data-ttu-id="b5731-125">本部分列出了可能会遇到的一些错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-125">This section lists some of the errors you may encounter.</span></span>

### <a name="identifier-name-is-not-a-valid-identifier"></a><span data-ttu-id="b5731-126">" \<identifier name> " 不是有效的标识符</span><span class="sxs-lookup"><span data-stu-id="b5731-126">'\<identifier name>' is not a valid identifier</span></span>

<span data-ttu-id="b5731-127">此错误表示字段、方法、事件或对象的命名不正确。</span><span class="sxs-lookup"><span data-stu-id="b5731-127">This error indicates that a field, method, event, or object is improperly named.</span></span>

### <a name="name-already-exists-in-project-name"></a><span data-ttu-id="b5731-128">"" \<name> 中已存在 " \<project name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-128">'\<name>' already exists in '\<project name>'</span></span>

<span data-ttu-id="b5731-129">错误消息： "" \<name> 中已存在 "" \<project name> 。</span><span class="sxs-lookup"><span data-stu-id="b5731-129">Error message: "'\<name>' already exists in '\<project name>'.</span></span> <span data-ttu-id="b5731-130">请输入唯一的名称。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-130">Please enter a unique name."</span></span>

<span data-ttu-id="b5731-131">你为继承的表单指定了项目中已存在的名称。</span><span class="sxs-lookup"><span data-stu-id="b5731-131">You've specified a name for an inherited form that already exists in the project.</span></span> <span data-ttu-id="b5731-132">若要更正此错误，请为继承的窗体指定一个唯一名称。</span><span class="sxs-lookup"><span data-stu-id="b5731-132">To correct this error, give the inherited form a unique name.</span></span>

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a><span data-ttu-id="b5731-133">" \<Toolbox tab name> " 不是工具箱类别</span><span class="sxs-lookup"><span data-stu-id="b5731-133">'\<Toolbox tab name>' is not a toolbox category</span></span>

<span data-ttu-id="b5731-134">第三方设计器已尝试访问不存在的工具箱中的选项卡。</span><span class="sxs-lookup"><span data-stu-id="b5731-134">A third-party designer has tried to access a tab on the Toolbox that does not exist.</span></span> <span data-ttu-id="b5731-135">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-135">Contact the component vendor.</span></span>

### <a name="a-requested-language-parser-is-not-installed"></a><span data-ttu-id="b5731-136">请求的语言分析器未安装</span><span class="sxs-lookup"><span data-stu-id="b5731-136">A requested language parser is not installed</span></span>

<span data-ttu-id="b5731-137">错误消息： "未安装请求的语言分析器。</span><span class="sxs-lookup"><span data-stu-id="b5731-137">Error message: "A requested language parser is not installed.</span></span> <span data-ttu-id="b5731-138">语言分析器名称为 " {0} "。</span><span class="sxs-lookup"><span data-stu-id="b5731-138">The language parser name is '{0}'."</span></span>

<span data-ttu-id="b5731-139">Visual Studio 尝试加载已为文件类型注册但无法加载的设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-139">Visual Studio attempted to a load a designer that's registered for the file type but could not.</span></span> <span data-ttu-id="b5731-140">这很可能是由于安装过程中出现错误引起的。</span><span class="sxs-lookup"><span data-stu-id="b5731-140">This is most likely because of an error that occurred during setup.</span></span> <span data-ttu-id="b5731-141">请与要用于修复的语言的供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-141">Contact the vendor of the language you're using for a fix.</span></span>

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a><span data-ttu-id="b5731-142">缺少生成和分析源代码所需的服务</span><span class="sxs-lookup"><span data-stu-id="b5731-142">A service required for generating and parsing source code is missing</span></span>

<span data-ttu-id="b5731-143">这是第三方组件的问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-143">This is a problem with a third-party component.</span></span> <span data-ttu-id="b5731-144">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-144">Contact the component vendor.</span></span>

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a><span data-ttu-id="b5731-145">尝试创建 "" 的实例时出现异常 \<object name></span><span class="sxs-lookup"><span data-stu-id="b5731-145">An exception occurred while trying to create an instance of '\<object name>'</span></span>

<span data-ttu-id="b5731-146">错误消息： "尝试创建" "的实例时出现异常 \<object name> 。</span><span class="sxs-lookup"><span data-stu-id="b5731-146">Error message: "An exception occurred while trying to create an instance of '\<object name>'.</span></span> <span data-ttu-id="b5731-147">异常为 " \<exception string\> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-147">The exception was "\<exception string\>".</span></span>

<span data-ttu-id="b5731-148">第三方设计器请求 Visual Studio 创建一个对象，但该对象引发了一个错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-148">A third-party designer requested that Visual Studio create an object, but the object raised an error.</span></span> <span data-ttu-id="b5731-149">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-149">Contact the component vendor.</span></span>

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a><span data-ttu-id="b5731-150">另一个编辑器 \<document name> 以不兼容模式打开了 ""</span><span class="sxs-lookup"><span data-stu-id="b5731-150">Another editor has '\<document name>' open in an incompatible mode</span></span>

<span data-ttu-id="b5731-151">错误消息： "另一个编辑器 \<document name> 以不兼容模式打开了 ' '。</span><span class="sxs-lookup"><span data-stu-id="b5731-151">Error message: "Another editor has '\<document name>' open in an incompatible mode.</span></span> <span data-ttu-id="b5731-152">请关闭编辑器，然后重试此操作。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-152">Please close the editor and try this operation again."</span></span>

<span data-ttu-id="b5731-153">如果尝试打开已在另一个编辑器中打开的文件，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-153">This error arises if you try to open a file that is already opened in another editor.</span></span> <span data-ttu-id="b5731-154">将显示已打开文件的编辑器。</span><span class="sxs-lookup"><span data-stu-id="b5731-154">The editor that already has the file open is shown.</span></span> <span data-ttu-id="b5731-155">若要更正此错误，请关闭打开该文件的编辑器，然后重试。</span><span class="sxs-lookup"><span data-stu-id="b5731-155">To correct this error, close the editor that has the file open, and try again.</span></span>

### <a name="another-editor-has-made-changes-to-document-name"></a><span data-ttu-id="b5731-156">另一个编辑器已对 "" 进行了更改 \<document name></span><span class="sxs-lookup"><span data-stu-id="b5731-156">Another editor has made changes to '\<document name>'</span></span>

<span data-ttu-id="b5731-157">关闭并重新打开设计器，以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="b5731-157">Close and reopen the designer for the changes to take effect.</span></span> <span data-ttu-id="b5731-158">通常情况下，Visual Studio 会在更改完成后自动重新加载设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-158">Normally, Visual Studio automatically reloads a designer after changes are made.</span></span> <span data-ttu-id="b5731-159">但是，其他设计器（如第三方组件设计器）可能不支持重载行为。</span><span class="sxs-lookup"><span data-stu-id="b5731-159">However, other designers, such as third-party component designers, may not support reload behavior.</span></span> <span data-ttu-id="b5731-160">在这种情况下，Visual Studio 会提示您手动关闭并重新打开设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-160">In this case, Visual Studio prompts you to close and reopen the designer manually.</span></span>

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a><span data-ttu-id="b5731-161">另一个编辑器以不兼容的模式打开了此文件</span><span class="sxs-lookup"><span data-stu-id="b5731-161">Another editor has the file open in an incompatible mode</span></span>

<span data-ttu-id="b5731-162">错误消息： "另一个编辑器以不兼容模式打开了该文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-162">Error message: "Another editor has the file open in an incompatible mode.</span></span> <span data-ttu-id="b5731-163">请关闭编辑器，然后重试此操作。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-163">Please close the editor and try this operation again."</span></span>

<span data-ttu-id="b5731-164">此消息类似于 "其他编辑器 \<document name> 在不兼容模式下打开"，但 Visual Studio 无法确定文件名。</span><span class="sxs-lookup"><span data-stu-id="b5731-164">This message is similar to "Another editor has '\<document name>' open in an incompatible mode", but Visual Studio is unable to determine the file name.</span></span> <span data-ttu-id="b5731-165">若要更正此错误，请关闭打开该文件的编辑器，然后重试。</span><span class="sxs-lookup"><span data-stu-id="b5731-165">To correct this error, close the editor that has the file open, and try again.</span></span>

### <a name="array-rank-rank-in-array-is-too-high"></a><span data-ttu-id="b5731-166">数组排名 " \<rank in array> " 过高</span><span class="sxs-lookup"><span data-stu-id="b5731-166">Array rank '\<rank in array>' is too high</span></span>

<span data-ttu-id="b5731-167">Visual Studio 仅支持由设计器分析的代码块中的单维度数组。</span><span class="sxs-lookup"><span data-stu-id="b5731-167">Visual Studio only supports single-dimension arrays in the code block that's parsed by the designer.</span></span> <span data-ttu-id="b5731-168">多维数组在此区域外有效。</span><span class="sxs-lookup"><span data-stu-id="b5731-168">Multidimensional arrays are valid outside this area.</span></span>

### <a name="assembly-assembly-name-could-not-be-opened"></a><span data-ttu-id="b5731-169">未能打开程序集 " \<assembly name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-169">Assembly '\<assembly name>' could not be opened</span></span>

<span data-ttu-id="b5731-170">错误消息：无法打开 "程序集" \<assembly name> 。</span><span class="sxs-lookup"><span data-stu-id="b5731-170">Error message: "Assembly '\<assembly name>' could not be opened.</span></span> <span data-ttu-id="b5731-171">验证该文件是否仍然存在。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-171">Verify that the file still exists."</span></span>

<span data-ttu-id="b5731-172">当您尝试打开无法打开的文件时，会出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="b5731-172">This error message arises when you try to open a file that could not be opened.</span></span> <span data-ttu-id="b5731-173">请确认该文件存在并且是有效的程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-173">Verify that the file exists and is a valid assembly.</span></span>

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a><span data-ttu-id="b5731-174">错误的元素类型。</span><span class="sxs-lookup"><span data-stu-id="b5731-174">Bad element type.</span></span> <span data-ttu-id="b5731-175">此序列化程序需要类型为 " \<type name> " 的元素</span><span class="sxs-lookup"><span data-stu-id="b5731-175">This serializer expects an element of type '\<type name>'</span></span>

<span data-ttu-id="b5731-176">这是第三方组件的问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-176">This is a problem with a third-party component.</span></span> <span data-ttu-id="b5731-177">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-177">Contact the component vendor.</span></span>

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a><span data-ttu-id="b5731-178">此时无法访问 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="b5731-178">Cannot access the Visual Studio Toolbox at this time</span></span>

<span data-ttu-id="b5731-179">Visual Studio 调用了 "工具箱"，此操作不可用。</span><span class="sxs-lookup"><span data-stu-id="b5731-179">Visual Studio made a call to the Toolbox, which was not available.</span></span> <span data-ttu-id="b5731-180">如果看到此错误，请查看此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-180">If you see this error, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a><span data-ttu-id="b5731-181">无法将事件处理程序绑定到 " \<event name> " 事件，因为它是只读的</span><span class="sxs-lookup"><span data-stu-id="b5731-181">Cannot bind an event handler to the '\<event name>' event because it is read-only</span></span>

<span data-ttu-id="b5731-182">如果尝试将事件连接到从基类继承的控件，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-182">This error most often arises when you've tried to connect an event to a control that's inherited from a base class.</span></span> <span data-ttu-id="b5731-183">如果控件的成员变量是私有的，则 Visual Studio 不能将事件连接到方法。</span><span class="sxs-lookup"><span data-stu-id="b5731-183">If the control's member variable is private, Visual Studio cannot connect the event to the method.</span></span> <span data-ttu-id="b5731-184">私下继承的控件不能具有绑定到它们的附加事件。</span><span class="sxs-lookup"><span data-stu-id="b5731-184">Privately inherited controls cannot have additional events bound to them.</span></span>

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a><span data-ttu-id="b5731-185">请求的组件不是设计容器的成员，因此无法创建该组件的方法名</span><span class="sxs-lookup"><span data-stu-id="b5731-185">Cannot create a method name for the requested component because it is not a member of the design container</span></span>

<span data-ttu-id="b5731-186">Visual Studio 尝试将事件处理程序添加到设计器中没有成员变量的组件。</span><span class="sxs-lookup"><span data-stu-id="b5731-186">Visual Studio has tried to add an event handler to a component that does not have a member variable in the designer.</span></span> <span data-ttu-id="b5731-187">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-187">Contact the component vendor.</span></span>

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a><span data-ttu-id="b5731-188">对象 " \<name> " 已命名为 ""，因此无法命名该对象 \<name></span><span class="sxs-lookup"><span data-stu-id="b5731-188">Cannot name the object '\<name>' because it is already named '\<name>'</span></span>

<span data-ttu-id="b5731-189">这是 Visual Studio 序列化程序中的内部错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-189">This is an internal error in the Visual Studio serializer.</span></span> <span data-ttu-id="b5731-190">它表示序列化程序尝试将对象命名为两次，这是不受支持的。</span><span class="sxs-lookup"><span data-stu-id="b5731-190">It indicates that the serializer has tried to name an object twice, which is not supported.</span></span> <span data-ttu-id="b5731-191">如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-191">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a><span data-ttu-id="b5731-192">无法移除或损坏继承的组件 " \<component name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-192">Cannot remove or destroy inherited component '\<component name>'</span></span>

<span data-ttu-id="b5731-193">继承的控件受继承类的所有权。</span><span class="sxs-lookup"><span data-stu-id="b5731-193">Inherited controls are under the ownership of their inheriting class.</span></span> <span data-ttu-id="b5731-194">对继承控件的更改必须在控件源自的类中进行。</span><span class="sxs-lookup"><span data-stu-id="b5731-194">Changes to the inherited control must be made in the class from which the control originates.</span></span> <span data-ttu-id="b5731-195">因此，不能重命名或销毁它。</span><span class="sxs-lookup"><span data-stu-id="b5731-195">Thus, you cannot rename or destroy it.</span></span>

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a><span data-ttu-id="b5731-196">类别 " \<Toolbox tab name> " 没有类 "" 的工具 \<class name></span><span class="sxs-lookup"><span data-stu-id="b5731-196">Category '\<Toolbox tab name>' does not have a tool for class '\<class name>'</span></span>

<span data-ttu-id="b5731-197">设计器尝试引用特定 "工具箱" 选项卡上的类，但类不存在。</span><span class="sxs-lookup"><span data-stu-id="b5731-197">The designer tried to reference a class on a particular Toolbox tab, but the class does not exist.</span></span> <span data-ttu-id="b5731-198">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-198">Contact the component vendor.</span></span>

### <a name="class-class-name-has-no-matching-constructor"></a><span data-ttu-id="b5731-199">类 " \<class name> " 没有匹配的构造函数</span><span class="sxs-lookup"><span data-stu-id="b5731-199">Class '\<class name>' has no matching constructor</span></span>

<span data-ttu-id="b5731-200">第三方设计器已要求 Visual Studio 使用构造函数中不存在的特定参数创建对象。</span><span class="sxs-lookup"><span data-stu-id="b5731-200">A third-party designer has asked Visual Studio to create an object with particular parameters in the constructor that does not exist.</span></span> <span data-ttu-id="b5731-201">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-201">Contact the component vendor.</span></span>

### <a name="code-generation-for-property-property-name-failed"></a><span data-ttu-id="b5731-202">属性 "" 的代码生成 \<property name> 失败</span><span class="sxs-lookup"><span data-stu-id="b5731-202">Code generation for property '\<property name>' failed</span></span>

<span data-ttu-id="b5731-203">这是一个用于错误的泛型包装器。</span><span class="sxs-lookup"><span data-stu-id="b5731-203">This is a generic wrapper for an error.</span></span> <span data-ttu-id="b5731-204">此消息附带的错误字符串将给出有关错误消息的更多详细信息，并具有指向更具体的帮助主题的链接。</span><span class="sxs-lookup"><span data-stu-id="b5731-204">The error string that accompanies this message will give more details about the error message and have a link to a more specific help topic.</span></span> <span data-ttu-id="b5731-205">若要更正此错误，请解决附加到此错误的错误消息中指定的错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-205">To correct this error, address the error specified in the error message appended to this error.</span></span>

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a><span data-ttu-id="b5731-206">组件 " \<component name> " 在其构造函数中未调用 Container. Add （）</span><span class="sxs-lookup"><span data-stu-id="b5731-206">Component '\<component name>' did not call Container.Add() in its constructor</span></span>

<span data-ttu-id="b5731-207">这是你刚加载或放置在窗体上的组件中的错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-207">This is an error in the component you just loaded or placed on the form.</span></span> <span data-ttu-id="b5731-208">它指示组件未将自身添加到其容器控件（无论是另一个控件还是窗体）。</span><span class="sxs-lookup"><span data-stu-id="b5731-208">It indicates that the component did not add itself to its container control (whether that is another control or a form).</span></span> <span data-ttu-id="b5731-209">设计器将继续工作，但在运行时组件可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-209">The designer will continue to work, but there may be problems with the component at run time.</span></span>

<span data-ttu-id="b5731-210">若要更正此错误，请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-210">To correct the error, contact the component vendor.</span></span> <span data-ttu-id="b5731-211">或者，如果它是您创建的组件，请 `IContainer.Add` 在组件的构造函数中调用方法。</span><span class="sxs-lookup"><span data-stu-id="b5731-211">Or, if it is a component you created, call the `IContainer.Add` method in the component's constructor.</span></span>

### <a name="component-name-cannot-be-empty"></a><span data-ttu-id="b5731-212">组件名称不能为空</span><span class="sxs-lookup"><span data-stu-id="b5731-212">Component name cannot be empty</span></span>

<span data-ttu-id="b5731-213">当你尝试将组件重命名为空值时，会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-213">This error arises when you try to rename a component to an empty value.</span></span>

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a><span data-ttu-id="b5731-214">无法访问变量 " \<variable name> "，因为它尚未初始化</span><span class="sxs-lookup"><span data-stu-id="b5731-214">Could not access the variable '\<variable name>' because it has not been initialized yet</span></span>

<span data-ttu-id="b5731-215">出现此错误的原因可能是两个方案。</span><span class="sxs-lookup"><span data-stu-id="b5731-215">This error can arise because of two scenarios.</span></span> <span data-ttu-id="b5731-216">第三方组件供应商在其分布的控件或组件有问题，或您编写的代码在组件之间具有递归依赖关系。</span><span class="sxs-lookup"><span data-stu-id="b5731-216">Either a third-party component vendor has a problem with a control or component they have distributed, or the code you have written has recursive dependencies between components.</span></span>

<span data-ttu-id="b5731-217">若要更正此错误，请确保你的代码不具有递归依赖项。</span><span class="sxs-lookup"><span data-stu-id="b5731-217">To correct this error, ensure that your code does not have a recursive dependency.</span></span> <span data-ttu-id="b5731-218">如果没有此类问题，请记录错误消息的确切文本，并与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-218">If it is free of such problems, note the exact text of the error message and contact the component vendor.</span></span>

### <a name="could-not-find-type-type-name"></a><span data-ttu-id="b5731-219">未能找到类型 " \<type name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-219">Could not find type '\<type name>'</span></span>

<span data-ttu-id="b5731-220">错误消息： "找不到类型" \<type name> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-220">Error message: "Could not find type '\<type name>'.</span></span> <span data-ttu-id="b5731-221">请确保引用包含此类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-221">Please make sure that the assembly that contains this type is referenced.</span></span> <span data-ttu-id="b5731-222">如果此类型是开发项目的一部分，请确保已成功生成项目。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-222">If this type is a part of your development project, make sure that the project has been successfully built."</span></span>

<span data-ttu-id="b5731-223">发生此错误的原因是找不到引用。</span><span class="sxs-lookup"><span data-stu-id="b5731-223">This error occurred because a reference was not found.</span></span> <span data-ttu-id="b5731-224">请确保引用错误消息中指示的类型，并且还会引用该类型所需的任何程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-224">Make sure the type indicated in the error message is referenced, and that any assemblies that the type requires are also referenced.</span></span> <span data-ttu-id="b5731-225">通常，问题在于解决方案中的某个控件尚未生成。</span><span class="sxs-lookup"><span data-stu-id="b5731-225">Often, the problem is that a control in the solution has not been built.</span></span> <span data-ttu-id="b5731-226">若要生成，请从 "**生成**" 菜单中选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="b5731-226">To build, select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="b5731-227">否则，如果已经生成了控件，请从解决方案资源管理器中的 "**引用**" 或 "**依赖项**" 文件夹的右键单击菜单手动添加引用。</span><span class="sxs-lookup"><span data-stu-id="b5731-227">Otherwise, if the control has already been built, add a reference manually from the right-click menu of the **References** or **Dependencies** folder in Solution Explorer.</span></span>

### <a name="could-not-load-type-type-name"></a><span data-ttu-id="b5731-228">未能加载类型 " \<type name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-228">Could not load type '\<type name>'</span></span>

<span data-ttu-id="b5731-229">错误消息： "无法加载类型" \<type name> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-229">Error message: "Could not load type '\<type name>'.</span></span> <span data-ttu-id="b5731-230">请确保将包含此类型的程序集添加到项目引用中。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-230">Please make sure that the assembly containing this type is added to the project references."</span></span>

<span data-ttu-id="b5731-231">Visual Studio 尝试连接事件处理方法，但找不到方法的一个或多个参数类型。</span><span class="sxs-lookup"><span data-stu-id="b5731-231">Visual Studio attempted to wire up an event-handling method and could not find one or more parameter types for the method.</span></span> <span data-ttu-id="b5731-232">这通常是由于缺少引用引起的。</span><span class="sxs-lookup"><span data-stu-id="b5731-232">This is usually caused by a missing reference.</span></span> <span data-ttu-id="b5731-233">若要更正此错误，请将包含该类型的引用添加到该项目，然后重试。</span><span class="sxs-lookup"><span data-stu-id="b5731-233">To correct this error, add the reference containing the type to the project and try again.</span></span>

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a><span data-ttu-id="b5731-234">未能找到继承的组件的项目项模板</span><span class="sxs-lookup"><span data-stu-id="b5731-234">Could not locate the project item templates for inherited components</span></span>

<span data-ttu-id="b5731-235">Visual Studio 中的继承窗体的模板不可用。</span><span class="sxs-lookup"><span data-stu-id="b5731-235">The templates for inherited forms in Visual Studio are not available.</span></span> <span data-ttu-id="b5731-236">如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-236">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a><span data-ttu-id="b5731-237">委托类 " \<class name> " 没有 invoke 方法。</span><span class="sxs-lookup"><span data-stu-id="b5731-237">Delegate class '\<class name>' has no invoke method.</span></span> <span data-ttu-id="b5731-238">此类是否为委托？</span><span class="sxs-lookup"><span data-stu-id="b5731-238">Is this class a delegate?</span></span>

<span data-ttu-id="b5731-239">Visual Studio 已尝试创建事件处理程序，但事件类型出现错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-239">Visual Studio has tried to create an event handler, but there is something wrong with the event type.</span></span> <span data-ttu-id="b5731-240">如果事件是由不符合 CLS 的语言创建的，则可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="b5731-240">This can happen if the event was created by a non-CLS-compliant language.</span></span> <span data-ttu-id="b5731-241">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-241">Contact the component vendor.</span></span>

### <a name="duplicate-declaration-of-member-member-name"></a><span data-ttu-id="b5731-242">成员 "" 的重复声明 \<member name></span><span class="sxs-lookup"><span data-stu-id="b5731-242">Duplicate declaration of member '\<member name>'</span></span>

<span data-ttu-id="b5731-243">出现此错误的原因是成员变量已被声明了两次（例如， `Button1` 在代码中声明了两个名为的控件）。</span><span class="sxs-lookup"><span data-stu-id="b5731-243">This error arises because a member variable has been declared twice (for example, two controls named `Button1` are declared in the code).</span></span> <span data-ttu-id="b5731-244">名称在继承的窗体中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="b5731-244">Names must be unique across inherited forms.</span></span> <span data-ttu-id="b5731-245">此外，名称不能仅区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b5731-245">Additionally, names cannot differ only by case.</span></span>

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a><span data-ttu-id="b5731-246">从区域性 "" 的资源文件中读取资源时出错 \<culture name></span><span class="sxs-lookup"><span data-stu-id="b5731-246">Error reading resources from the resource file for the culture '\<culture name>'</span></span>

<span data-ttu-id="b5731-247">如果项目中存在错误的 .resx 文件，则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-247">This error can occur if there is a bad .resx file in the project.</span></span>

<span data-ttu-id="b5731-248">若要更正该错误，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b5731-248">To correct this error:</span></span>

1. <span data-ttu-id="b5731-249">单击解决方案资源管理器中的 "**显示所有文件**" 按钮，查看与该解决方案相关联的 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-249">Click the **Show All Files** button in Solution Explorer to view the .resx files associated with the solution.</span></span>
2. <span data-ttu-id="b5731-250">右键单击 .resx 文件，然后选择 "**打开**"，在 XML 编辑器中加载 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-250">Load the .resx file in the XML Editor by right-clicking the .resx file and choosing **Open**.</span></span>
3. <span data-ttu-id="b5731-251">手动编辑 .resx 文件以解决错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-251">Edit the .resx file manually to address the errors.</span></span>

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a><span data-ttu-id="b5731-252">从默认区域性 "" 的资源文件中读取资源时出错 \<culture name></span><span class="sxs-lookup"><span data-stu-id="b5731-252">Error reading resources from the resource file for the default culture '\<culture name>'</span></span>

<span data-ttu-id="b5731-253">如果默认区域性的项目中有无效的 .resx 文件，则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-253">This error can occur if there is a bad .resx file in the project for the default culture.</span></span>

<span data-ttu-id="b5731-254">若要更正该错误，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b5731-254">To correct this error:</span></span>

1. <span data-ttu-id="b5731-255">单击解决方案资源管理器中的 "**显示所有文件**" 按钮，查看与该解决方案相关联的 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-255">Click the **Show All Files** button in Solution Explorer to view the .resx files associated with the solution.</span></span>
2. <span data-ttu-id="b5731-256">右键单击 .resx 文件，然后选择 "**打开**"，在 XML 编辑器中加载 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-256">Load the .resx file in the XML Editor by right-clicking the .resx file and choosing **Open**.</span></span>
3. <span data-ttu-id="b5731-257">手动编辑 .resx 文件以解决错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-257">Edit the .resx file manually to address the errors.</span></span>

### <a name="failed-to-parse-method-method-name"></a><span data-ttu-id="b5731-258">未能分析方法 " \<method name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-258">Failed to parse method '\<method name>'</span></span>

<span data-ttu-id="b5731-259">错误消息： "无法分析方法" \<method name> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-259">Error message: "Failed to parse method '\<method name>'.</span></span> <span data-ttu-id="b5731-260">分析器报告以下错误： " \<error string> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-260">The parser reported the following error: '\<error string>'.</span></span> <span data-ttu-id="b5731-261">请查看任务列表是否有可能的错误。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-261">Please look in the Task List for potential errors."</span></span>

<span data-ttu-id="b5731-262">这是分析过程中出现的问题的常规错误消息。</span><span class="sxs-lookup"><span data-stu-id="b5731-262">This is a general error message for problems that arise during parsing.</span></span> <span data-ttu-id="b5731-263">这些错误通常是由语法错误引起的。</span><span class="sxs-lookup"><span data-stu-id="b5731-263">These errors are often due to syntax errors.</span></span> <span data-ttu-id="b5731-264">请参阅与错误相关的特定消息的任务列表。</span><span class="sxs-lookup"><span data-stu-id="b5731-264">See the Task List for specific messages related to the error.</span></span>

### <a name="invalid-component-name-component-name"></a><span data-ttu-id="b5731-265">无效的组件名称： " \<component name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-265">Invalid component name: '\<component name>'</span></span>

<span data-ttu-id="b5731-266">您尝试将组件重命名为该语言的无效值。</span><span class="sxs-lookup"><span data-stu-id="b5731-266">You've tried to rename a component to an invalid value for that language.</span></span> <span data-ttu-id="b5731-267">若要更正此错误，请为组件命名，使其符合该语言的命名规则。</span><span class="sxs-lookup"><span data-stu-id="b5731-267">To correct this error, name the component such that it complies with the naming rules for that language.</span></span>

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a><span data-ttu-id="b5731-268">类型 " \<class name> " 由同一文件中的几个分部类组成</span><span class="sxs-lookup"><span data-stu-id="b5731-268">The type '\<class name>' is made of several partial classes in the same file</span></span>

<span data-ttu-id="b5731-269">使用[partial](../../../csharp/language-reference/keywords/partial-type.md)关键字在多个文件中定义类时，每个文件中只能有一个部分定义。</span><span class="sxs-lookup"><span data-stu-id="b5731-269">When you define a class in multiple files by using the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword, you can only have one partial definition in each file.</span></span>

<span data-ttu-id="b5731-270">若要更正此错误，请从文件中删除类的所有分部定义之外的所有部分定义。</span><span class="sxs-lookup"><span data-stu-id="b5731-270">To correct this error, remove all but one of the partial definitions of your class from the file.</span></span>

### <a name="the-assembly-assembly-name-could-not-be-found"></a><span data-ttu-id="b5731-271">未能找到程序集 " \<assembly name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-271">The assembly '\<assembly name>' could not be found</span></span>

<span data-ttu-id="b5731-272">错误消息： "找不到程序集" \<assembly name> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-272">Error message: "The assembly '\<assembly name>' could not be found.</span></span> <span data-ttu-id="b5731-273">确保引用该程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-273">Ensure that the assembly is referenced.</span></span> <span data-ttu-id="b5731-274">如果程序集是当前开发项目的一部分，请确保已生成项目。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-274">If the assembly is part of the current development project, ensure that the project has been built."</span></span>

<span data-ttu-id="b5731-275">此错误类似于 "找不到类型" \<type name> ，但此错误通常是由于元数据属性造成的。</span><span class="sxs-lookup"><span data-stu-id="b5731-275">This error is similar to "The type '\<type name>' could not be found", but this error usually happens because of a metadata attribute.</span></span> <span data-ttu-id="b5731-276">若要更正此错误，请检查是否引用了属性使用的所有程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-276">To correct this error, check that all assemblies used by attributes are referenced.</span></span>

### <a name="the-assembly-name-assembly-name-is-invalid"></a><span data-ttu-id="b5731-277">程序集名称 " \<assembly name> " 无效</span><span class="sxs-lookup"><span data-stu-id="b5731-277">The assembly name '\<assembly name>' is invalid</span></span>

<span data-ttu-id="b5731-278">组件已请求特定程序集，但组件提供的名称不是有效的程序集名称。</span><span class="sxs-lookup"><span data-stu-id="b5731-278">A component has requested a particular assembly, but the name provided by the component is not a valid assembly name.</span></span> <span data-ttu-id="b5731-279">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-279">Contact the component vendor.</span></span>

### <a name="the-base-class-class-name-cannot-be-designed"></a><span data-ttu-id="b5731-280">无法设计基类 " \<class name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-280">The base class '\<class name>' cannot be designed</span></span>

<span data-ttu-id="b5731-281">Visual Studio 加载了类，但无法设计该类，因为该类的实施者未提供设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-281">Visual Studio loaded the class, but the class cannot be designed because the implementer of the class did not provide a designer.</span></span> <span data-ttu-id="b5731-282">如果类支持设计器，请确保没有任何问题导致在设计器中显示它（例如编译器错误）时出现问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-282">If the class supports a designer, make sure there are no problems that would cause issues with displaying it in a designer, such as compiler errors.</span></span> <span data-ttu-id="b5731-283">另外，请确保对类的所有引用都是正确的，并且所有类名的拼写正确。</span><span class="sxs-lookup"><span data-stu-id="b5731-283">Also, make sure that all references to the class are correct and all class names are correctly spelled.</span></span> <span data-ttu-id="b5731-284">否则，如果类不是可设计的，请在代码视图中对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="b5731-284">Otherwise, if the class is not designable, edit it in Code view.</span></span>

### <a name="the-base-class-class-name-could-not-be-loaded"></a><span data-ttu-id="b5731-285">无法加载基类 " \<class name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-285">The base class '\<class name>' could not be loaded</span></span>

<span data-ttu-id="b5731-286">项目中未引用类，因此 Visual Studio 无法加载它。</span><span class="sxs-lookup"><span data-stu-id="b5731-286">The class is not referenced in the project, so Visual Studio can't load it.</span></span> <span data-ttu-id="b5731-287">若要更正此错误，请在项目中添加对类的引用，然后关闭并重新打开 Windows 窗体设计器窗口。</span><span class="sxs-lookup"><span data-stu-id="b5731-287">To correct this error, add a reference to the class in the project, and close and reopen the Windows Forms Designer window.</span></span>

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a><span data-ttu-id="b5731-288">类 " \<class name> " 不能在此版本的 Visual Studio 中设计</span><span class="sxs-lookup"><span data-stu-id="b5731-288">The class '\<class name>' cannot be designed in this version of Visual Studio</span></span>

<span data-ttu-id="b5731-289">此控件或组件的设计器不支持 Visual Studio 所用的相同类型。</span><span class="sxs-lookup"><span data-stu-id="b5731-289">The designer for this control or component does not support the same types that Visual Studio does.</span></span> <span data-ttu-id="b5731-290">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-290">Contact the component vendor.</span></span>

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a><span data-ttu-id="b5731-291">该类名不是此语言的有效标识符</span><span class="sxs-lookup"><span data-stu-id="b5731-291">The class name is not a valid identifier for this language</span></span>

<span data-ttu-id="b5731-292">用户创建的源代码的类名称对所使用的语言无效。</span><span class="sxs-lookup"><span data-stu-id="b5731-292">The source code being created by the user has a class name that is not valid for the language being used.</span></span> <span data-ttu-id="b5731-293">若要更正此错误，请将类命名为符合语言要求。</span><span class="sxs-lookup"><span data-stu-id="b5731-293">To correct this error, name the class such that it conforms to the language requirements.</span></span>

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a><span data-ttu-id="b5731-294">无法添加该组件，因为它包含对 "" 的循环引用 \<reference name></span><span class="sxs-lookup"><span data-stu-id="b5731-294">The component cannot be added because it contains a circular reference to '\<reference name>'</span></span>

<span data-ttu-id="b5731-295">不能将控件或组件添加到其自身。</span><span class="sxs-lookup"><span data-stu-id="b5731-295">You cannot add a control or component to itself.</span></span> <span data-ttu-id="b5731-296">如果出现这种情况，则可能会发生这种情况：在 InitializeComponent 方法中，有一个创建另一个 Form1 实例的窗体的代码。</span><span class="sxs-lookup"><span data-stu-id="b5731-296">Another situation where this might occur is if there is code in the InitializeComponent method of a form (for example, Form1) that creates another instance of Form1.</span></span>

### <a name="the-designer-cannot-be-modified-at-this-time"></a><span data-ttu-id="b5731-297">此时无法修改设计器</span><span class="sxs-lookup"><span data-stu-id="b5731-297">The designer cannot be modified at this time</span></span>

<span data-ttu-id="b5731-298">当编辑器中的文件标记为只读时，会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-298">This error occurs when the file in the editor is marked as read-only.</span></span> <span data-ttu-id="b5731-299">确保该文件未标记为只读并且应用程序未运行。</span><span class="sxs-lookup"><span data-stu-id="b5731-299">Ensure that the file is not marked read-only and the application is not running.</span></span>

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a><span data-ttu-id="b5731-300">文件中的类都不能进行设计，因此未能为该文件显示设计器</span><span class="sxs-lookup"><span data-stu-id="b5731-300">The designer could not be shown for this file because none of the classes within it can be designed</span></span>

<span data-ttu-id="b5731-301">当 Visual Studio 找不到满足设计器要求的基类时，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-301">This error occurs when Visual Studio cannot find a base class that satisfies designer requirements.</span></span> <span data-ttu-id="b5731-302">窗体和控件必须派生自支持设计器的基类。</span><span class="sxs-lookup"><span data-stu-id="b5731-302">Forms and controls must derive from a base class that supports designers.</span></span> <span data-ttu-id="b5731-303">如果要从继承的窗体或控件派生，请确保已生成项目。</span><span class="sxs-lookup"><span data-stu-id="b5731-303">If you're deriving from an inherited form or control, make sure the project has been built.</span></span>

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a><span data-ttu-id="b5731-304">未安装基类 "" 的设计器 \<class name></span><span class="sxs-lookup"><span data-stu-id="b5731-304">The designer for base class '\<class name>' is not installed</span></span>

<span data-ttu-id="b5731-305">Visual Studio 无法加载类的设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-305">Visual Studio could not load the designer for the class.</span></span> <span data-ttu-id="b5731-306">如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-306">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a><span data-ttu-id="b5731-307">设计器必须创建类型为 "" 的实例 \<type name> ，但由于该类型已声明为抽象类型，因此无法创建该类型的实例</span><span class="sxs-lookup"><span data-stu-id="b5731-307">The designer must create an instance of type '\<type name>', but it can't because the type is declared as abstract</span></span>

<span data-ttu-id="b5731-308">发生此错误的原因是，传递到设计器的对象的基类是[抽象](../../../csharp/language-reference/keywords/abstract.md)的，这是不允许的。</span><span class="sxs-lookup"><span data-stu-id="b5731-308">This error occurred because the base class of the object being passed to the designer is [abstract](../../../csharp/language-reference/keywords/abstract.md), which is not allowed.</span></span>

### <a name="the-file-could-not-be-loaded-in-the-designer"></a><span data-ttu-id="b5731-309">未能在设计器中加载该文件</span><span class="sxs-lookup"><span data-stu-id="b5731-309">The file could not be loaded in the designer</span></span>

<span data-ttu-id="b5731-310">此文件的基类不支持任何设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-310">The base class of this file does not support any designers.</span></span> <span data-ttu-id="b5731-311">作为一种解决方法，使用代码视图处理该文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-311">As a workaround, use Code view to work on the file.</span></span> <span data-ttu-id="b5731-312">在解决方案资源管理器中右键单击该文件，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="b5731-312">Right-click the file in Solution Explorer and choose **View Code**.</span></span>

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a><span data-ttu-id="b5731-313">该文件的语言不支持必需的代码分析和生成服务</span><span class="sxs-lookup"><span data-stu-id="b5731-313">The language for this file does not support the necessary code parsing and generation services</span></span>

<span data-ttu-id="b5731-314">错误消息： "此文件的语言不支持必要的代码分析和生成服务。</span><span class="sxs-lookup"><span data-stu-id="b5731-314">Error message: "The language for this file does not support the necessary code parsing and generation services.</span></span> <span data-ttu-id="b5731-315">请确保正在打开的文件是项目的成员，然后再次尝试打开该文件。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-315">Please ensure the file you are opening is a member of a project and then try to open the file again."</span></span>

<span data-ttu-id="b5731-316">此错误最有可能是由于打开的项目中的文件不支持设计器而导致的。</span><span class="sxs-lookup"><span data-stu-id="b5731-316">This error most likely resulted from opening a file that's in a project that does not support designers.</span></span>

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a><span data-ttu-id="b5731-317">语言分析器类 " \<class name> " 未正确实现</span><span class="sxs-lookup"><span data-stu-id="b5731-317">The language parser class '\<class name>' is not implemented properly</span></span>

<span data-ttu-id="b5731-318">错误消息： "语言分析器类" \<class name> "未正确实现。</span><span class="sxs-lookup"><span data-stu-id="b5731-318">Error message: "The language parser class '\<class name>' is not implemented properly.</span></span> <span data-ttu-id="b5731-319">请与供应商联系以获取更新的分析器模块。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-319">Contact the vendor for an updated parser module."</span></span>

<span data-ttu-id="b5731-320">所使用的语言已注册了一个不是从正确的基类派生的设计器类。</span><span class="sxs-lookup"><span data-stu-id="b5731-320">The language in use has registered a designer class that doesn't derive from the correct base class.</span></span> <span data-ttu-id="b5731-321">联系你使用的语言的供应商。</span><span class="sxs-lookup"><span data-stu-id="b5731-321">Contact the vendor of the language you're using.</span></span>

### <a name="the-name-name-is-already-used-by-another-object"></a><span data-ttu-id="b5731-322">名称 " \<name> " 已由另一个对象使用</span><span class="sxs-lookup"><span data-stu-id="b5731-322">The name '\<name>' is already used by another object</span></span>

<span data-ttu-id="b5731-323">这是 Visual Studio 序列化程序中的内部错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-323">This is an internal error in the Visual Studio serializer.</span></span> <span data-ttu-id="b5731-324">如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-324">If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a><span data-ttu-id="b5731-325">对象 " \<object name> " 未实现 IComponent 接口</span><span class="sxs-lookup"><span data-stu-id="b5731-325">The object '\<object name>' does not implement the IComponent interface</span></span>

<span data-ttu-id="b5731-326">Visual Studio 尝试创建组件，但所创建的对象未实现 <xref:System.ComponentModel.IComponent> 接口。</span><span class="sxs-lookup"><span data-stu-id="b5731-326">Visual Studio tried to create a component, but the object created does not implement the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="b5731-327">请与组件供应商联系以获取修补程序。</span><span class="sxs-lookup"><span data-stu-id="b5731-327">Contact the component vendor for a fix.</span></span>

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a><span data-ttu-id="b5731-328">对象 " \<object name> " 为属性 "" 返回了 null， \<property name> 但这是不允许的</span><span class="sxs-lookup"><span data-stu-id="b5731-328">The object '\<object name>' returned null for the property '\<property name>' but this is not allowed</span></span>

<span data-ttu-id="b5731-329">有一些应始终返回对象的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="b5731-329">There are some .NET properties that should always return an object.</span></span> <span data-ttu-id="b5731-330">例如，窗体的**控件**集合应始终返回对象，即使其中没有任何控件也是如此。</span><span class="sxs-lookup"><span data-stu-id="b5731-330">For example, the **Controls** collection of a form should always return an object, even when there are no controls in it.</span></span>

<span data-ttu-id="b5731-331">若要更正此错误，请确保错误中指定的属性不为 null。</span><span class="sxs-lookup"><span data-stu-id="b5731-331">To correct this error, ensure that the property specified in the error is not null.</span></span>

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a><span data-ttu-id="b5731-332">序列化数据对象的类型不正确</span><span class="sxs-lookup"><span data-stu-id="b5731-332">The serialization data object is not of the proper type</span></span>

<span data-ttu-id="b5731-333">序列化程序提供的数据对象不是与当前正在使用的序列化程序匹配的类型的实例。</span><span class="sxs-lookup"><span data-stu-id="b5731-333">A data object offered by the serializer is not an instance of a type that matches the current serializer being used.</span></span> <span data-ttu-id="b5731-334">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-334">Contact the component vendor.</span></span>

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a><span data-ttu-id="b5731-335">服务 " \<service name> " 是必需的，但未能找到</span><span class="sxs-lookup"><span data-stu-id="b5731-335">The service '\<service name>' is required, but could not be located</span></span>

<span data-ttu-id="b5731-336">错误消息： "服务" \<service name> "是必需的，但找不到。</span><span class="sxs-lookup"><span data-stu-id="b5731-336">Error message: "The service '\<service name>' is required, but could not be located.</span></span> <span data-ttu-id="b5731-337">Visual Studio 安装可能有问题。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-337">There may be a problem with your Visual Studio installation."</span></span>

<span data-ttu-id="b5731-338">Visual Studio 所需的服务不可用。</span><span class="sxs-lookup"><span data-stu-id="b5731-338">A service required by Visual Studio is unavailable.</span></span> <span data-ttu-id="b5731-339">如果尝试加载的项目不支持该设计器，请使用代码编辑器进行所需的更改。</span><span class="sxs-lookup"><span data-stu-id="b5731-339">If you were trying to load a project that does not support that designer, use the Code Editor to make the changes you require.</span></span> <span data-ttu-id="b5731-340">否则，如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-340">Otherwise, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a><span data-ttu-id="b5731-341">服务实例必须派生自或实现 " \<interface name> "</span><span class="sxs-lookup"><span data-stu-id="b5731-341">The service instance must derive from or implement '\<interface name>'</span></span>

<span data-ttu-id="b5731-342">此错误表示组件或组件设计器调用了**AddService**方法，该方法需要接口和对象，但指定的对象未实现指定的接口。</span><span class="sxs-lookup"><span data-stu-id="b5731-342">This error indicates that a component or component designer has called the **AddService** method, which requires an interface and object, but the object specified does not implement the interface specified.</span></span> <span data-ttu-id="b5731-343">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-343">Contact the component vendor.</span></span>

### <a name="the-text-in-the-code-window-could-not-be-modified"></a><span data-ttu-id="b5731-344">未能修改代码窗口中的文本</span><span class="sxs-lookup"><span data-stu-id="b5731-344">The text in the code window could not be modified</span></span>

<span data-ttu-id="b5731-345">错误消息： "无法修改代码窗口中的文本。</span><span class="sxs-lookup"><span data-stu-id="b5731-345">Error message: "The text in the code window could not be modified.</span></span> <span data-ttu-id="b5731-346">请检查该文件是否不是只读的，以及是否有足够的磁盘空间。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-346">Check that the file is not read-only and there is sufficient disk space."</span></span>

<span data-ttu-id="b5731-347">由于磁盘空间或内存问题导致 Visual Studio 无法编辑文件，或者文件被标记为只读时，会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-347">This error occurs when Visual Studio is unable to edit a file due to disk space or memory problems, or the file is marked read-only.</span></span>

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a><span data-ttu-id="b5731-348">工具箱枚举数对象仅支持一次检索一个项</span><span class="sxs-lookup"><span data-stu-id="b5731-348">The Toolbox enumerator object only supports retrieving one item at a time</span></span>

<span data-ttu-id="b5731-349">如果看到此错误，请查看此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-349">If you see this error, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a><span data-ttu-id="b5731-350">\<component name>无法从工具箱检索 "" 的工具箱项</span><span class="sxs-lookup"><span data-stu-id="b5731-350">The Toolbox item for '\<component name>' could not be retrieved from the Toolbox</span></span>

<span data-ttu-id="b5731-351">错误消息： " \<component name> 无法从工具箱检索" "的工具箱项。</span><span class="sxs-lookup"><span data-stu-id="b5731-351">Error message: "The Toolbox item for '\<component name>' could not be retrieved from the Toolbox.</span></span> <span data-ttu-id="b5731-352">请确保正确安装了包含工具箱项的程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-352">Make sure the assembly that contains the Toolbox item is correctly installed.</span></span> <span data-ttu-id="b5731-353">工具箱项引发了以下错误： \<error string> 。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-353">The Toolbox item raised the following error: \<error string>."</span></span>

<span data-ttu-id="b5731-354">当 Visual Studio 对其进行访问时，有问题的组件引发异常。</span><span class="sxs-lookup"><span data-stu-id="b5731-354">The component in question threw an exception when Visual Studio accessed it.</span></span> <span data-ttu-id="b5731-355">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-355">Contact the component vendor.</span></span>

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a><span data-ttu-id="b5731-356">\<Toolbox item name>无法从工具箱检索 "" 的工具箱项</span><span class="sxs-lookup"><span data-stu-id="b5731-356">The Toolbox item for '\<Toolbox item name>' could not be retrieved from the Toolbox</span></span>

<span data-ttu-id="b5731-357">错误消息： " \<Toolbox item name> 无法从工具箱检索" "的工具箱项。</span><span class="sxs-lookup"><span data-stu-id="b5731-357">Error message: "The Toolbox item for '\<Toolbox item name>' could not be retrieved from the Toolbox.</span></span> <span data-ttu-id="b5731-358">请尝试删除 "工具箱" 中的项并将其添加回去。</span><span class="sxs-lookup"><span data-stu-id="b5731-358">Try removing the item from the Toolbox and adding it back."</span></span>

<span data-ttu-id="b5731-359">如果工具箱项中的数据损坏或组件的版本发生了更改，则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-359">This error occurs if the data within the Toolbox item becomes corrupted or the version of the component has changed.</span></span> <span data-ttu-id="b5731-360">尝试从工具箱中移除该项，然后重新添加。</span><span class="sxs-lookup"><span data-stu-id="b5731-360">Try removing the item from the Toolbox and adding it back again.</span></span>

### <a name="the-type-type-name-could-not-be-found"></a><span data-ttu-id="b5731-361">\<type name>未能找到类型 ""</span><span class="sxs-lookup"><span data-stu-id="b5731-361">The type '\<type name>' could not be found</span></span>

<span data-ttu-id="b5731-362">错误消息： "找不到类型" \<type name> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-362">Error message: "The type '\<type name>' could not be found.</span></span> <span data-ttu-id="b5731-363">确保引用包含该类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-363">Ensure that the assembly containing the type is referenced.</span></span> <span data-ttu-id="b5731-364">如果程序集是当前开发项目的一部分，请确保已生成项目。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-364">If the assembly is part of the current development project, ensure that the project has been built."</span></span>

<span data-ttu-id="b5731-365">加载设计器时，Visual Studio 找不到类型。</span><span class="sxs-lookup"><span data-stu-id="b5731-365">While loading the designer, Visual Studio failed to find a type.</span></span> <span data-ttu-id="b5731-366">确保引用包含该类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="b5731-366">Ensure that the assembly containing the type is referenced.</span></span> <span data-ttu-id="b5731-367">如果程序集是当前开发项目的一部分，请确保已生成项目。</span><span class="sxs-lookup"><span data-stu-id="b5731-367">If the assembly is part of the current development project, ensure that the project has been built.</span></span>

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a><span data-ttu-id="b5731-368">只能从主应用程序线程调用类型解析服务</span><span class="sxs-lookup"><span data-stu-id="b5731-368">The type resolution service may only be called from the main application thread</span></span>

<span data-ttu-id="b5731-369">Visual Studio 尝试从错误的线程访问所需资源。</span><span class="sxs-lookup"><span data-stu-id="b5731-369">Visual Studio attempted to access required resources from the wrong thread.</span></span> <span data-ttu-id="b5731-370">当用于创建设计器的代码从主应用程序线程以外的线程调用类型解析服务时，将显示此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-370">This error is displayed when the code used to create the designer has called the type resolution service from a thread other than the main application thread.</span></span> <span data-ttu-id="b5731-371">若要更正此错误，请从正确的线程调用服务，或与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-371">To correct this error, call the service from the correct thread or contact the component vendor.</span></span>

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a><span data-ttu-id="b5731-372">变量 " \<variable name> " 未声明或从未赋值</span><span class="sxs-lookup"><span data-stu-id="b5731-372">The variable '\<variable name>' is either undeclared or was never assigned</span></span>

<span data-ttu-id="b5731-373">源代码引用了对变量的引用，例如**Button1**，未声明或赋值。</span><span class="sxs-lookup"><span data-stu-id="b5731-373">The source code has a reference to a variable, such as **Button1**, that isn't declared or assigned.</span></span> <span data-ttu-id="b5731-374">如果尚未分配该变量，则此消息将显示为警告而不是错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-374">If the variable has not been assigned, this message appears as a warning, not an error.</span></span>

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a><span data-ttu-id="b5731-375">菜单命令 "" 已经有一个命令处理程序 \<menu command name></span><span class="sxs-lookup"><span data-stu-id="b5731-375">There is already a command handler for the menu command '\<menu command name>'</span></span>

<span data-ttu-id="b5731-376">如果第三方设计器将已有处理程序的命令添加到命令表，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-376">This error arises if a third-party designer adds a command that already has a handler to the command table.</span></span> <span data-ttu-id="b5731-377">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-377">Contact the component vendor.</span></span>

### <a name="there-is-already-a-component-named-component-name"></a><span data-ttu-id="b5731-378">已存在名为 "" 的组件 \<component name></span><span class="sxs-lookup"><span data-stu-id="b5731-378">There is already a component named '\<component name>'</span></span>

<span data-ttu-id="b5731-379">错误消息： "已存在名为" "的组件 \<component name> 。</span><span class="sxs-lookup"><span data-stu-id="b5731-379">Error message: "There is already a component named '\<component name>'.</span></span> <span data-ttu-id="b5731-380">组件必须具有唯一的名称，并且名称必须不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b5731-380">Components must have unique names, and names must not be case-sensitive.</span></span> <span data-ttu-id="b5731-381">名称也不能与继承类中任何组件的名称冲突。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-381">A name also cannot conflict with the name of any component in an inherited class."</span></span>

<span data-ttu-id="b5731-382">如果在属性窗口中更改了组件的名称，则会出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="b5731-382">This error message arises when there has been a change to the name of a component in the Properties window.</span></span> <span data-ttu-id="b5731-383">若要更正此错误，请确保所有组件名称都是唯一的，不区分大小写，并且不会与继承的类中任何组件的名称冲突。</span><span class="sxs-lookup"><span data-stu-id="b5731-383">To correct this error, ensure that all component names are unique, are not case-sensitive, and do not conflict with the names of any components in the inherited classes.</span></span>

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a><span data-ttu-id="b5731-384">已为 "" 格式注册工具箱项创建者 \<format name></span><span class="sxs-lookup"><span data-stu-id="b5731-384">There is already a Toolbox item creator registered for the format '\<format name>'</span></span>

<span data-ttu-id="b5731-385">第三方组件对 "工具箱" 选项卡上的项进行了回调，但该项已经包含了一个回调。</span><span class="sxs-lookup"><span data-stu-id="b5731-385">A third-party component made a callback to an item on a Toolbox tab, but the item already contained a callback.</span></span> <span data-ttu-id="b5731-386">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-386">Contact the component vendor.</span></span>

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a><span data-ttu-id="b5731-387">此语言引擎不支持用于加载设计器的 CodeModel</span><span class="sxs-lookup"><span data-stu-id="b5731-387">This language engine does not support a CodeModel with which to load a designer</span></span>

<span data-ttu-id="b5731-388">此消息类似于 "此文件的语言不支持必要的代码分析和生成服务"，但此消息涉及内部注册问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-388">This message is similar to "The language for this file does not support the necessary code parsing and generation services", but this message involves an internal registration problem.</span></span> <span data-ttu-id="b5731-389">如果看到此错误，请查看此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-389">If you see this error, If you see this error, please log an issue by using [Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).</span></span>

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a><span data-ttu-id="b5731-390">类型 " \<type name\> " 没有具有类型为 "" 的参数的构造函数 \<parameter type names></span><span class="sxs-lookup"><span data-stu-id="b5731-390">Type '\<type name\>' does not have a constructor with parameters of types '\<parameter type names>'</span></span>

<span data-ttu-id="b5731-391">Visual Studio 找不到具有匹配参数的[构造函数](../../../csharp/programming-guide/classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="b5731-391">Visual Studio could not find a [constructor](../../../csharp/programming-guide/classes-and-structs/constructors.md) that had matching parameters.</span></span> <span data-ttu-id="b5731-392">这可能是因为提供的构造函数的类型不是所需的类型。</span><span class="sxs-lookup"><span data-stu-id="b5731-392">This may be the result of supplying a constructor with types other than those that are required.</span></span> <span data-ttu-id="b5731-393">例如，**点**构造函数可能采用两个整数。</span><span class="sxs-lookup"><span data-stu-id="b5731-393">For example, a **Point** constructor might take two integers.</span></span> <span data-ttu-id="b5731-394">如果提供了浮点，则会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-394">If you provided floats, this error is raised.</span></span>

<span data-ttu-id="b5731-395">若要更正此错误，请使用其他构造函数或显式强制转换参数类型，使其与构造函数提供的类型匹配。</span><span class="sxs-lookup"><span data-stu-id="b5731-395">To correct this error, use a different constructor or explicitly cast the parameter types such that they match those provided by the constructor.</span></span>

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a><span data-ttu-id="b5731-396">无法向 \<reference name> 当前应用程序添加引用 ""</span><span class="sxs-lookup"><span data-stu-id="b5731-396">Unable to add reference '\<reference name>' to the current application</span></span>

<span data-ttu-id="b5731-397">错误消息： "无法向 \<reference name> 当前应用程序添加引用" "。</span><span class="sxs-lookup"><span data-stu-id="b5731-397">Error message: "Unable to add reference '\<reference name>' to the current application.</span></span> <span data-ttu-id="b5731-398">请检查是否已引用不同版本的 " \<reference name> "。</span><span class="sxs-lookup"><span data-stu-id="b5731-398">Check that a different version of '\<reference name>' is not already referenced."</span></span>

<span data-ttu-id="b5731-399">Visual Studio 无法添加引用。</span><span class="sxs-lookup"><span data-stu-id="b5731-399">Visual Studio is unable to add a reference.</span></span> <span data-ttu-id="b5731-400">若要更正此错误，请检查是否已引用不同版本的引用。</span><span class="sxs-lookup"><span data-stu-id="b5731-400">To correct this error, check that a different version of the reference is not already referenced.</span></span>

### <a name="unable-to-check-out-the-current-file"></a><span data-ttu-id="b5731-401">无法签出当前文件</span><span class="sxs-lookup"><span data-stu-id="b5731-401">Unable to check out the current file</span></span>

<span data-ttu-id="b5731-402">错误消息： "无法签出当前文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-402">Error message: "Unable to check out the current file.</span></span> <span data-ttu-id="b5731-403">文件可能已被锁定，或者可能需要手动签出文件。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-403">The file may be locked, or you may need to check out the file manually."</span></span>

<span data-ttu-id="b5731-404">如果将当前签入的文件更改为源代码管理，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-404">This error arises when you change a file that's currently checked in to source-code control.</span></span> <span data-ttu-id="b5731-405">通常情况下，Visual Studio 会显示 "文件签出" 对话框，以便用户签出文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-405">Usually, Visual Studio presents the file checkout dialog box so that the user can check out the file.</span></span> <span data-ttu-id="b5731-406">这一次，文件未签出，可能是因为在签出过程中出现合并冲突。</span><span class="sxs-lookup"><span data-stu-id="b5731-406">This time, the file was not checked out, perhaps because of a merge conflict during checkout.</span></span> <span data-ttu-id="b5731-407">若要更正此错误，请确保文件未锁定，然后尝试手动签出文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-407">To correct this error, ensure that the file is not locked, and then try to check out the file manually.</span></span>

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a><span data-ttu-id="b5731-408">找不到名为 " \<Options dialog box tab name> " 的页</span><span class="sxs-lookup"><span data-stu-id="b5731-408">Unable to find page named '\<Options dialog box tab name>'</span></span>

<span data-ttu-id="b5731-409">当组件设计器通过使用不存在的名称从 "选项" 对话框请求对页面的访问权限时，会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-409">This error arises when a component designer requests access to a page from the Options dialog box by using a name that does not exist.</span></span> <span data-ttu-id="b5731-410">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-410">Contact the component vendor.</span></span>

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a><span data-ttu-id="b5731-411">找不到 \<property name> 页面 "" 上的属性 "" \<Options dialog box tab name></span><span class="sxs-lookup"><span data-stu-id="b5731-411">Unable to find property '\<property name>' on page '\<Options dialog box tab name>'</span></span>

<span data-ttu-id="b5731-412">当组件设计器请求从 "选项" 对话框访问页面上的特定值，但该值不存在时，会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="b5731-412">This error arises when a component designer requests access to a particular value on a page from the Options dialog box, but that value does not exist.</span></span> <span data-ttu-id="b5731-413">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-413">Contact the component vendor.</span></span>

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a><span data-ttu-id="b5731-414">该文件内的类不是从可进行可视化设计的类继承，因此 Visual Studio 无法为该文件打开设计器</span><span class="sxs-lookup"><span data-stu-id="b5731-414">Visual Studio cannot open a designer for the file because the class within it does not inherit from a class that can be visually designed</span></span>

<span data-ttu-id="b5731-415">Visual Studio 加载了类，但未能加载该类的设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-415">Visual Studio loaded the class, but the designer for that class could not be loaded.</span></span> <span data-ttu-id="b5731-416">Visual Studio 要求设计器使用文件中的第一个类。</span><span class="sxs-lookup"><span data-stu-id="b5731-416">Visual Studio requires that designers use the first class in a file.</span></span> <span data-ttu-id="b5731-417">若要更正此错误，请移动类代码，使其成为文件中的第一个类，然后再次加载设计器。</span><span class="sxs-lookup"><span data-stu-id="b5731-417">To correct this error, move the class code so that it is the first class in the file, and then load the designer again.</span></span>

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a><span data-ttu-id="b5731-418">Visual Studio 无法保存或加载类型为 "" 的实例 \<type name></span><span class="sxs-lookup"><span data-stu-id="b5731-418">Visual Studio cannot save or load instances of the type '\<type name>'</span></span>

<span data-ttu-id="b5731-419">这是第三方组件的问题。</span><span class="sxs-lookup"><span data-stu-id="b5731-419">This is a problem with a third-party component.</span></span> <span data-ttu-id="b5731-420">请与组件供应商联系。</span><span class="sxs-lookup"><span data-stu-id="b5731-420">Contact the component vendor.</span></span>

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a><span data-ttu-id="b5731-421">Visual Studio 无法 \<document name> 在设计视图中打开 ""</span><span class="sxs-lookup"><span data-stu-id="b5731-421">Visual Studio is unable to open '\<document name>' in Design view</span></span>

<span data-ttu-id="b5731-422">错误消息： "Visual Studio 无法 \<document name> 在设计视图中打开" "。</span><span class="sxs-lookup"><span data-stu-id="b5731-422">Error message: "Visual Studio is unable to open '\<document name>' in Design view.</span></span> <span data-ttu-id="b5731-423">没有为文件类型安装分析器。 "</span><span class="sxs-lookup"><span data-stu-id="b5731-423">No parser is installed for the file type."</span></span>

<span data-ttu-id="b5731-424">此错误表明，项目的语言不支持设计器，当您尝试在 "打开文件" 对话框或解决方案资源管理器中打开文件时，会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="b5731-424">This error indicates that the language of the project does not support a designer and arises when you attempt to open a file in the Open File dialog box or from Solution Explorer.</span></span> <span data-ttu-id="b5731-425">而是在代码视图中编辑该文件。</span><span class="sxs-lookup"><span data-stu-id="b5731-425">Instead, edit the file in Code view.</span></span>

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a><span data-ttu-id="b5731-426">Visual Studio 找不到 "" 类型的类的设计器 \<type name></span><span class="sxs-lookup"><span data-stu-id="b5731-426">Visual Studio was unable to find a designer for classes of type '\<type name>'</span></span>

<span data-ttu-id="b5731-427">Visual Studio 加载了类，但无法设计该类。</span><span class="sxs-lookup"><span data-stu-id="b5731-427">Visual Studio loaded the class, but the class cannot be designed.</span></span> <span data-ttu-id="b5731-428">而是在代码视图中编辑类，方法是右键单击类，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="b5731-428">Instead, edit the class in Code view by right-clicking the class and choosing **View Code**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5731-429">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5731-429">See also</span></span>

- [<span data-ttu-id="b5731-430">使用设计器开发 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="b5731-430">Develop Windows Forms controls using the designer</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="b5731-431">Windows 窗体设计器论坛</span><span class="sxs-lookup"><span data-stu-id="b5731-431">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
