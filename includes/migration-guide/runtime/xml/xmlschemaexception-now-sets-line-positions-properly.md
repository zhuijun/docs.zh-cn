---
ms.openlocfilehash: 04d1c1162dc79bbcb0578c6661466f4d58a57acc
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497911"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="0483f-101">XmlSchemaException 现在正确设置行位置</span><span class="sxs-lookup"><span data-stu-id="0483f-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="0483f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0483f-102">Details</span></span>

<span data-ttu-id="0483f-103">如果将 <xref:System.Xml.Linq.LoadOptions.SetLineInfo> 值传递给 Load 方法并发生验证错误，则 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 属性现在包含行信息。</span><span class="sxs-lookup"><span data-stu-id="0483f-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0483f-104">建议</span><span class="sxs-lookup"><span data-stu-id="0483f-104">Suggestion</span></span>

<span data-ttu-id="0483f-105">应该更新假设不设置 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 的异常处理代码，因为这些属性将会在加载 XML 且使用 SetLineInfo 的时候正确设置。</span><span class="sxs-lookup"><span data-stu-id="0483f-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="0483f-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="0483f-106">Name</span></span>    | <span data-ttu-id="0483f-107">“值”</span><span class="sxs-lookup"><span data-stu-id="0483f-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0483f-108">范围</span><span class="sxs-lookup"><span data-stu-id="0483f-108">Scope</span></span>   |<span data-ttu-id="0483f-109">边缘</span><span class="sxs-lookup"><span data-stu-id="0483f-109">Edge</span></span>|
|<span data-ttu-id="0483f-110">Version</span><span class="sxs-lookup"><span data-stu-id="0483f-110">Version</span></span>|<span data-ttu-id="0483f-111">4.5</span><span class="sxs-lookup"><span data-stu-id="0483f-111">4.5</span></span>|
|<span data-ttu-id="0483f-112">类型</span><span class="sxs-lookup"><span data-stu-id="0483f-112">Type</span></span>|<span data-ttu-id="0483f-113">运行时</span><span class="sxs-lookup"><span data-stu-id="0483f-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="0483f-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0483f-114">Affected APIs</span></span>

- <xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Xml.Linq.LoadOptions.SetLineInfo`

-->
