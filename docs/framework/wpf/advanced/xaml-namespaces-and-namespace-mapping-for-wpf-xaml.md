---
title: XAML 命名空间和命名空间映射
description: 详细了解两个 XAML 命名空间映射的存在和用途（通常位于 Windows Presentation Foundation XAML 文件的根标记中）。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
ms.openlocfilehash: 42808df8e7483f60b1420fda890fe374493538f1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168373"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>WPF XAML 的 XAML 命名空间和命名空间映射
本主题进一步解释通常在 WPF XAML 文件的根标记中出现的两个 XAML 命名空间映射的存在性和用途。 此外，还介绍如何生成相似映射以使用代码中和/或单独程序集内定义的元素。  

## <a name="what-is-a-xaml-namespace"></a>什么是 XAML 命名空间？  
 XAML 命名空间实际上是 XML 命名空间概念的扩展。 指定 XAML 命名空间的方法依赖于 XML 命名空间语法、将 URI 用作命名空间标识符以及使用前缀提供从相同标记源引用多个命名空间等约定。 XML 命名空间的 XAML 定义增添的主要概念是，XAML 命名空间表示标记用法唯一性范围，还影响标记实体可如何受特定 CLR 命名空间和引用程序集支持。 后者也会受 XAML 架构上下文概念影响。 但是出于 WPF 如何处理 XAML 命名空间的目的，对于默认 XAML 命名空间、XAML 语言命名空间以及任何其他由 XAML 标记直接映射到特定支持 CLR 命名空间和引用程序集的 XAML 命名空间，可通常考虑为 XAML 命名空间。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF 和 XAML 命名空间声明  
 在许多 XAML 文件的根标记中的命名空间声明内，通常可看到两个 XML 命名空间声明。 第一个声明默认映射整个 WPF 客户端/框架 XAML 命名空间：  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 第二个声明映射单独的 XAML 命名空间，（通常）将其映射到 `x:` 前缀。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 这些声明之间的关系是 `x:` 前缀映射支持 XAML 语言定义中的内部函数，并且 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是将 XAML 用作语言并为 XAML 定义对象词汇的一种实现。 因为 WPF 词汇用法远比 XAML 内部函数用法常见，因此默认映射 WPF 词汇。  
  
 `x:`映射 XAML 语言内部函数支持的前缀约定后跟项目模板、示例代码和此 SDK 中的语言功能文档。 XAML 命名空间定义许多常用功能，即使对于基本 WPF 应用程序而言，这些功能也是必需的。 例如，若要通过分部类将任何代码隐藏加入到 XAML 文件，必须将该类命名为相关 XAML 文件根元素中的 `x:Class` 属性。 或者，XAML 页面中定义的任何要作为键控资源访问的元素都应在当前元素上设置 `x:Key` 属性。 有关 XAML 的这些方面和其他方面的详细信息，请参阅 [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md) 或 [XAML 语法详述](xaml-syntax-in-detail.md)。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>映射到自定义类和程序集  
 在 `xmlns` 前缀声明内使用一系列标记可将 XML 命名空间映射到程序集，方法类似于将标准 WPF 和 XAML 内部函数 XAML 命名空间映射到前缀。  
  
 此语法采用以下可能的已命名标记和以下值：  
  
 `clr-namespace:` 在程序集中声明的 CLR 命名空间，此程序集包含要作为元素公开的公共类型。  
  
 `assembly=`包含部分或全部引用的 CLR 命名空间的程序集。 此值通常为程序集的名称而不是路径，且不包含扩展名（例如 .dll 或 .exe）。 程序集路径必须创建为包含要映射的 XAML 的项目文件中的项目引用。 为了并入版本控制和强名称签名， `assembly` 该值可以是由定义的字符串 <xref:System.Reflection.AssemblyName> ，而不是简单的字符串名称。  
  
 请注意，分隔 `clr-namespace` 标记和其值的字符是冒号 (:)，而分隔 `assembly` 标记和其值的字符为等号 (=)。 这两个标记之间应使用的字符是分号。 此外，不要在声明中的任何位置包含任何空白。  
  
### <a name="a-basic-custom-mapping-example"></a>基本自定义映射示例  
 如下代码定义一个示例自定义类：  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 此自定义类随后编译到库，库按项目设置（未显示）命名为 `SDKSampleLibrary`。  
  
 为引用此自定义类，还需将其添加为当前项目的引用（通常可使用 Visual Studio 中的解决方案资源管理器 UI 完成此操作）。  
  
 具有包含类的库并在项目设置中对其进行引用后，可将如下前缀映射到 XAML 中的根元素中：  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 综合而言，以下为根标记中包含自定义映射、典型默认值和 x: 映射的 XAML，然后使用前缀引用实例化此 UI 中的 `ExampleClass`：  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>映射到当前程序集  
 如果要在与引用自定义类的应用程序代码相同的程序集内定义引用的 `clr-namespace`，则可省略 `assembly`。 或者，这种情况的等效语法是指定 `assembly=` 且等号后不含任何字符串标记。  
  
 如果在同一程序集中定义，则自定义类无法用作页面的根元素。 分部类无需映射；仅需映射应用程序中不是页面分部类的类（若要将其引用为 XAML 中的元素）。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>将 CLR 命名空间映射到程序集中的 XML 命名空间  
 WPF 定义 XAML 处理器使用的 CLR 属性，以便将多个 CLR 命名空间映射到单个 XAML 命名空间。 此属性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 将放置在生成程序集的源代码的程序集级别上。 WPF 程序集源代码使用此特性将各种公共命名空间（如 <xref:System.Windows> 和 <xref:System.Windows.Controls> ）映射到 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 命名空间。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>采用两个参数： XML/XAML 命名空间名称和 CLR 命名空间名称。 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以有多个 CLR 命名空间，以便将多个 CLR 命名空间映射到同一个 XML 命名空间。 映射后，通过在分部类代码隐藏页中提供相应 `using` 语句，可在无完全限定的情况下引用这些命名空间的成员（如果需要）。 如需了解详情，请访问 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>。  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>设计器命名空间和 XAML 模板中的其他前缀  
 如果使用 WPF XAML 的开发环境和/或设计工具，你可能会注意到 XAML 标记内存在其他定义的 XAML 命名空间/前缀。  
  
 适用于 Visual Studio 的 WPF 设计器使用通常映射到前缀的设计器命名空间 `d:` 。 适用于 WPF 的更高的项目模板可以预映射此 XAML 命名空间，以支持 WPF 设计器与 Visual Studio 和其他设计环境之间的 XAML 交换。 此设计 XAML 命名空间用于在设计器中往返基于 XAML 的 UI 时保持设计状态。 它也用于 `d:IsDataSource`（在设计器中启用运行时数据源）等功能。  
  
 可能看到的另一个映射前缀是 `mc:`。 `mc:` 用于标记兼容，使用一种并不一定特定于 XAML 的标记兼容模式。 某种程度上，标记兼容功能可用于在框架之间或跨后备实现的其他边界交换 XAML、在 XAML 架构上下文之间运行、为设计器中限制模式提供兼容性等。 有关标记兼容概念及其与 WPF 的关系的详细信息，请参阅[标记兼容 (mc:) 语言功能](markup-compatibility-mc-language-features.md)。  
  
## <a name="wpf-and-assembly-loading"></a>WPF 和程序集加载  
 WPF 的 XAML 架构上下文与 WPF 应用程序模型集成，后者又使用的 CLR 定义的概念 <xref:System.AppDomain> 。 下面的序列说明 XAML 架构上下文如何解释如何在运行时或设计时加载程序集或查找类型，具体取决于 WPF 使用 <xref:System.AppDomain> 和其他因素。  
  
1. 循环访问 <xref:System.AppDomain> ，查找与名称的所有方面匹配的已加载程序集（从最新加载的程序集开始）。  
  
2. 如果名称是限定的，则对 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> 限定名称调用。  
  
3. 如果限定名称的短名称和公钥标记匹配从中加载标记的程序集，则返回此程序集。  
  
4. 使用短名称 + 公钥标记调用 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> 。  
  
5. 如果名称不合格，请调用 <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> 。  
  
 宽松型 XAML 不使用步骤 3；不存在从中加载标记的程序集。  
  
 用于 WPF 的已编译 XAML （通过 XamlBuildTask 生成）未使用中已加载的程序集 <xref:System.AppDomain> （步骤1）。 此外，名称应不会从 XamlBuildTask 输出进行限定，因此步骤 5 不适用。  
  
 虽然 BAML 也不应包含非限定程序集名称，但是已编译 BAML（通过 PresentationBuildTask 生成）会使用所有步骤。  
  
## <a name="see-also"></a>另请参阅

- [了解 XML 命名空间](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
