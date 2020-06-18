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
# <a name="windows-forms-designer-error-page"></a>Windows 窗体设计器错误页

如果 Windows 窗体设计器由于代码中的错误、第三方组件或其他位置无法加载，则会看到错误页，而不是设计器。 此错误页不一定表示设计器中的 bug。 Bug 可能位于名为的代码隐藏页中的某个位置 \<your-form-name> 。Designer.cs。 错误显示在可折叠的黄色栏中，其中包含一个链接，可跳转到代码页上错误的位置。

![Windows 窗体设计器错误页](media/windows-forms-designer-error-page-collapsed.png)

您可以选择忽略错误，然后通过单击 "**忽略并继续**" 继续加载设计器。 此操作可能会导致意外的行为，例如，控件可能不会显示在设计图面上。

## <a name="instances-of-this-error"></a>此错误的实例

展开黄色误差线时，将列出该错误的每个实例。 许多错误类型都包含采用以下格式的准确位置： *[项目名称]* *[窗体名称]* 行：*[行号]* 列：*[列号]*。 如果调用堆栈与错误相关联，则可以单击 "**显示调用堆栈**" 链接以查看该错误。 检查调用堆栈可能会进一步帮助您解决此错误。

![Windows 窗体设计器扩展错误](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - 对于 Visual Basic 应用，设计时错误页不会显示多个错误，但它可能会显示同一错误的多个实例。
> - 对于 c + + 应用程序，错误没有代码位置链接。

## <a name="help-with-this-error"></a>有关此错误的帮助

如果有针对错误的帮助主题，请单击**MSDN 帮助**链接，直接转到 docs.microsoft.com 上的帮助页面。

## <a name="forum-posts-about-this-error"></a>有关此错误的论坛帖子

单击 "在**MSDN 论坛中搜索与此错误相关的帖子**" 链接以导航到 Microsoft 开发人员网络论坛。 你可能想要专门搜索[Windows 窗体设计器](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)或[Windows 窗体](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)论坛。

## <a name="design-time-errors"></a>设计时错误

本部分列出了可能会遇到的一些错误。

### <a name="identifier-name-is-not-a-valid-identifier"></a>" \<identifier name> " 不是有效的标识符

此错误表示字段、方法、事件或对象的命名不正确。

### <a name="name-already-exists-in-project-name"></a>"" \<name> 中已存在 " \<project name> "

错误消息： "" \<name> 中已存在 "" \<project name> 。 请输入唯一的名称。 "

你为继承的表单指定了项目中已存在的名称。 若要更正此错误，请为继承的窗体指定一个唯一名称。

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>" \<Toolbox tab name> " 不是工具箱类别

第三方设计器已尝试访问不存在的工具箱中的选项卡。 请与组件供应商联系。

### <a name="a-requested-language-parser-is-not-installed"></a>请求的语言分析器未安装

错误消息： "未安装请求的语言分析器。 语言分析器名称为 " {0} "。

Visual Studio 尝试加载已为文件类型注册但无法加载的设计器。 这很可能是由于安装过程中出现错误引起的。 请与要用于修复的语言的供应商联系。

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>缺少生成和分析源代码所需的服务

这是第三方组件的问题。 请与组件供应商联系。

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>尝试创建 "" 的实例时出现异常 \<object name>

错误消息： "尝试创建" "的实例时出现异常 \<object name> 。 异常为 " \<exception string\> "。

第三方设计器请求 Visual Studio 创建一个对象，但该对象引发了一个错误。 请与组件供应商联系。

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>另一个编辑器 \<document name> 以不兼容模式打开了 ""

错误消息： "另一个编辑器 \<document name> 以不兼容模式打开了 ' '。 请关闭编辑器，然后重试此操作。 "

如果尝试打开已在另一个编辑器中打开的文件，则会出现此错误。 将显示已打开文件的编辑器。 若要更正此错误，请关闭打开该文件的编辑器，然后重试。

### <a name="another-editor-has-made-changes-to-document-name"></a>另一个编辑器已对 "" 进行了更改 \<document name>

关闭并重新打开设计器，以使更改生效。 通常情况下，Visual Studio 会在更改完成后自动重新加载设计器。 但是，其他设计器（如第三方组件设计器）可能不支持重载行为。 在这种情况下，Visual Studio 会提示您手动关闭并重新打开设计器。

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>另一个编辑器以不兼容的模式打开了此文件

错误消息： "另一个编辑器以不兼容模式打开了该文件。 请关闭编辑器，然后重试此操作。 "

此消息类似于 "其他编辑器 \<document name> 在不兼容模式下打开"，但 Visual Studio 无法确定文件名。 若要更正此错误，请关闭打开该文件的编辑器，然后重试。

### <a name="array-rank-rank-in-array-is-too-high"></a>数组排名 " \<rank in array> " 过高

Visual Studio 仅支持由设计器分析的代码块中的单维度数组。 多维数组在此区域外有效。

### <a name="assembly-assembly-name-could-not-be-opened"></a>未能打开程序集 " \<assembly name> "

错误消息：无法打开 "程序集" \<assembly name> 。 验证该文件是否仍然存在。 "

当您尝试打开无法打开的文件时，会出现此错误消息。 请确认该文件存在并且是有效的程序集。

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>错误的元素类型。 此序列化程序需要类型为 " \<type name> " 的元素

这是第三方组件的问题。 请与组件供应商联系。

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>此时无法访问 Visual Studio 工具箱

Visual Studio 调用了 "工具箱"，此操作不可用。 如果看到此错误，请查看此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>无法将事件处理程序绑定到 " \<event name> " 事件，因为它是只读的

如果尝试将事件连接到从基类继承的控件，则会出现此错误。 如果控件的成员变量是私有的，则 Visual Studio 不能将事件连接到方法。 私下继承的控件不能具有绑定到它们的附加事件。

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>请求的组件不是设计容器的成员，因此无法创建该组件的方法名

Visual Studio 尝试将事件处理程序添加到设计器中没有成员变量的组件。 请与组件供应商联系。

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>对象 " \<name> " 已命名为 ""，因此无法命名该对象 \<name>

这是 Visual Studio 序列化程序中的内部错误。 它表示序列化程序尝试将对象命名为两次，这是不受支持的。 如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>无法移除或损坏继承的组件 " \<component name> "

继承的控件受继承类的所有权。 对继承控件的更改必须在控件源自的类中进行。 因此，不能重命名或销毁它。

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>类别 " \<Toolbox tab name> " 没有类 "" 的工具 \<class name>

设计器尝试引用特定 "工具箱" 选项卡上的类，但类不存在。 请与组件供应商联系。

### <a name="class-class-name-has-no-matching-constructor"></a>类 " \<class name> " 没有匹配的构造函数

第三方设计器已要求 Visual Studio 使用构造函数中不存在的特定参数创建对象。 请与组件供应商联系。

### <a name="code-generation-for-property-property-name-failed"></a>属性 "" 的代码生成 \<property name> 失败

这是一个用于错误的泛型包装器。 此消息附带的错误字符串将给出有关错误消息的更多详细信息，并具有指向更具体的帮助主题的链接。 若要更正此错误，请解决附加到此错误的错误消息中指定的错误。

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>组件 " \<component name> " 在其构造函数中未调用 Container. Add （）

这是你刚加载或放置在窗体上的组件中的错误。 它指示组件未将自身添加到其容器控件（无论是另一个控件还是窗体）。 设计器将继续工作，但在运行时组件可能会出现问题。

若要更正此错误，请与组件供应商联系。 或者，如果它是您创建的组件，请 `IContainer.Add` 在组件的构造函数中调用方法。

### <a name="component-name-cannot-be-empty"></a>组件名称不能为空

当你尝试将组件重命名为空值时，会出现此错误。

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>无法访问变量 " \<variable name> "，因为它尚未初始化

出现此错误的原因可能是两个方案。 第三方组件供应商在其分布的控件或组件有问题，或您编写的代码在组件之间具有递归依赖关系。

若要更正此错误，请确保你的代码不具有递归依赖项。 如果没有此类问题，请记录错误消息的确切文本，并与组件供应商联系。

### <a name="could-not-find-type-type-name"></a>未能找到类型 " \<type name> "

错误消息： "找不到类型" \<type name> "。 请确保引用包含此类型的程序集。 如果此类型是开发项目的一部分，请确保已成功生成项目。 "

发生此错误的原因是找不到引用。 请确保引用错误消息中指示的类型，并且还会引用该类型所需的任何程序集。 通常，问题在于解决方案中的某个控件尚未生成。 若要生成，请从 "**生成**" 菜单中选择 "**生成解决方案**"。 否则，如果已经生成了控件，请从解决方案资源管理器中的 "**引用**" 或 "**依赖项**" 文件夹的右键单击菜单手动添加引用。

### <a name="could-not-load-type-type-name"></a>未能加载类型 " \<type name> "

错误消息： "无法加载类型" \<type name> "。 请确保将包含此类型的程序集添加到项目引用中。 "

Visual Studio 尝试连接事件处理方法，但找不到方法的一个或多个参数类型。 这通常是由于缺少引用引起的。 若要更正此错误，请将包含该类型的引用添加到该项目，然后重试。

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>未能找到继承的组件的项目项模板

Visual Studio 中的继承窗体的模板不可用。 如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>委托类 " \<class name> " 没有 invoke 方法。 此类是否为委托？

Visual Studio 已尝试创建事件处理程序，但事件类型出现错误。 如果事件是由不符合 CLS 的语言创建的，则可能会发生这种情况。 请与组件供应商联系。

### <a name="duplicate-declaration-of-member-member-name"></a>成员 "" 的重复声明 \<member name>

出现此错误的原因是成员变量已被声明了两次（例如， `Button1` 在代码中声明了两个名为的控件）。 名称在继承的窗体中必须是唯一的。 此外，名称不能仅区分大小写。

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>从区域性 "" 的资源文件中读取资源时出错 \<culture name>

如果项目中存在错误的 .resx 文件，则会发生此错误。

若要更正该错误，请执行以下操作：

1. 单击解决方案资源管理器中的 "**显示所有文件**" 按钮，查看与该解决方案相关联的 .resx 文件。
2. 右键单击 .resx 文件，然后选择 "**打开**"，在 XML 编辑器中加载 .resx 文件。
3. 手动编辑 .resx 文件以解决错误。

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>从默认区域性 "" 的资源文件中读取资源时出错 \<culture name>

如果默认区域性的项目中有无效的 .resx 文件，则会发生此错误。

若要更正该错误，请执行以下操作：

1. 单击解决方案资源管理器中的 "**显示所有文件**" 按钮，查看与该解决方案相关联的 .resx 文件。
2. 右键单击 .resx 文件，然后选择 "**打开**"，在 XML 编辑器中加载 .resx 文件。
3. 手动编辑 .resx 文件以解决错误。

### <a name="failed-to-parse-method-method-name"></a>未能分析方法 " \<method name> "

错误消息： "无法分析方法" \<method name> "。 分析器报告以下错误： " \<error string> "。 请查看任务列表是否有可能的错误。 "

这是分析过程中出现的问题的常规错误消息。 这些错误通常是由语法错误引起的。 请参阅与错误相关的特定消息的任务列表。

### <a name="invalid-component-name-component-name"></a>无效的组件名称： " \<component name> "

您尝试将组件重命名为该语言的无效值。 若要更正此错误，请为组件命名，使其符合该语言的命名规则。

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>类型 " \<class name> " 由同一文件中的几个分部类组成

使用[partial](../../../csharp/language-reference/keywords/partial-type.md)关键字在多个文件中定义类时，每个文件中只能有一个部分定义。

若要更正此错误，请从文件中删除类的所有分部定义之外的所有部分定义。

### <a name="the-assembly-assembly-name-could-not-be-found"></a>未能找到程序集 " \<assembly name> "

错误消息： "找不到程序集" \<assembly name> "。 确保引用该程序集。 如果程序集是当前开发项目的一部分，请确保已生成项目。 "

此错误类似于 "找不到类型" \<type name> ，但此错误通常是由于元数据属性造成的。 若要更正此错误，请检查是否引用了属性使用的所有程序集。

### <a name="the-assembly-name-assembly-name-is-invalid"></a>程序集名称 " \<assembly name> " 无效

组件已请求特定程序集，但组件提供的名称不是有效的程序集名称。 请与组件供应商联系。

### <a name="the-base-class-class-name-cannot-be-designed"></a>无法设计基类 " \<class name> "

Visual Studio 加载了类，但无法设计该类，因为该类的实施者未提供设计器。 如果类支持设计器，请确保没有任何问题导致在设计器中显示它（例如编译器错误）时出现问题。 另外，请确保对类的所有引用都是正确的，并且所有类名的拼写正确。 否则，如果类不是可设计的，请在代码视图中对其进行编辑。

### <a name="the-base-class-class-name-could-not-be-loaded"></a>无法加载基类 " \<class name> "

项目中未引用类，因此 Visual Studio 无法加载它。 若要更正此错误，请在项目中添加对类的引用，然后关闭并重新打开 Windows 窗体设计器窗口。

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>类 " \<class name> " 不能在此版本的 Visual Studio 中设计

此控件或组件的设计器不支持 Visual Studio 所用的相同类型。 请与组件供应商联系。

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>该类名不是此语言的有效标识符

用户创建的源代码的类名称对所使用的语言无效。 若要更正此错误，请将类命名为符合语言要求。

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>无法添加该组件，因为它包含对 "" 的循环引用 \<reference name>

不能将控件或组件添加到其自身。 如果出现这种情况，则可能会发生这种情况：在 InitializeComponent 方法中，有一个创建另一个 Form1 实例的窗体的代码。

### <a name="the-designer-cannot-be-modified-at-this-time"></a>此时无法修改设计器

当编辑器中的文件标记为只读时，会发生此错误。 确保该文件未标记为只读并且应用程序未运行。

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>文件中的类都不能进行设计，因此未能为该文件显示设计器

当 Visual Studio 找不到满足设计器要求的基类时，将发生此错误。 窗体和控件必须派生自支持设计器的基类。 如果要从继承的窗体或控件派生，请确保已生成项目。

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>未安装基类 "" 的设计器 \<class name>

Visual Studio 无法加载类的设计器。 如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>设计器必须创建类型为 "" 的实例 \<type name> ，但由于该类型已声明为抽象类型，因此无法创建该类型的实例

发生此错误的原因是，传递到设计器的对象的基类是[抽象](../../../csharp/language-reference/keywords/abstract.md)的，这是不允许的。

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>未能在设计器中加载该文件

此文件的基类不支持任何设计器。 作为一种解决方法，使用代码视图处理该文件。 在解决方案资源管理器中右键单击该文件，然后选择 "**查看代码**"。

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>该文件的语言不支持必需的代码分析和生成服务

错误消息： "此文件的语言不支持必要的代码分析和生成服务。 请确保正在打开的文件是项目的成员，然后再次尝试打开该文件。 "

此错误最有可能是由于打开的项目中的文件不支持设计器而导致的。

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>语言分析器类 " \<class name> " 未正确实现

错误消息： "语言分析器类" \<class name> "未正确实现。 请与供应商联系以获取更新的分析器模块。 "

所使用的语言已注册了一个不是从正确的基类派生的设计器类。 联系你使用的语言的供应商。

### <a name="the-name-name-is-already-used-by-another-object"></a>名称 " \<name> " 已由另一个对象使用

这是 Visual Studio 序列化程序中的内部错误。 如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>对象 " \<object name> " 未实现 IComponent 接口

Visual Studio 尝试创建组件，但所创建的对象未实现 <xref:System.ComponentModel.IComponent> 接口。 请与组件供应商联系以获取修补程序。

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>对象 " \<object name> " 为属性 "" 返回了 null， \<property name> 但这是不允许的

有一些应始终返回对象的 .NET 属性。 例如，窗体的**控件**集合应始终返回对象，即使其中没有任何控件也是如此。

若要更正此错误，请确保错误中指定的属性不为 null。

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>序列化数据对象的类型不正确

序列化程序提供的数据对象不是与当前正在使用的序列化程序匹配的类型的实例。 请与组件供应商联系。

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>服务 " \<service name> " 是必需的，但未能找到

错误消息： "服务" \<service name> "是必需的，但找不到。 Visual Studio 安装可能有问题。 "

Visual Studio 所需的服务不可用。 如果尝试加载的项目不支持该设计器，请使用代码编辑器进行所需的更改。 否则，如果看到此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>服务实例必须派生自或实现 " \<interface name> "

此错误表示组件或组件设计器调用了**AddService**方法，该方法需要接口和对象，但指定的对象未实现指定的接口。 请与组件供应商联系。

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>未能修改代码窗口中的文本

错误消息： "无法修改代码窗口中的文本。 请检查该文件是否不是只读的，以及是否有足够的磁盘空间。 "

由于磁盘空间或内存问题导致 Visual Studio 无法编辑文件，或者文件被标记为只读时，会出现此错误。

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>工具箱枚举数对象仅支持一次检索一个项

如果看到此错误，请查看此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>\<component name>无法从工具箱检索 "" 的工具箱项

错误消息： " \<component name> 无法从工具箱检索" "的工具箱项。 请确保正确安装了包含工具箱项的程序集。 工具箱项引发了以下错误： \<error string> 。 "

当 Visual Studio 对其进行访问时，有问题的组件引发异常。 请与组件供应商联系。

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>\<Toolbox item name>无法从工具箱检索 "" 的工具箱项

错误消息： " \<Toolbox item name> 无法从工具箱检索" "的工具箱项。 请尝试删除 "工具箱" 中的项并将其添加回去。

如果工具箱项中的数据损坏或组件的版本发生了更改，则会发生此错误。 尝试从工具箱中移除该项，然后重新添加。

### <a name="the-type-type-name-could-not-be-found"></a>\<type name>未能找到类型 ""

错误消息： "找不到类型" \<type name> "。 确保引用包含该类型的程序集。 如果程序集是当前开发项目的一部分，请确保已生成项目。 "

加载设计器时，Visual Studio 找不到类型。 确保引用包含该类型的程序集。 如果程序集是当前开发项目的一部分，请确保已生成项目。

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>只能从主应用程序线程调用类型解析服务

Visual Studio 尝试从错误的线程访问所需资源。 当用于创建设计器的代码从主应用程序线程以外的线程调用类型解析服务时，将显示此错误。 若要更正此错误，请从正确的线程调用服务，或与组件供应商联系。

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>变量 " \<variable name> " 未声明或从未赋值

源代码引用了对变量的引用，例如**Button1**，未声明或赋值。 如果尚未分配该变量，则此消息将显示为警告而不是错误。

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>菜单命令 "" 已经有一个命令处理程序 \<menu command name>

如果第三方设计器将已有处理程序的命令添加到命令表，则会出现此错误。 请与组件供应商联系。

### <a name="there-is-already-a-component-named-component-name"></a>已存在名为 "" 的组件 \<component name>

错误消息： "已存在名为" "的组件 \<component name> 。 组件必须具有唯一的名称，并且名称必须不区分大小写。 名称也不能与继承类中任何组件的名称冲突。 "

如果在属性窗口中更改了组件的名称，则会出现此错误消息。 若要更正此错误，请确保所有组件名称都是唯一的，不区分大小写，并且不会与继承的类中任何组件的名称冲突。

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>已为 "" 格式注册工具箱项创建者 \<format name>

第三方组件对 "工具箱" 选项卡上的项进行了回调，但该项已经包含了一个回调。 请与组件供应商联系。

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>此语言引擎不支持用于加载设计器的 CodeModel

此消息类似于 "此文件的语言不支持必要的代码分析和生成服务"，但此消息涉及内部注册问题。 如果看到此错误，请查看此错误，请使用[报告问题](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)记录问题。

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>类型 " \<type name\> " 没有具有类型为 "" 的参数的构造函数 \<parameter type names>

Visual Studio 找不到具有匹配参数的[构造函数](../../../csharp/programming-guide/classes-and-structs/constructors.md)。 这可能是因为提供的构造函数的类型不是所需的类型。 例如，**点**构造函数可能采用两个整数。 如果提供了浮点，则会引发此错误。

若要更正此错误，请使用其他构造函数或显式强制转换参数类型，使其与构造函数提供的类型匹配。

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>无法向 \<reference name> 当前应用程序添加引用 ""

错误消息： "无法向 \<reference name> 当前应用程序添加引用" "。 请检查是否已引用不同版本的 " \<reference name> "。

Visual Studio 无法添加引用。 若要更正此错误，请检查是否已引用不同版本的引用。

### <a name="unable-to-check-out-the-current-file"></a>无法签出当前文件

错误消息： "无法签出当前文件。 文件可能已被锁定，或者可能需要手动签出文件。 "

如果将当前签入的文件更改为源代码管理，则会出现此错误。 通常情况下，Visual Studio 会显示 "文件签出" 对话框，以便用户签出文件。 这一次，文件未签出，可能是因为在签出过程中出现合并冲突。 若要更正此错误，请确保文件未锁定，然后尝试手动签出文件。

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>找不到名为 " \<Options dialog box tab name> " 的页

当组件设计器通过使用不存在的名称从 "选项" 对话框请求对页面的访问权限时，会出现此错误。 请与组件供应商联系。

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>找不到 \<property name> 页面 "" 上的属性 "" \<Options dialog box tab name>

当组件设计器请求从 "选项" 对话框访问页面上的特定值，但该值不存在时，会出现此错误。 请与组件供应商联系。

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>该文件内的类不是从可进行可视化设计的类继承，因此 Visual Studio 无法为该文件打开设计器

Visual Studio 加载了类，但未能加载该类的设计器。 Visual Studio 要求设计器使用文件中的第一个类。 若要更正此错误，请移动类代码，使其成为文件中的第一个类，然后再次加载设计器。

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>Visual Studio 无法保存或加载类型为 "" 的实例 \<type name>

这是第三方组件的问题。 请与组件供应商联系。

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>Visual Studio 无法 \<document name> 在设计视图中打开 ""

错误消息： "Visual Studio 无法 \<document name> 在设计视图中打开" "。 没有为文件类型安装分析器。 "

此错误表明，项目的语言不支持设计器，当您尝试在 "打开文件" 对话框或解决方案资源管理器中打开文件时，会发生这种情况。 而是在代码视图中编辑该文件。

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>Visual Studio 找不到 "" 类型的类的设计器 \<type name>

Visual Studio 加载了类，但无法设计该类。 而是在代码视图中编辑类，方法是右键单击类，然后选择 "**查看代码**"。

## <a name="see-also"></a>另请参阅

- [使用设计器开发 Windows 窗体控件](developing-windows-forms-controls-at-design-time.md)
- [Windows 窗体设计器论坛](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
