---
title: Internet Explorer 完成的与 WCF 完成的服务证书验证之间的差异
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 151075f2894b895ab90418748df9face3aa70252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599186"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="416ea-102">Internet Explorer 完成的与 WCF 完成的服务证书验证之间的差异</span><span class="sxs-lookup"><span data-stu-id="416ea-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="416ea-103">由于 Internet Explorer 和 Windows Communication Foundation （WCF）在使用 HTTPS 时验证服务证书的方式不同，因此 Internet Explorer 将无法访问帮助页或服务的 Web 服务描述语言（WSDL），即使 WCF 客户端可以成功地将消息发送到服务终结点也是如此。</span><span class="sxs-lookup"><span data-stu-id="416ea-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="416ea-104">这是因为 Internet Explorer 会检查服务证书是否 `ServerAuthentication` 在增强使用标志中具有对象标识符（OID），而 WCF 不会强制实施此类约束。</span><span class="sxs-lookup"><span data-stu-id="416ea-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="416ea-105">如果 Internet Explorer 无法访问服务帮助页或服务的 WSDL，请使用 "使用"[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)访问服务元数据。</span><span class="sxs-lookup"><span data-stu-id="416ea-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416ea-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="416ea-106">See also</span></span>

- [<span data-ttu-id="416ea-107">HTTPS、通过 TCP 的 SSL 与 SOAP 安全之间的证书验证差异</span><span class="sxs-lookup"><span data-stu-id="416ea-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="416ea-108">如何：检索元数据并实现兼容服务</span><span class="sxs-lookup"><span data-stu-id="416ea-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
