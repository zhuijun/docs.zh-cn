---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619818"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging 设为 true 的 GridViews 可能在离开视图最后一页时触发 PageIndexChanging 事件

#### <a name="details"></a>详细信息

.NET Framework 4.5 中的 bug 导致 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> 有时在遇到已启用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 时不会触发。

#### <a name="suggestion"></a>建议

此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。 作为解决方法，应用可以对任何满足以下条件的 <code>Page_Load</code> 执行显式 BindGrid（<xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 在最后一页且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> 不同于 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>）。 或者，可以将应用修改为允许分页（不是自定义分页），因为该方案不演示此问题。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
