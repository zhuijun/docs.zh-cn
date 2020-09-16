---
title: XAML 服务
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 313cb46813d8c0cfa9f1f317a65d2e21298ecff9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552850"
---
# <a name="xaml-services"></a>XAML 服务

本主题介绍 .NET XAML 服务技术集的功能。 其中所述的大部分服务和 API 位于程序集 `System.Xaml` 中。 这些服务包括读取器和编写器、架构类和架构支持、工厂、类的特性化、XAML 语言内部支持以及其他 XAML 语言功能。

## <a name="about-this-documentation"></a>关于本文档

.NET XAML 服务的概念文档假定你之前接触过 XAML 语言，并了解如何将它应用到特定框架（例如 Windows Presentation Foundation (WPF) 或 Windows Workflow Foundation），或者了解特定的技术功能领域，例如 <xref:Microsoft.Build.Framework.XamlTypes> 中的生成自定义项功能。 本文档不会尝试解释作为标记语言的 XAML 的基础知识、XAML 语法术语或其他介绍性材料。 相反，本文档重点介绍如何使用 System.Xaml 程序集库中启用的 .NET XAML 服务。 其中大多数 API 适用于 XAML 语言集成和扩展性场景。 这可能包括以下任何场景：

- 扩展基础 XAML 读取器或 XAML 编写器的功能（直接处理 XAML 节点流；派生自己的 XAML 读取器或 XAML 编写器）。

- 定义不具有特定框架依赖项的 XAML 可用的自定义类型，并对这些类型进行特性化，以将其 XAML 类型系统特征传递给 .NET XAML 服务。

- 将 XAML 读取器或 XAML 编写器托管为应用程序的组件，例如适用于 XAML 标记源的可视化设计器或交互式编辑器。

- 编写 XAML 值转换器（标记扩展、自定义类型的类型转换器）。

- 定义自定义 XAML 架构上下文（对后备类型源使用替代程序集加载技术；使用已知类型查找技术而不是总是反映程序集；使用加载的程序集概念，这些概念不使用公共语言运行时 (CLR) `AppDomain` 及其关联的安全模型）。

- 扩展基础 XAML 类型系统。

- 使用 `Lookup` 或 `Invoker` 技术来影响 XAML 类型系统和类型后备的评估方式。

如果你需要 XAML 语言的介绍性材料，可以查看 [XAML 概述 (WPF)](../fundamentals/xaml.md)。 该主题面向不熟悉 Windows Presentation Foundation (WPF) 和不知道如何使用 XAML 标记及 XAML 语言功能的受众介绍 XAML。 另一个有用的文档是 [XAML 语言规范](/previous-versions/msp-n-p/ff650760(v=pandp.10))中的介绍性材料。

## <a name="net-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET 体系结构中的 .NET XAML 服务和 `System.Xaml`

.NET XAML 服务和 `System.Xaml` 程序集定义了支持 XAML 语言功能所需的大部分内容。 其中一项便是 XAML 读取器和 XAML 编写器的基类。 添加到 .NET XAML 服务中的最重要功能（以前特定于该框架的任何 XAML 实现中均不存在）是 XAML 的类型系统表示形式。 此类型系统表示形式以面向对象的方式表示 XAML，它以 XAML 功能为中心，而不依赖于框架的特定功能。

XAML 类型系统既不受 XAML 源的标记形式或运行时细节的限制，也不受任何特定后备类型系统的限制。 XAML 类型系统包括类型、成员、XAML 架构上下文、XML 级别概念和其他 XAML 语言概念或 XAML 内部函数的对象表示形式。 使用或扩展 XAML 类型系统可以从 XAML 读取器和 XAML 编写器等类实现派生，并可将 XAML 表示形式的功能扩展为受框架、技术或使用或发出 XAML 的应用程序支持的特定功能。 XAML 架构上下文的概念支持从 XAML 对象编写器实现、通过上下文中程序集信息传达的技术后备类型系统和 XAML 节点源的组合来实现实际的对象图写入操作。 若要详细了解 XAML 架构概念， 请参阅[默认 XAML 架构上下文和 WPF XAML 架构上下文](default-schema-context.md)。

## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML 节点流、XAML 读取器和 XAML 编写器

要了解 .NET XAML 服务在 XAML 语言和使用 XAML 作为语言的特定技术之间的关系中扮演着何种角色，首先了解 XAML 节点流概念以及该概念如何影响 API 和术语会很有帮助。 XAML 节点流是 XAML 语言表示形式与 XAML 表示或定义的对象图之间的概念中间产物。

- XAML 读取器是一个以某种形式处理 XAML 的实体，会生成 XAML 节点流。 在 API 中，XAML 读取器由基类 <xref:System.Xaml.XamlReader> 表示。

- XAML 编写器是一个处理 XAML 节点流并生成其他内容的实体。 在 API 中，XAML 编写器由基类 <xref:System.Xaml.XamlWriter> 表示。

  涉及 XAML 的最常见情况有两种：加载 XAML 来实例化对象图，以及保存来自应用程序或工具的对象图并生成 XAML 表示形式（通常以标记形式保存为文本文件）。 在本文档中，加载 XAML 和创建对象图通常称为加载路径。 在本文档中，保存现有对象图或将其序列化为 XAML 通常称为保存路径。

  最常见的加载路径类型如下所示：

- 以采用 UTF 编码的 XML 格式开始使用 XAML 表示形式，并保存为文本文件。

- 将该 XAML 加载到 <xref:System.Xaml.XamlXmlReader> 中。 <xref:System.Xaml.XamlXmlReader> 是一个 <xref:System.Xaml.XamlReader> 子类。

- 结果是一个 XAML 节点流。 可以使用 <xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> API 访问此 XAML 节点流中的各个节点。 此时最典型的操作是前进至 XAML 节点流，使用“当前记录”工具处理各个节点。

- 将 XAML 节点流中生成的节点传递到 <xref:System.Xaml.XamlObjectWriter> API。 <xref:System.Xaml.XamlObjectWriter> 是一个 <xref:System.Xaml.XamlWriter> 子类。

- <xref:System.Xaml.XamlObjectWriter> 根据源 XAML 节点流中的进度编写对象图（一次一个对象）。 对象编写是通过 XAML 架构上下文和可访问后备类型系统和框架的程序集和类型的实现来完成的。

- 在 XAML 节点流的末尾调用 <xref:System.Xaml.XamlObjectWriter.Result%2A> 来获取对象图的根对象。

  保存路径的最常见类型如下所述：

- 以整个应用程序运行时的对象图、运行时的 UI 内容和状态，或整体应用程序在运行时的对象表示形式的一小部分开始。

- 从逻辑起始对象（例如应用程序或文档根目录）中，将对象加载到 <xref:System.Xaml.XamlObjectReader>。 <xref:System.Xaml.XamlObjectReader> 是一个 <xref:System.Xaml.XamlReader> 子类。

- 结果是一个 XAML 节点流。 可以使用 <xref:System.Xaml.XamlObjectReader> 和 <xref:System.Xaml.XamlReader> API 访问此 XAML 节点流中的各个节点。 此时最典型的操作是前进至 XAML 节点流，使用“当前记录”工具处理各个节点。

- 将 XAML 节点流中生成的节点传递到 <xref:System.Xaml.XamlXmlWriter> API。 <xref:System.Xaml.XamlXmlWriter> 是一个 <xref:System.Xaml.XamlWriter> 子类。

- <xref:System.Xaml.XamlXmlWriter> 采用 XML UTF 编码编写 XAML。 可以将其保存为文本文件、流或其他形式。

- 调用 <xref:System.Xaml.XamlXmlWriter.Flush%2A> 以获取最终输出。

若要详细了解 XAML 节点流概念，请参阅[了解 XAML 节点流结构和概念](understanding-xaml-node-stream-structures-and-concepts.md)。

### <a name="the-xamlservices-class"></a>XamlServices 类

并非始终需要处理 XAML 节点流。 如果需要基础的加载路径或基础的保存路径，可以使用 <xref:System.Xaml.XamlServices> 类中的 API。

- <xref:System.Xaml.XamlServices.Load%2A> 的各种签名实现了一个加载路径。 你可以加载文件或流，或者可以加载 <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader> 或 <xref:System.Xaml.XamlReader>，它们通过使用读取器的 API 进行加载来包装你的 XAML 输入。

- <xref:System.Xaml.XamlServices.Save%2A> 的各种签名保存对象图并生成流、文件或 <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> 实例形式的输出。

- <xref:System.Xaml.XamlServices.Transform%2A> 通过将一个加载路径和一个保存路径链接为单个操作来转换 XAML。 可以将不同的架构上下文或不同的后备类型系统用于 <xref:System.Xaml.XamlReader> 和 <xref:System.Xaml.XamlWriter>，这会影响生成的 XAML 的转换方式。

有关如何使用 <xref:System.Xaml.XamlServices> 的详细信息，请参阅 [XAMLServices 类和基本的 XAML 读取或写入](basic-reading-writing.md)。

## <a name="xaml-type-system"></a>XAML 类型系统

XAML 类型系统提供了处理 XAML 节点流的特定单个节点所需的 API。

<xref:System.Xaml.XamlType> 是对象的表示形式（开始对象节点和结束对象节点之间的处理内容）。

<xref:System.Xaml.XamlMember> 是对象成员的表示形式（开始成员节点和结束成员节点之间的处理内容）。

<xref:System.Xaml.XamlType.GetAllMembers%2A>、<xref:System.Xaml.XamlType.GetMember%2A> 和 <xref:System.Xaml.XamlMember.DeclaringType%2A> 等 API 报告 <xref:System.Xaml.XamlType> 和 <xref:System.Xaml.XamlMember> 之间的关系。

由 .NET XAML 服务实现的 XAML 类型系统的默认行为基于公共语言运行时 (CLR) 以及使用反射对程序集中 CLR 类型进行的静态分析。 因此，对于特定的 CLR 类型，XAML 类型系统的默认实现可以公开该类型及其成员的 XAML 架构，并根据 XAML 类型系统对其进行报告。 在默认的 XAML 类型系统中，类型转让概念映射到 CLR 继承上，实例、值类型等概念也映射到 CLR 的支持行为和功能上。

## <a name="reference-for-xaml-language-features"></a>XAML 语言功能参考

为支持 XAML，.NET XAML 服务提供了为 XAML 语言 XAML 命名空间定义的 XAML 语言概念的具体实现。 它们记录在特定的参考页中。 介绍语言功能的角度是这些语言功能在由 .NET XAML 服务定义的 XAML 读取器或 XAML 编写器处理时产生的行为方式。 有关详细信息，请参阅 [XAML 命名空间 (x:)语言功能](namespace-language-features.md)。
