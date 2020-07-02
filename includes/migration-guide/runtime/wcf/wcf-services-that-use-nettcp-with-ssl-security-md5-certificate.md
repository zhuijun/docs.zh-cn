---
ms.openlocfilehash: fb9436ec9e525afb497033775e34b6b636ced22d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621153"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a><span data-ttu-id="8a60c-101">使用带有 SSL 安全和 MD5 证书身份验证的 NETTCP 的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="8a60c-101">WCF services that use NETTCP with SSL security and MD5 certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="8a60c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8a60c-102">Details</span></span>

<span data-ttu-id="8a60c-103">.NET Framework 4.6 将 TLS 1.1 和 TLS 1.2 添加到 WCF SSL 默认协议列表。</span><span class="sxs-lookup"><span data-stu-id="8a60c-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL default protocol list.</span></span> <span data-ttu-id="8a60c-104">客户端和服务器计算机都安装了 .NET Framework 4.6 或更高版本时，TLS 1.2 用于协商。TLS 1.2 不支持 MD5 证书身份验证。</span><span class="sxs-lookup"><span data-stu-id="8a60c-104">When both client and server machines have the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="8a60c-105">因此，如果客户使用 MD5 证书，WCF 客户端将无法连接到 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="8a60c-105">As a result, if a customer uses an MD5 certificate, the WCF client will fail to connect to the WCF service.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8a60c-106">建议</span><span class="sxs-lookup"><span data-stu-id="8a60c-106">Suggestion</span></span>

<span data-ttu-id="8a60c-107">可以通过执行下列任一操作来解决此问题，以便 WCF 客户端可以连接 WCF 服务器：</span><span class="sxs-lookup"><span data-stu-id="8a60c-107">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="8a60c-108">将证书更新为不使用 MD5 算法。</span><span class="sxs-lookup"><span data-stu-id="8a60c-108">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="8a60c-109">建议采用此解决方案。</span><span class="sxs-lookup"><span data-stu-id="8a60c-109">This is the recommended solution.</span></span>
- <span data-ttu-id="8a60c-110">如果未在源代码中动态配置绑定，将应用程序的配置文件更新为使用 TLS 1.1 或更低版本的协议。</span><span class="sxs-lookup"><span data-stu-id="8a60c-110">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="8a60c-111">这样便可以继续将证书和 MD5 哈希算法结合使用。</span><span class="sxs-lookup"><span data-stu-id="8a60c-111">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

> [!WARNING]
> <span data-ttu-id="8a60c-112">不建议采用此解决方法，因为使用 MD5 哈希算法的证书被视为不安全。</span><span class="sxs-lookup"><span data-stu-id="8a60c-112">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

<span data-ttu-id="8a60c-113">下面的配置文件就采用了此解决方法：</span><span class="sxs-lookup"><span data-stu-id="8a60c-113">The following configuration file does this:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- <span data-ttu-id="8a60c-114">如果在源代码中动态配置了绑定，将 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> 属性更新为在源代码中使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) 或更早版本的协议。</span><span class="sxs-lookup"><span data-stu-id="8a60c-114">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> or an earlier version of the protocol in the source code.</span></span>

> [!WARNING]
> <span data-ttu-id="8a60c-115">不建议采用此解决方法，因为使用 MD5 哈希算法的证书被视为不安全。</span><span class="sxs-lookup"><span data-stu-id="8a60c-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

| <span data-ttu-id="8a60c-116">“属性”</span><span class="sxs-lookup"><span data-stu-id="8a60c-116">Name</span></span>    | <span data-ttu-id="8a60c-117">值</span><span class="sxs-lookup"><span data-stu-id="8a60c-117">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="8a60c-118">范围</span><span class="sxs-lookup"><span data-stu-id="8a60c-118">Scope</span></span>   | <span data-ttu-id="8a60c-119">次要</span><span class="sxs-lookup"><span data-stu-id="8a60c-119">Minor</span></span>   |
| <span data-ttu-id="8a60c-120">Version</span><span class="sxs-lookup"><span data-stu-id="8a60c-120">Version</span></span> | <span data-ttu-id="8a60c-121">4.6</span><span class="sxs-lookup"><span data-stu-id="8a60c-121">4.6</span></span>     |
| <span data-ttu-id="8a60c-122">类型</span><span class="sxs-lookup"><span data-stu-id="8a60c-122">Type</span></span>    | <span data-ttu-id="8a60c-123">运行时</span><span class="sxs-lookup"><span data-stu-id="8a60c-123">Runtime</span></span> |
