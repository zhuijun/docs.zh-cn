---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621058"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen=False 的链接弹出窗口

#### <a name="details"></a>详细信息

在弹出窗口外部单击时，StaysOpen=False 的弹出窗口应该关闭。 当链接两个或更多此类弹出窗口时（即一个包含另一个），会出现很多问题，包括：<ul><li>打开两个级别，在 P2 外部单击，但却在 P1 内。  没有反应。</li><li>打开两个级别，在 P1 外部单击。  两个弹出窗口关闭。</li><li>打开和关闭两个级别。  然后尝试再次打开 P2。  没有反应。</li><li>尝试打开三个级别。  无法打开。  （要么不执行任何操作，要么前两个级别关闭，具体取决于单击的位置。）这些情况（及其他变体情况）现在按预期方式工作。</li></ul>

| “属性”    | 值       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.7.1|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
