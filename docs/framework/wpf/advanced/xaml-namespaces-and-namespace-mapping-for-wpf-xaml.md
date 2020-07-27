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
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a><span data-ttu-id="0f42b-103">WPF XAML 的 XAML 命名空间和命名空间映射</span><span class="sxs-lookup"><span data-stu-id="0f42b-103">XAML Namespaces and Namespace Mapping for WPF XAML</span></span>
<span data-ttu-id="0f42b-104">本主题进一步解释通常在 WPF XAML 文件的根标记中出现的两个 XAML 命名空间映射的存在性和用途。</span><span class="sxs-lookup"><span data-stu-id="0f42b-104">This topic further explains the presence and purpose of the two XAML namespace mappings as often found in the root tag of a WPF XAML file.</span></span> <span data-ttu-id="0f42b-105">此外，还介绍如何生成相似映射以使用代码中和/或单独程序集内定义的元素。</span><span class="sxs-lookup"><span data-stu-id="0f42b-105">It also describes how to produce similar mappings for using elements that are defined in your own code, and/or within separate assemblies.</span></span>  

## <a name="what-is-a-xaml-namespace"></a><span data-ttu-id="0f42b-106">什么是 XAML 命名空间？</span><span class="sxs-lookup"><span data-stu-id="0f42b-106">What is a XAML Namespace?</span></span>  
 <span data-ttu-id="0f42b-107">XAML 命名空间实际上是 XML 命名空间概念的扩展。</span><span class="sxs-lookup"><span data-stu-id="0f42b-107">A XAML namespace is really an extension of the concept of an XML namespace.</span></span> <span data-ttu-id="0f42b-108">指定 XAML 命名空间的方法依赖于 XML 命名空间语法、将 URI 用作命名空间标识符以及使用前缀提供从相同标记源引用多个命名空间等约定。</span><span class="sxs-lookup"><span data-stu-id="0f42b-108">The techniques of specifying a XAML namespace rely on the XML namespace syntax, the convention of using URIs as namespace identifiers, using prefixes to provide a means to reference multiple namespaces from the same markup source, and so on.</span></span> <span data-ttu-id="0f42b-109">XML 命名空间的 XAML 定义增添的主要概念是，XAML 命名空间表示标记用法唯一性范围，还影响标记实体可如何受特定 CLR 命名空间和引用程序集支持。</span><span class="sxs-lookup"><span data-stu-id="0f42b-109">The primary concept that is added to the XAML definition of the XML namespace is that a XAML namespace implies both a scope of uniqueness for the markup usages, and also influences how markup entities are potentially backed by specific CLR namespaces and referenced assemblies.</span></span> <span data-ttu-id="0f42b-110">后者也会受 XAML 架构上下文概念影响。</span><span class="sxs-lookup"><span data-stu-id="0f42b-110">This latter consideration is also influenced by the concept of a XAML schema context.</span></span> <span data-ttu-id="0f42b-111">但是出于 WPF 如何处理 XAML 命名空间的目的，对于默认 XAML 命名空间、XAML 语言命名空间以及任何其他由 XAML 标记直接映射到特定支持 CLR 命名空间和引用程序集的 XAML 命名空间，可通常考虑为 XAML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0f42b-111">But for purposes of how WPF works with XAML namespaces, you can generally think of XAML namespaces in terms of a default XAML namespace, the XAML language namespace, and any further XAML namespaces as mapped by your XAML markup directly to specific backing CLR namespaces and referenced assemblies.</span></span>  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a><span data-ttu-id="0f42b-112">WPF 和 XAML 命名空间声明</span><span class="sxs-lookup"><span data-stu-id="0f42b-112">The WPF and XAML Namespace Declarations</span></span>  
 <span data-ttu-id="0f42b-113">在许多 XAML 文件的根标记中的命名空间声明内，通常可看到两个 XML 命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="0f42b-113">Within the namespace declarations in the root tag of many XAML files, you will see that there are typically two XML namespace declarations.</span></span> <span data-ttu-id="0f42b-114">第一个声明默认映射整个 WPF 客户端/框架 XAML 命名空间：</span><span class="sxs-lookup"><span data-stu-id="0f42b-114">The first declaration maps the overall WPF client / framework XAML namespace as the default:</span></span>  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 <span data-ttu-id="0f42b-115">第二个声明映射单独的 XAML 命名空间，（通常）将其映射到 `x:` 前缀。</span><span class="sxs-lookup"><span data-stu-id="0f42b-115">The second declaration maps a separate XAML namespace, mapping it (typically) to the `x:` prefix.</span></span>  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 <span data-ttu-id="0f42b-116">这些声明之间的关系是 `x:` 前缀映射支持 XAML 语言定义中的内部函数，并且 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是将 XAML 用作语言并为 XAML 定义对象词汇的一种实现。</span><span class="sxs-lookup"><span data-stu-id="0f42b-116">The relationship between these declarations is that the `x:` prefix mapping supports the intrinsics that are part of the XAML language definition, and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] is one implementation that uses XAML as a language and defines a vocabulary of its objects for XAML.</span></span> <span data-ttu-id="0f42b-117">因为 WPF 词汇用法远比 XAML 内部函数用法常见，因此默认映射 WPF 词汇。</span><span class="sxs-lookup"><span data-stu-id="0f42b-117">Because the WPF vocabulary's usages will be far more common than the XAML intrinsics usages, the WPF vocabulary is mapped as the default.</span></span>  
  
 <span data-ttu-id="0f42b-118">`x:`映射 XAML 语言内部函数支持的前缀约定后跟项目模板、示例代码和此 SDK 中的语言功能文档。</span><span class="sxs-lookup"><span data-stu-id="0f42b-118">The `x:` prefix convention for mapping the XAML language intrinsics support is followed by project templates, sample code, and the documentation of language features within this SDK.</span></span> <span data-ttu-id="0f42b-119">XAML 命名空间定义许多常用功能，即使对于基本 WPF 应用程序而言，这些功能也是必需的。</span><span class="sxs-lookup"><span data-stu-id="0f42b-119">The XAML namespace defines many commonly-used features that are necessary even for basic WPF  applications.</span></span> <span data-ttu-id="0f42b-120">例如，若要通过分部类将任何代码隐藏加入到 XAML 文件，必须将该类命名为相关 XAML 文件根元素中的 `x:Class` 属性。</span><span class="sxs-lookup"><span data-stu-id="0f42b-120">For instance, in order to join any code-behind to a XAML file through a partial class, you must name that class as the `x:Class` attribute in the root element of the relevant XAML file.</span></span> <span data-ttu-id="0f42b-121">或者，XAML 页面中定义的任何要作为键控资源访问的元素都应在当前元素上设置 `x:Key` 属性。</span><span class="sxs-lookup"><span data-stu-id="0f42b-121">Or, any element as defined in a XAML page that you wish to access as a keyed resource should have the `x:Key` attribute set on the element in question.</span></span> <span data-ttu-id="0f42b-122">有关 XAML 的这些方面和其他方面的详细信息，请参阅 [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md) 或 [XAML 语法详述](xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="0f42b-122">For more information on these and other aspects of XAML see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [XAML Syntax In Detail](xaml-syntax-in-detail.md).</span></span>  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a><span data-ttu-id="0f42b-123">映射到自定义类和程序集</span><span class="sxs-lookup"><span data-stu-id="0f42b-123">Mapping to Custom Classes and Assemblies</span></span>  
 <span data-ttu-id="0f42b-124">在 `xmlns` 前缀声明内使用一系列标记可将 XML 命名空间映射到程序集，方法类似于将标准 WPF 和 XAML 内部函数 XAML 命名空间映射到前缀。</span><span class="sxs-lookup"><span data-stu-id="0f42b-124">You can map XML namespaces to assemblies using a series of tokens within an `xmlns` prefix declaration, similar to how the standard WPF and XAML-intrinsics XAML namespaces are mapped to prefixes.</span></span>  
  
 <span data-ttu-id="0f42b-125">此语法采用以下可能的已命名标记和以下值：</span><span class="sxs-lookup"><span data-stu-id="0f42b-125">The syntax takes the following possible named tokens and following values:</span></span>  
  
 <span data-ttu-id="0f42b-126">`clr-namespace:` 在程序集中声明的 CLR 命名空间，此程序集包含要作为元素公开的公共类型。</span><span class="sxs-lookup"><span data-stu-id="0f42b-126">`clr-namespace:` The CLR namespace declared within the assembly that contains the public types to expose as elements.</span></span>  
  
 <span data-ttu-id="0f42b-127">`assembly=`包含部分或全部引用的 CLR 命名空间的程序集。</span><span class="sxs-lookup"><span data-stu-id="0f42b-127">`assembly=` The assembly that contains some or all of the referenced CLR namespace.</span></span> <span data-ttu-id="0f42b-128">此值通常为程序集的名称而不是路径，且不包含扩展名（例如 .dll 或 .exe）。</span><span class="sxs-lookup"><span data-stu-id="0f42b-128">This value is typically just the name of the assembly, not the path, and does not include the extension (such as .dll or .exe).</span></span> <span data-ttu-id="0f42b-129">程序集路径必须创建为包含要映射的 XAML 的项目文件中的项目引用。</span><span class="sxs-lookup"><span data-stu-id="0f42b-129">The path to that assembly must be established as a project reference in the project file that contains the XAML you are trying to map.</span></span> <span data-ttu-id="0f42b-130">为了并入版本控制和强名称签名， `assembly` 该值可以是由定义的字符串 <xref:System.Reflection.AssemblyName> ，而不是简单的字符串名称。</span><span class="sxs-lookup"><span data-stu-id="0f42b-130">In order to incorporate versioning and strong-name signing, the `assembly` value can be a string as defined by <xref:System.Reflection.AssemblyName>, rather than the simple string name.</span></span>  
  
 <span data-ttu-id="0f42b-131">请注意，分隔 `clr-namespace` 标记和其值的字符是冒号 (:)，而分隔 `assembly` 标记和其值的字符为等号 (=)。</span><span class="sxs-lookup"><span data-stu-id="0f42b-131">Note that the character separating the `clr-namespace` token from its value is a colon (:) whereas the character separating the `assembly` token from its value is an equals sign (=).</span></span> <span data-ttu-id="0f42b-132">这两个标记之间应使用的字符是分号。</span><span class="sxs-lookup"><span data-stu-id="0f42b-132">The character to use between these two tokens is a semicolon.</span></span> <span data-ttu-id="0f42b-133">此外，不要在声明中的任何位置包含任何空白。</span><span class="sxs-lookup"><span data-stu-id="0f42b-133">Also, do not include any white space anywhere in the declaration.</span></span>  
  
### <a name="a-basic-custom-mapping-example"></a><span data-ttu-id="0f42b-134">基本自定义映射示例</span><span class="sxs-lookup"><span data-stu-id="0f42b-134">A Basic Custom Mapping Example</span></span>  
 <span data-ttu-id="0f42b-135">如下代码定义一个示例自定义类：</span><span class="sxs-lookup"><span data-stu-id="0f42b-135">The following code defines an example custom class:</span></span>  
  
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
  
 <span data-ttu-id="0f42b-136">此自定义类随后编译到库，库按项目设置（未显示）命名为 `SDKSampleLibrary`。</span><span class="sxs-lookup"><span data-stu-id="0f42b-136">This custom class is then compiled into a library, which per the project settings (not shown) is named `SDKSampleLibrary`.</span></span>  
  
 <span data-ttu-id="0f42b-137">为引用此自定义类，还需将其添加为当前项目的引用（通常可使用 Visual Studio 中的解决方案资源管理器 UI 完成此操作）。</span><span class="sxs-lookup"><span data-stu-id="0f42b-137">In order to reference this custom class, you also need to include it as a reference for your current project, which you would typically do using the Solution Explorer UI in Visual Studio.</span></span>  
  
 <span data-ttu-id="0f42b-138">具有包含类的库并在项目设置中对其进行引用后，可将如下前缀映射到 XAML 中的根元素中：</span><span class="sxs-lookup"><span data-stu-id="0f42b-138">Now that you have a library containing a class, and a reference to it in project settings, you can add the following prefix mapping as part of your root element in XAML:</span></span>  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 <span data-ttu-id="0f42b-139">综合而言，以下为根标记中包含自定义映射、典型默认值和 x: 映射的 XAML，然后使用前缀引用实例化此 UI 中的 `ExampleClass`：</span><span class="sxs-lookup"><span data-stu-id="0f42b-139">To put it all together, the following is XAML that includes the custom mapping along with the typical default and x: mappings in the root tag, then uses a prefixed reference to instantiate `ExampleClass` in that UI:</span></span>  
  
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
  
### <a name="mapping-to-current-assemblies"></a><span data-ttu-id="0f42b-140">映射到当前程序集</span><span class="sxs-lookup"><span data-stu-id="0f42b-140">Mapping to Current Assemblies</span></span>  
 <span data-ttu-id="0f42b-141">如果要在与引用自定义类的应用程序代码相同的程序集内定义引用的 `clr-namespace`，则可省略 `assembly`。</span><span class="sxs-lookup"><span data-stu-id="0f42b-141">`assembly` can be omitted if the `clr-namespace` referenced is being defined within the same assembly as the application code that is referencing the custom classes.</span></span> <span data-ttu-id="0f42b-142">或者，这种情况的等效语法是指定 `assembly=` 且等号后不含任何字符串标记。</span><span class="sxs-lookup"><span data-stu-id="0f42b-142">Or, an equivalent syntax for this case is to specify `assembly=`, with no string token following the equals sign.</span></span>  
  
 <span data-ttu-id="0f42b-143">如果在同一程序集中定义，则自定义类无法用作页面的根元素。</span><span class="sxs-lookup"><span data-stu-id="0f42b-143">Custom classes cannot be used as the root element of a page if defined in the same assembly.</span></span> <span data-ttu-id="0f42b-144">分部类无需映射；仅需映射应用程序中不是页面分部类的类（若要将其引用为 XAML 中的元素）。</span><span class="sxs-lookup"><span data-stu-id="0f42b-144">Partial classes do not need to be mapped; only classes that are not the partial class of a page in your application need to be mapped if you intend to reference them as elements in XAML.</span></span>  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a><span data-ttu-id="0f42b-145">将 CLR 命名空间映射到程序集中的 XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="0f42b-145">Mapping CLR Namespaces to XML Namespaces in an Assembly</span></span>  
 <span data-ttu-id="0f42b-146">WPF 定义 XAML 处理器使用的 CLR 属性，以便将多个 CLR 命名空间映射到单个 XAML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0f42b-146">WPF defines a CLR attribute that is consumed by XAML processors in order to map multiple CLR namespaces to a single XAML namespace.</span></span> <span data-ttu-id="0f42b-147">此属性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 将放置在生成程序集的源代码的程序集级别上。</span><span class="sxs-lookup"><span data-stu-id="0f42b-147">This attribute, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, is placed at the assembly level in the source code that produces the assembly.</span></span> <span data-ttu-id="0f42b-148">WPF 程序集源代码使用此特性将各种公共命名空间（如 <xref:System.Windows> 和 <xref:System.Windows.Controls> ）映射到 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0f42b-148">The WPF assembly source code uses this attribute to map the various common namespaces, such as <xref:System.Windows> and <xref:System.Windows.Controls>, to the `http://schemas.microsoft.com/winfx/2006/xaml/presentation` namespace.</span></span>  
  
 <span data-ttu-id="0f42b-149"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>采用两个参数： XML/XAML 命名空间名称和 CLR 命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="0f42b-149">The <xref:System.Windows.Markup.XmlnsDefinitionAttribute> takes two parameters: the XML/XAML namespace name, and the CLR namespace name.</span></span> <span data-ttu-id="0f42b-150"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以有多个 CLR 命名空间，以便将多个 CLR 命名空间映射到同一个 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0f42b-150">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can exist to map multiple CLR namespaces to the same XML namespace.</span></span> <span data-ttu-id="0f42b-151">映射后，通过在分部类代码隐藏页中提供相应 `using` 语句，可在无完全限定的情况下引用这些命名空间的成员（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="0f42b-151">Once mapped, members of those namespaces can also be referenced without full qualification if desired by providing the appropriate `using` statement in the partial-class code-behind page.</span></span> <span data-ttu-id="0f42b-152">如需了解详情，请访问 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0f42b-152">For more details, see <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span>  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a><span data-ttu-id="0f42b-153">设计器命名空间和 XAML 模板中的其他前缀</span><span class="sxs-lookup"><span data-stu-id="0f42b-153">Designer Namespaces and Other Prefixes From XAML Templates</span></span>  
 <span data-ttu-id="0f42b-154">如果使用 WPF XAML 的开发环境和/或设计工具，你可能会注意到 XAML 标记内存在其他定义的 XAML 命名空间/前缀。</span><span class="sxs-lookup"><span data-stu-id="0f42b-154">If you are working with development environments and/or design tools for WPF XAML, you may notice that there are other defined XAML namespaces / prefixes within the XAML markup.</span></span>  
  
 <span data-ttu-id="0f42b-155">适用于 Visual Studio 的 WPF 设计器使用通常映射到前缀的设计器命名空间 `d:` 。</span><span class="sxs-lookup"><span data-stu-id="0f42b-155">WPF Designer for Visual Studio uses a designer namespace that is typically mapped to the prefix `d:`.</span></span> <span data-ttu-id="0f42b-156">适用于 WPF 的更高的项目模板可以预映射此 XAML 命名空间，以支持 WPF 设计器与 Visual Studio 和其他设计环境之间的 XAML 交换。</span><span class="sxs-lookup"><span data-stu-id="0f42b-156">More recent project templates for WPF might pre-map this XAML namespace to support interchange of the XAML between WPF Designer for Visual Studio and other design environments.</span></span> <span data-ttu-id="0f42b-157">此设计 XAML 命名空间用于在设计器中往返基于 XAML 的 UI 时保持设计状态。</span><span class="sxs-lookup"><span data-stu-id="0f42b-157">This design XAML namespace is used to perpetuate design state while roundtripping XAML-based UI in the designer.</span></span> <span data-ttu-id="0f42b-158">它也用于 `d:IsDataSource`（在设计器中启用运行时数据源）等功能。</span><span class="sxs-lookup"><span data-stu-id="0f42b-158">It is also used for features such as `d:IsDataSource`, which enable runtime data sources in a designer.</span></span>  
  
 <span data-ttu-id="0f42b-159">可能看到的另一个映射前缀是 `mc:`。</span><span class="sxs-lookup"><span data-stu-id="0f42b-159">Another prefix you might see mapped is `mc:`.</span></span> <span data-ttu-id="0f42b-160">`mc:` 用于标记兼容，使用一种并不一定特定于 XAML 的标记兼容模式。</span><span class="sxs-lookup"><span data-stu-id="0f42b-160">`mc:` is for markup compatibility, and is leveraging a markup compatibility pattern that is not necessarily XAML-specific.</span></span> <span data-ttu-id="0f42b-161">某种程度上，标记兼容功能可用于在框架之间或跨后备实现的其他边界交换 XAML、在 XAML 架构上下文之间运行、为设计器中限制模式提供兼容性等。</span><span class="sxs-lookup"><span data-stu-id="0f42b-161">To some extent, the markup compatibility features can be used to exchange XAML between frameworks or across other boundaries of backing implementation, work between XAML schema contexts, provide compatibility for limited modes in designers, and so on.</span></span> <span data-ttu-id="0f42b-162">有关标记兼容概念及其与 WPF 的关系的详细信息，请参阅[标记兼容 (mc:) 语言功能](markup-compatibility-mc-language-features.md)。</span><span class="sxs-lookup"><span data-stu-id="0f42b-162">For more information on markup compatibility concepts and how they relate to WPF, see  [Markup Compatibility (mc:) Language Features](markup-compatibility-mc-language-features.md).</span></span>  
  
## <a name="wpf-and-assembly-loading"></a><span data-ttu-id="0f42b-163">WPF 和程序集加载</span><span class="sxs-lookup"><span data-stu-id="0f42b-163">WPF and Assembly Loading</span></span>  
 <span data-ttu-id="0f42b-164">WPF 的 XAML 架构上下文与 WPF 应用程序模型集成，后者又使用的 CLR 定义的概念 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="0f42b-164">The XAML schema context for WPF integrates with the WPF application model, which in turn uses the CLR-defined concept of <xref:System.AppDomain>.</span></span> <span data-ttu-id="0f42b-165">下面的序列说明 XAML 架构上下文如何解释如何在运行时或设计时加载程序集或查找类型，具体取决于 WPF 使用 <xref:System.AppDomain> 和其他因素。</span><span class="sxs-lookup"><span data-stu-id="0f42b-165">The following sequence describes how XAML schema context interprets how to either load assemblies or find types at run time or design time, based on the WPF use of <xref:System.AppDomain> and other factors.</span></span>  
  
1. <span data-ttu-id="0f42b-166">循环访问 <xref:System.AppDomain> ，查找与名称的所有方面匹配的已加载程序集（从最新加载的程序集开始）。</span><span class="sxs-lookup"><span data-stu-id="0f42b-166">Iterate through the <xref:System.AppDomain>, looking for an already-loaded assembly that matches all aspects of the name, starting from the most recently loaded assembly.</span></span>  
  
2. <span data-ttu-id="0f42b-167">如果名称是限定的，则对 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> 限定名称调用。</span><span class="sxs-lookup"><span data-stu-id="0f42b-167">If the name is qualified, call <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> on the qualified name.</span></span>  
  
3. <span data-ttu-id="0f42b-168">如果限定名称的短名称和公钥标记匹配从中加载标记的程序集，则返回此程序集。</span><span class="sxs-lookup"><span data-stu-id="0f42b-168">If the short name + public key token of a qualified name matches the assembly that the markup was loaded from, return that assembly.</span></span>  
  
4. <span data-ttu-id="0f42b-169">使用短名称 + 公钥标记调用 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0f42b-169">Use the short name + public key token to call <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.</span></span>  
  
5. <span data-ttu-id="0f42b-170">如果名称不合格，请调用 <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0f42b-170">If the name is unqualified, call <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0f42b-171">宽松型 XAML 不使用步骤 3；不存在从中加载标记的程序集。</span><span class="sxs-lookup"><span data-stu-id="0f42b-171">Loose XAML does not use Step 3; there is no loaded-from assembly.</span></span>  
  
 <span data-ttu-id="0f42b-172">用于 WPF 的已编译 XAML （通过 XamlBuildTask 生成）未使用中已加载的程序集 <xref:System.AppDomain> （步骤1）。</span><span class="sxs-lookup"><span data-stu-id="0f42b-172">Compiled XAML for WPF (generated via XamlBuildTask) does not use the already-loaded assemblies from <xref:System.AppDomain> (Step 1).</span></span> <span data-ttu-id="0f42b-173">此外，名称应不会从 XamlBuildTask 输出进行限定，因此步骤 5 不适用。</span><span class="sxs-lookup"><span data-stu-id="0f42b-173">Also, the name should never be unqualified from XamlBuildTask output, so Step 5 does not apply.</span></span>  
  
 <span data-ttu-id="0f42b-174">虽然 BAML 也不应包含非限定程序集名称，但是已编译 BAML（通过 PresentationBuildTask 生成）会使用所有步骤。</span><span class="sxs-lookup"><span data-stu-id="0f42b-174">Compiled BAML (generated via PresentationBuildTask) uses all steps, although BAML also should not contain unqualified assembly names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f42b-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f42b-175">See also</span></span>

- <span data-ttu-id="0f42b-176">[了解 XML 命名空间](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="0f42b-176">[Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))</span></span>
- [<span data-ttu-id="0f42b-177">XAML 概述 (WPF)</span><span class="sxs-lookup"><span data-stu-id="0f42b-177">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
