---
ms.openlocfilehash: 23987c300ac4fbad401de180b63106cd234f8d27
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497803"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>从 WCF TransportDefaults 删除 Ssl3

#### <a name="details"></a>详细信息

结合使用 NetTcp 与传输安全性和凭据类型证书时，SSL 3 协议不再是用于协商安全连接的默认协议。 在大多数情况下，应该不会对现有应用程序造成任何影响，因为 TLS 1.0 始终包含在 NetTcp 协议列表中。 所有现有客户端应该至少能够使用 TLS 1.0 来协商连接。

#### <a name="suggestion"></a>建议

如果 Ssl3 必需，则使用以下配置机制之一将 Ssl3 添加到协商协议的列表。<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;customBinding&gt; 的 &lt;sslStreamSecurity&gt; 部分]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>

| 名称    | 值       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.6.2|
|类型|运行时|

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
