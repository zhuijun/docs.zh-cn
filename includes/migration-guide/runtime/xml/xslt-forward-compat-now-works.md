---
ms.openlocfilehash: 8c8477ae3719cfcc2060459ba85bcc9e76f11c41
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496348"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="60c85-101">XSLT 向前兼容现在有效</span><span class="sxs-lookup"><span data-stu-id="60c85-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="60c85-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="60c85-102">Details</span></span>

<span data-ttu-id="60c85-103">在 .NET Framework 4 中，XSLT 1.0 向前兼容性具有以下问题：</span><span class="sxs-lookup"><span data-stu-id="60c85-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="60c85-104">如果其版本设置为 2.0，并且分析器遇到无法识别的 XSLT 1.0 构造，则无法加载样式表。</span><span class="sxs-lookup"><span data-stu-id="60c85-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="60c85-105">如果将样式表版本设置为 1.1，则 <code>xsl:sort</code> 构造无法对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="60c85-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="60c85-106">在 .NET Framework 4.5 中，这些问题已修复，并且 XSLT 1.0 向前兼容性模式可正常工作。</span><span class="sxs-lookup"><span data-stu-id="60c85-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="60c85-107">建议</span><span class="sxs-lookup"><span data-stu-id="60c85-107">Suggestion</span></span>

<span data-ttu-id="60c85-108">大多数应用应该不受影响，但由于遵循 xsl:sort，某些情况下数据排序将会不同。</span><span class="sxs-lookup"><span data-stu-id="60c85-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="60c85-109">如果在 1.1 样式表中使用 <code>xsl:sort</code>，请确定应用不依赖于未排序数据。</span><span class="sxs-lookup"><span data-stu-id="60c85-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="60c85-110">如果应用依赖于 4.0 排序行为，请从样式表删除 <code>xsl:sort</code>。</span><span class="sxs-lookup"><span data-stu-id="60c85-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="60c85-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="60c85-111">Name</span></span>    | <span data-ttu-id="60c85-112">“值”</span><span class="sxs-lookup"><span data-stu-id="60c85-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="60c85-113">范围</span><span class="sxs-lookup"><span data-stu-id="60c85-113">Scope</span></span>   |<span data-ttu-id="60c85-114">边缘</span><span class="sxs-lookup"><span data-stu-id="60c85-114">Edge</span></span>|
|<span data-ttu-id="60c85-115">Version</span><span class="sxs-lookup"><span data-stu-id="60c85-115">Version</span></span>|<span data-ttu-id="60c85-116">4.5</span><span class="sxs-lookup"><span data-stu-id="60c85-116">4.5</span></span>|
|<span data-ttu-id="60c85-117">类型</span><span class="sxs-lookup"><span data-stu-id="60c85-117">Type</span></span>|<span data-ttu-id="60c85-118">运行时</span><span class="sxs-lookup"><span data-stu-id="60c85-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="60c85-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="60c85-119">Affected APIs</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Xml.Xsl.XslCompiledTransform`

-->
