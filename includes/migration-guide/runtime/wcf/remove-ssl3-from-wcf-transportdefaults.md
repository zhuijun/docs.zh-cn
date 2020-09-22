---
ms.openlocfilehash: a5f4047d70276a90c9d72918a2559fd795feb26e
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770908"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="e0312-101">从 WCF TransportDefaults 删除 Ssl3</span><span class="sxs-lookup"><span data-stu-id="e0312-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="e0312-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e0312-102">Details</span></span>

<span data-ttu-id="e0312-103">结合使用 NetTcp 与传输安全性和凭据类型证书时，SSL 3 协议不再是用于协商安全连接的默认协议。</span><span class="sxs-lookup"><span data-stu-id="e0312-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="e0312-104">在大多数情况下，应该不会对现有应用程序造成任何影响，因为 TLS 1.0 始终包含在 NetTcp 协议列表中。</span><span class="sxs-lookup"><span data-stu-id="e0312-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="e0312-105">所有现有客户端应该至少能够使用 TLS 1.0 来协商连接。</span><span class="sxs-lookup"><span data-stu-id="e0312-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e0312-106">建议</span><span class="sxs-lookup"><span data-stu-id="e0312-106">Suggestion</span></span>

<span data-ttu-id="e0312-107">如果 Ssl3 必需，则使用以下配置机制之一将 Ssl3 添加到协商协议的列表。</span><span class="sxs-lookup"><span data-stu-id="e0312-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>
- [<span data-ttu-id="e0312-108">\<netTcpBinding> 的 \<transport></span><span class="sxs-lookup"><span data-stu-id="e0312-108">\<transport> of \<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)
- [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

| <span data-ttu-id="e0312-109">名称</span><span class="sxs-lookup"><span data-stu-id="e0312-109">Name</span></span>    | <span data-ttu-id="e0312-110">值</span><span class="sxs-lookup"><span data-stu-id="e0312-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="e0312-111">范围</span><span class="sxs-lookup"><span data-stu-id="e0312-111">Scope</span></span>   | <span data-ttu-id="e0312-112">边缘</span><span class="sxs-lookup"><span data-stu-id="e0312-112">Edge</span></span>    |
| <span data-ttu-id="e0312-113">Version</span><span class="sxs-lookup"><span data-stu-id="e0312-113">Version</span></span> | <span data-ttu-id="e0312-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e0312-114">4.6.2</span></span>   |
| <span data-ttu-id="e0312-115">类型</span><span class="sxs-lookup"><span data-stu-id="e0312-115">Type</span></span>    | <span data-ttu-id="e0312-116">运行时</span><span class="sxs-lookup"><span data-stu-id="e0312-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e0312-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e0312-117">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
