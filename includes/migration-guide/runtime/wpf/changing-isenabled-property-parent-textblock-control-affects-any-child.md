---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621059"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>更改 TextBlock 控件父级的 IsEnabled 属性会影响任何子控件

#### <a name="details"></a>详细信息

自 .NET Framework 4.6.2 起，更改 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 属性会影响 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件的任意子控件（例如超链接和按钮）。在 .NET Framework 4.6.1 和更早版本中，<xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 中的控件并非始终反映 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 属性状态。

#### <a name="suggestion"></a>建议

无。 此更改符合 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件中各控件的预期行为。

| “属性”    | 值       |
|:--------|:------------|
| 范围   |次要|
|Version|4.6.2|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
