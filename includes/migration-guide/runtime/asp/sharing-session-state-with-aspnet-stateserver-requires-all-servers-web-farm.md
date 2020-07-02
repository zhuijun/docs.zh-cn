---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619824"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>与 Asp.Net StateServer 共享会话状态需要 Web 场中的所有服务器使用相同版本的 .NET Framework

#### <a name="details"></a>详细信息

启用 <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> 会话状态时，给定 Web 场中的所有服务器必须使用相同版本的 .NET Framework 以便正确共享状态。

#### <a name="suggestion"></a>建议

请务必在同时共享状态的 Web 服务器上升级 .NET Framework 版本。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
