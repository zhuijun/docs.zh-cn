---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619870"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>锁定承载来自 .NET Framework 1.1 和 2.0 的控件的托管浏览器

#### <a name="details"></a>详细信息

Internet Explorer 中阻止对这些控件的承载。

#### <a name="suggestion"></a>建议

Internet Explorer 将无法启动使用用于承载控件的托管浏览器的应用程序。 通过将注册表子项 <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> 的 EnableIEHosting 值设置为 <code>1</code>（对于 x86 系统和 x64 系统上的 32 位处理器），并将注册表子项 <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> 的 <code>EnableIEHosting</code> 值设置为 <code>1</code>（对于 x64 系统上的 64 位处理器），可以还原之前的行为。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.5|
|类型|运行时|
