---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621936"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a>修复了 ListBox 包含重复值类型时的挂起问题

#### <a name="details"></a>详细信息

修复了项集合包含重复的值类型对象时，虚拟化 <xref:System.Windows.Controls.ItemsControl> 可能在滚动期间挂起的问题。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |主要|
|Version|4.8|
|类型|运行时|
