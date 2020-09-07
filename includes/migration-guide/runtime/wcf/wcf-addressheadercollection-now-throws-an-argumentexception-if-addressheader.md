---
ms.openlocfilehash: 200c22a1b83149d833a083365ebb65d0e80bc31a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496163"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>如果 addressHeader 元素为 null，则 WCF AddressHeaderCollection 现在引发 ArgumentException

#### <a name="details"></a>详细信息

自 .NET Framework 4.7.1 起，如果有一个元素为 <code>null</code>，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 构造函数就会引发 <xref:System.ArgumentException>。 在 .NET Framework 4.7 和更低版本中，不引发异常。

#### <a name="suggestion"></a>建议

如果在包含此更改的 .NET Framework 4.7.1 或更高版本中遇到兼容性问题，可以通过在 app.config 文件的 <code>&lt;runtime&gt;</code> 部分添加下面的代码行选择退出它：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名称    | 值       |
|:--------|:------------|
| 范围   |次要|
|Version|4.7.1|
|类型|运行时|

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
