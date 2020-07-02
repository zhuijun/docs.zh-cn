---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619874"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="eec95-101">WF 现在采用不同方式序列化 Expressions.Literal&lt;T&gt; DateTimes（中断自定义 XAML 分析器）</span><span class="sxs-lookup"><span data-stu-id="eec95-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="eec95-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="eec95-102">Details</span></span>

<span data-ttu-id="eec95-103">关联的 <xref:System.Windows.Markup.ValueSerializer> 对象将一个 <xref:System.DateTime?displayProperty=fullName> 或 <xref:System.DateTimeOffset?displayProperty=fullName> 对象（其 Second 和 <xref:System.DateTime.Millisecond?displayProperty=fullName> 组件非零且（针对 <xref:System.DateTime?displayProperty=fullName> 值）且其 <xref:System.DateTime.Kind> 属性不是 Unspecified）转换为属性元素语法而不是字符串。</span><span class="sxs-lookup"><span data-stu-id="eec95-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="eec95-104">此更改允许 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值往返。</span><span class="sxs-lookup"><span data-stu-id="eec95-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="eec95-105">假定输入 XAML 是采用特性语法的自定义 XAML 分析器将无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="eec95-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eec95-106">建议</span><span class="sxs-lookup"><span data-stu-id="eec95-106">Suggestion</span></span>

<span data-ttu-id="eec95-107">此更改允许 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值往返。</span><span class="sxs-lookup"><span data-stu-id="eec95-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="eec95-108">假定输入 XAML 是采用特性语法的自定义 XAML 分析器将无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="eec95-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="eec95-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="eec95-109">Name</span></span>    | <span data-ttu-id="eec95-110">“值”</span><span class="sxs-lookup"><span data-stu-id="eec95-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eec95-111">范围</span><span class="sxs-lookup"><span data-stu-id="eec95-111">Scope</span></span>   |<span data-ttu-id="eec95-112">边缘</span><span class="sxs-lookup"><span data-stu-id="eec95-112">Edge</span></span>|
|<span data-ttu-id="eec95-113">Version</span><span class="sxs-lookup"><span data-stu-id="eec95-113">Version</span></span>|<span data-ttu-id="eec95-114">4.5</span><span class="sxs-lookup"><span data-stu-id="eec95-114">4.5</span></span>|
|<span data-ttu-id="eec95-115">类型</span><span class="sxs-lookup"><span data-stu-id="eec95-115">Type</span></span>|<span data-ttu-id="eec95-116">运行时</span><span class="sxs-lookup"><span data-stu-id="eec95-116">Runtime</span></span>|
