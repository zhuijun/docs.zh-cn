---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621116"
---
### <a name="keytips-behavior-improved-in-wpf"></a>WPF 中改进的 Keytip 行为

#### <a name="details"></a>详细信息

已修改 Keytip 行为，以便对 Microsoft Word 和 Windows 资源管理器行为进行奇偶校验。 通过在按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey>（特别是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>）的情况下检查是否启用 keytip 状态，WPF 可正确地处理 keytip 键。 现在，即使是通过鼠标打开的菜单，keytip 也可将其关闭。

#### <a name="suggestion"></a>建议

不可用

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.7.2|
|类型|运行时|
