---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621053"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="ddf15-101">如果 addressHeader 元素为 null，则 WCF AddressHeaderCollection 现在引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="ddf15-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="ddf15-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ddf15-102">Details</span></span>

<span data-ttu-id="ddf15-103">自 .NET Framework 4.7.1 起，如果有一个元素为 <code>null</code>，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 构造函数就会引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ddf15-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="ddf15-104">在 .NET Framework 4.7 和更低版本中，不引发异常。</span><span class="sxs-lookup"><span data-stu-id="ddf15-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ddf15-105">建议</span><span class="sxs-lookup"><span data-stu-id="ddf15-105">Suggestion</span></span>

<span data-ttu-id="ddf15-106">如果在包含此更改的 .NET Framework 4.7.1 或更高版本中遇到兼容性问题，可以通过在 app.config 文件的 <code>&lt;runtime&gt;</code> 部分添加下面的代码行选择退出它：</span><span class="sxs-lookup"><span data-stu-id="ddf15-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ddf15-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="ddf15-107">Name</span></span>    | <span data-ttu-id="ddf15-108">值</span><span class="sxs-lookup"><span data-stu-id="ddf15-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ddf15-109">范围</span><span class="sxs-lookup"><span data-stu-id="ddf15-109">Scope</span></span>   |<span data-ttu-id="ddf15-110">次要</span><span class="sxs-lookup"><span data-stu-id="ddf15-110">Minor</span></span>|
|<span data-ttu-id="ddf15-111">Version</span><span class="sxs-lookup"><span data-stu-id="ddf15-111">Version</span></span>|<span data-ttu-id="ddf15-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ddf15-112">4.7.1</span></span>|
|<span data-ttu-id="ddf15-113">类型</span><span class="sxs-lookup"><span data-stu-id="ddf15-113">Type</span></span>|<span data-ttu-id="ddf15-114">运行时</span><span class="sxs-lookup"><span data-stu-id="ddf15-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ddf15-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ddf15-115">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
