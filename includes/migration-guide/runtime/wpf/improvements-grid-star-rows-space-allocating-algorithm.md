---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621932"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>网格星型行空格分配算法的改进

#### <a name="details"></a>详细信息

修复了在 .NET Framework 4.7 中引入的 <xref:System.Windows.Controls.Grid> 中[用于分配大小的算法](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)的问题。  在某些情况下，例如，<code>Height=&quot;Auto&quot;</code> 包含空行的网格，行排列在错误的位置，可能完全在网格之外。

#### <a name="suggestion"></a>建议

为使应用程序从这些更改中获益，它必须在 .NET Framework 4.8 或更高版本上运行。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |主要|
|Version|4.8|
|类型|运行时|
