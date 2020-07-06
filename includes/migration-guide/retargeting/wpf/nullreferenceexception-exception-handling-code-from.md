---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614390"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="7926b-101">ImageSourceConverter.ConvertFrom 异常处理代码中的 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="7926b-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="7926b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="7926b-102">Details</span></span>

<span data-ttu-id="7926b-103"><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> 的异常处理代码中的错误导致引发不正确的 <xref:System.NullReferenceException?displayProperty=fullName> 而不是预期的异常（<xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> 或 <xref:System.IO.FileNotFoundException?displayProperty=fullName>）。</span><span class="sxs-lookup"><span data-stu-id="7926b-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="7926b-104">此更改更正了该错误，因此，该方法现在将引发正确的异常。</span><span class="sxs-lookup"><span data-stu-id="7926b-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="7926b-105">默认情况下，所有面向 .NET Framework 4.6.2 和更低版本的应用程序都将继续引发 <xref:System.NullReferenceException?displayProperty=fullName> 以确保兼容性。</span><span class="sxs-lookup"><span data-stu-id="7926b-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="7926b-106">面向 .NET Framework 4.7 和更高版本的开发人员应该能看到正确的异常。</span><span class="sxs-lookup"><span data-stu-id="7926b-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7926b-107">建议</span><span class="sxs-lookup"><span data-stu-id="7926b-107">Suggestion</span></span>

<span data-ttu-id="7926b-108">想要还原为在面向 .NET Framework 4.7 或更高版本时获取 <xref:System.NullReferenceException?displayProperty=fullName> 的开发人员可将以下内容添加/合并到应用程序的 App.config 文件：</span><span class="sxs-lookup"><span data-stu-id="7926b-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7926b-109">名称</span><span class="sxs-lookup"><span data-stu-id="7926b-109">Name</span></span>    | <span data-ttu-id="7926b-110">“值”</span><span class="sxs-lookup"><span data-stu-id="7926b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7926b-111">范围</span><span class="sxs-lookup"><span data-stu-id="7926b-111">Scope</span></span>   | <span data-ttu-id="7926b-112">边缘</span><span class="sxs-lookup"><span data-stu-id="7926b-112">Edge</span></span>        |
| <span data-ttu-id="7926b-113">Version</span><span class="sxs-lookup"><span data-stu-id="7926b-113">Version</span></span> | <span data-ttu-id="7926b-114">4.7</span><span class="sxs-lookup"><span data-stu-id="7926b-114">4.7</span></span>         |
| <span data-ttu-id="7926b-115">类型</span><span class="sxs-lookup"><span data-stu-id="7926b-115">Type</span></span>    | <span data-ttu-id="7926b-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="7926b-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7926b-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="7926b-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
