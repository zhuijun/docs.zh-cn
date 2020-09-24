---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538809"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a>默认导入 Directory.Packages.props 文件

如果在项目文件夹或其任何上级中找到名为 Directory.Packages.props 的文件，则 NuGet 的 .props 文件会自动导入该文件 。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 8

#### <a name="change-description"></a>更改说明

在以前的 .NET 版本中，项目文件中有一个名为 Directory.Packages.props 的文件，并且 NuGet 的 .props 文件不会在生成时自动导入该文件 。

从 .NET 5.0 开始，如果项目文件夹或其任何上级中存在这样的文件，将自动导入它。 如果项目文件夹中有一个具有此名称的文件，则此自动导入可能会更改生成的行为。 例如，将导入该文件，但是与之前有所不同，如果你特意导入该文件，则导入顺序可能会发生变化。

#### <a name="reason-for-change"></a>更改原因

进行此更改是为了支持 NuGet 的[中央包版本控制](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions)。

#### <a name="recommended-action"></a>建议操作

如果不应自动导入现有 Directory.Packages.props 文件，请重命名此文件。

#### <a name="category"></a>类别

MSBuild

#### <a name="affected-apis"></a>受影响的 API

不可用

<!--

#### Affected APIs

Not detectable via API analysis.

-->
