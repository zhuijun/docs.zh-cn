---
ms.openlocfilehash: e0f72d19a884087b1f0f6ebd1b6baea75bc37af4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619901"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF 生成可冻结鼠标的 wisptis.exe 进程

#### <a name="details"></a>详细信息

4\.5.2 中引入了一个问题，导致生成可冻结鼠标输入的 <code>wisptis.exe</code>。

#### <a name="suggestion"></a>建议

.NET Framework 4.5.2 的服务版本（修补程序汇总 3026376）中提供了此问题的修补程序，也可通过升级到 .NET Framework 4.6 解决此问题

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |主要|
|Version|4.5.2|
|类型|运行时|
