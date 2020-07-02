---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619862"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>maxRequestLength 或 maxReceivedMessageSize 的错误代码是不同的

#### <a name="details"></a>详细信息

Internet Information Services (IIS) 或 ASP.NET 开发服务器承载的 WCF Web 服务中的消息如果超过 maxRequestLength（在 ASP.NET 中）或 maxReceivedMessageSize（在 WCF 中），则有不同的错误代码。HTTP 状态代码已从 400（错误请求）更改为 413（请求实体太大），并且超过 maxRequestLength 或 maxReceivedMessageSize 设置的消息引发了 <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> 异常。 这包括转换模式为“流式处理”的情况。

#### <a name="suggestion"></a>建议

在消息长度超过 ASP.NET 或 WCF 所允许的限制的情况下，此更改有利于调试。必须基于 HTTP 400 状态代码修改执行处理的任何代码。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时|
