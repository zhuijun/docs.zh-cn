---
ms.openlocfilehash: fa2a856911c7dcf81a39b7682a62a86c35328037
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275564"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="61b1e-101">如果 addressHeader 元素为 null，则 WCF AddressHeaderCollection 现在引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="61b1e-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

|   |   |
|---|---|
|<span data-ttu-id="61b1e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="61b1e-102">Details</span></span>|<span data-ttu-id="61b1e-103">自 .NET Framework 4.7.1 起，如果有一个元素为 <code>null</code>，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 构造函数就会引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="61b1e-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="61b1e-104">在 .NET Framework 4.7 和更低版本中，不引发异常。</span><span class="sxs-lookup"><span data-stu-id="61b1e-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>|
|<span data-ttu-id="61b1e-105">建议</span><span class="sxs-lookup"><span data-stu-id="61b1e-105">Suggestion</span></span>|<span data-ttu-id="61b1e-106">如果在包含此更改的 .NET Framework 4.7.1 或更高版本中遇到兼容性问题，可以通过在 app.config 文件的 <code>&lt;runtime&gt;</code> 部分添加下面的代码行选择退出它：</span><span class="sxs-lookup"><span data-stu-id="61b1e-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="61b1e-107">范围</span><span class="sxs-lookup"><span data-stu-id="61b1e-107">Scope</span></span>|<span data-ttu-id="61b1e-108">次要</span><span class="sxs-lookup"><span data-stu-id="61b1e-108">Minor</span></span>|
|<span data-ttu-id="61b1e-109">Version</span><span class="sxs-lookup"><span data-stu-id="61b1e-109">Version</span></span>|<span data-ttu-id="61b1e-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="61b1e-110">4.7.1</span></span>|
|<span data-ttu-id="61b1e-111">类型</span><span class="sxs-lookup"><span data-stu-id="61b1e-111">Type</span></span>|<span data-ttu-id="61b1e-112">运行时</span><span class="sxs-lookup"><span data-stu-id="61b1e-112">Runtime</span></span>|
|<span data-ttu-id="61b1e-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="61b1e-113">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
