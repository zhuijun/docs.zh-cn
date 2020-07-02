---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621926"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="0c9cb-101">使用自定义 DataAnnotations.ValidationAttribute 时，ASP.NET ValidationContext.MemberName 不为 NULL</span><span class="sxs-lookup"><span data-stu-id="0c9cb-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="0c9cb-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0c9cb-102">Details</span></span>

<span data-ttu-id="0c9cb-103">在 .NET Framework 4.7.2 及更低版本中，使用自定义 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 时，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 属性返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="0c9cb-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="0c9cb-104">在 2019 年 10 月更新之前的 .NET Framework 4.8 版本中，它返回成员名称。</span><span class="sxs-lookup"><span data-stu-id="0c9cb-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="0c9cb-105">从 .NET Framework 4.8 的 [.NET Framework 2019 年 10 月质量汇总预览](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)开始，它默认将返回 `null`，但是可以选择改为返回成员名称。</span><span class="sxs-lookup"><span data-stu-id="0c9cb-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0c9cb-106">建议</span><span class="sxs-lookup"><span data-stu-id="0c9cb-106">Suggestion</span></span>

<span data-ttu-id="0c9cb-107">将以下设置添加到属性的 web.config 文件中，以返回 .NET Framework 4.8 和更高版本的 [.NET Framework 2019 年 10 月质量汇总预览](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)中的成员名称：</span><span class="sxs-lookup"><span data-stu-id="0c9cb-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="0c9cb-108">在 2019 年 10 月更新之前的 .NET Framework 4.8 版本中，将此内容添加到 web.config 文件中将还原以前的行为，并且属性返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="0c9cb-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="0c9cb-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="0c9cb-109">Name</span></span>    | <span data-ttu-id="0c9cb-110">“值”</span><span class="sxs-lookup"><span data-stu-id="0c9cb-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0c9cb-111">范围</span><span class="sxs-lookup"><span data-stu-id="0c9cb-111">Scope</span></span>   |<span data-ttu-id="0c9cb-112">未知</span><span class="sxs-lookup"><span data-stu-id="0c9cb-112">Unknown</span></span>|
|<span data-ttu-id="0c9cb-113">Version</span><span class="sxs-lookup"><span data-stu-id="0c9cb-113">Version</span></span>|<span data-ttu-id="0c9cb-114">4.8</span><span class="sxs-lookup"><span data-stu-id="0c9cb-114">4.8</span></span>|
|<span data-ttu-id="0c9cb-115">类型</span><span class="sxs-lookup"><span data-stu-id="0c9cb-115">Type</span></span>|<span data-ttu-id="0c9cb-116">运行时</span><span class="sxs-lookup"><span data-stu-id="0c9cb-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c9cb-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0c9cb-117">Affected APIs</span></span>

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
