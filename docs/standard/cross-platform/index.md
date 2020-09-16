---
title: 使用 .NET Framework 针对多个平台开发
ms.date: 07/18/2018
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
ms.openlocfilehash: 770944f69abe2b6d4dcfd7baffcc282dbfb41274
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547592"
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>使用 .NET Framework 针对多个平台开发

可以通过使用 .NET Framework 和 Visual Studio 开发 Microsoft 和非 Microsoft 平台上的应用。
  
## <a name="options-for-cross-platform-development"></a>跨平台开发的选项

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 若要针对多个平台进行开发，你可以共享源代码或二进制文件，并可以在 .NET Framework 代码和 Windows 运行时 API 之间进行调用。  
  
|若希望...|使用...|  
|-----------------------|------------|  
|在 Windows Phone 8.1 和 Windows 8.1 应用之间共享源代码|**共享项目** (Visual Studio 2013，Update 2) 中的通用应用模板。<br /><br /> -当前无 Visual Basic 支持。<br />-可以使用 # 语句将特定于平台的代码分隔开来 `if` 。<br /><br /> 有关详细信息，请参阅：<br /><br /> -   [开始编码](/windows/uwp/get-started/create-uwp-apps)<br />-   [使用 Visual Studio 生成通用 XAML 应用](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/) (博客文章) <br />-   [使用 Visual Studio 生成 XAML 聚合应用](https://channel9.msdn.com/Events/Build/2014/3-591) (视频) |  
|在面向不同平台的应用之间共享二进制文件|与平台无关的代码的**可移植类库项目**。<br /><br /> -此方法通常用于实现业务逻辑的代码。<br />-可以使用 Visual Basic 或 c #。<br />-API 支持因平台而异。<br />-面向 Windows 8.1 和 Windows Phone 8.1 支持 Windows 运行时 Api 和 XAML）的可移植类库项目。 这些功能在较旧版本的可移植类库中不可用。<br />-如果需要，你可以通过使用接口或抽象类来抽象出平台特定的代码。<br /><br /> 有关详细信息，请参阅：<br /><br /> -   [可移植类库](cross-platform-development-with-the-portable-class-library.md)<br />-   [如何使可移植类库适用于你](/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you) (博客文章) <br />-   [将可移植类库与 MVVM 配合使用](using-portable-class-library-with-model-view-view-model.md) <br />-   [面向多个平台的库的应用资源](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.Net 可移植性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (Visual Studio 扩展) |  
|在平台（Windows8.1 和 Windows Phone 8.1 除外）的应用之间共享源代码|**添加为链接** 功能。<br /><br /> -此方法适用于这两种应用程序的通用应用程序逻辑，但出于某种原因，此方法是不可移植的。 你可以将此功能用于 C＃ 或 Visual Basic 代码。<br />     例如，Windows Phone 8 和 Windows 8 共享 Windows 运行时 API，但可移植类库不支持这些平台的 Windows 运行时。 你可以使用 `Add as link` 在 Windows Phone 8 应用和面向 Windows 8 的 Windows 应用商店应用之间共享公共 Windows 运行时代码。<br /><br /> 有关详细信息，请参阅：<br /><br /> -   [通过 "添加为" 链接共享代码](/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [如何：向项目中添加现有项](/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|  
|使用 .NET Framework 代码或从 NET Framework 代码调用 Windows 运行时 API，编写 Windows 应用商店应用|从 .NET Framework c # 或 Visual Basic 代码**Windows 运行时 api** ，并使用 .NET Framework 来创建 Windows 应用商店应用。 你应该注意这两个平台的 API 差异。 但是，存在帮助你处理这些差异的类。<br /><br /> 有关详细信息，请参阅：<br /><br /> -   [Windows 应用商店应用和 Windows 运行时 .NET Framework 支持](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [将 URI 传递到 Windows 运行时](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|  
|构建面向非 Microsoft 平台的 .NET Framework 应用|**可移植类库引用** .NET Framework 中的程序集，以及 Visual Studio 扩展或 Xamarin 等第三方工具。<br /><br /> 有关详细信息，请参阅：<br /><br /> -   [可移植类库现在在所有平台上都可用。](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) （博客文章）<br />-   [Xamarin 文档](/xamarin)|  
|将 JavaScript 和 HTML 用于跨平台开发|Visual Studio 2013、Update 2 中的**通用应用模板**，可针对 Windows 8.1 和 Windows Phone 8.1 Windows 运行时 api 进行开发。 当前，你不能将 .NET Framework API 与 JavaScript 和 HTML 结合使用来开发跨平台应用。<br /><br /> 有关详细信息，请参阅：<br /><br /> -   [JavaScript 项目模板](/previous-versions/windows/apps/hh758331(v=win.10))<br />-   [使用 JavaScript 将 Windows 运行时应用迁移到 Windows Phone](/previous-versions/windows/apps/dn636144(v=win.10))|
