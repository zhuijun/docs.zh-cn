---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621773"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>WPF 拼写检查器引发的 ObjectDisposedException

#### <a name="details"></a>详细信息

应用程序关闭，拼写检查器引发 <xref:System.ObjectDisposedException?displayProperty=fullName>，在这期间，WPF 应用程序有时会出现故障。 .NET Framework 4.7 WPF 中已通过妥善处理异常解决了此问题，因此确保了应用程序不再受到不良影响。 应注意，在调试器控制下运行的应用程序中会继续观察到偶尔引发的最可能异常。

#### <a name="suggestion"></a>建议

升级到 .NET Framework 4.7

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.6.1|
|类型|运行时|
