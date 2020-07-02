---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621044"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>允许在类似于 UNC 共享的 URI 中使用 Unicode

#### <a name="details"></a>详细信息

在 <xref:System.Uri?displayProperty=fullName> 中，构造包含 UNC 共享名称和 Unicode 字符的文件 URI 将不再导致出现内部状态无效的 URI。 仅当以下各项均为 true 时，该行为才会更改：<ul><li>URI 具有方案 <code>file:</code>，且后接四个及以上的斜杠。</li><li>主机名称以下划线或其他非保留符号开头。</li><li>URI 包含 Unicode 字符。</li></ul>

#### <a name="suggestion"></a>建议

使用始终包含 Unicode 的 URI 的应用程序可能已使用此行为来禁止对 UNC 共享的引用。 这些应用程序应使用 <xref:System.Uri.IsUnc>。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.7.2|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
