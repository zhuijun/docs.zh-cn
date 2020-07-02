---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621046"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>存在 Unicode 时支持特殊的相对 URI 表示法

#### <a name="details"></a>详细信息

如果在包含 Unicode 的某些相对 URI 上调用 <xref:System.Uri.TryCreate%2A>，则 <xref:System.Uri> 将不再引发 <xref:System.NullReferenceException>。 下面是重现 <xref:System.NullReferenceException> 最简单的做法，其中两个语句是等效的：<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>若要重现 <xref:System.NullReferenceException>，以下各项必须为 true：<ul><li>必须将 URI 指定为相对，方法是在其前追加“http:”，且其后不跟“//”。</li><li>URI 必须包含百分比编码的 Unicode 或未保留的符号。</li></ul>

#### <a name="suggestion"></a>建议

根据此行为禁用相对 URI 的用户应在创建 URI 时转而指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.7.2|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
