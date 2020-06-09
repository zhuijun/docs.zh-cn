---
title: WCF 中使用的安全概念
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: f852ba4e1100103289bc5fd879b19ebd40443b8d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595175"
---
# <a name="security-concepts-used-in-wcf"></a>WCF 中使用的安全概念
Windows Communication Foundation （WCF）安全基于已在使用并部署在各种安全基础结构中的概念而构建。  
  
 WCF 支持其中一些基础结构，如 HTTP （HTTPS）上的安全套接字层（SSL）。 不过，WCF 通过通过 SOAP 编码的消息实现更新的可互操作安全标准（如 WS 安全性），超出了现有安全基础结构的支持。 无论是使用现有机制还是新的可互操作标准，其背后的安全概念都是相同的。 理解现有基础结构以及较新的标准背后的概念对于为应用程序实现最佳安全模型至关重要。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web 服务安全简介  

Microsoft 模式和实践组编写了一篇称为[WCF 安全指南](https://archive.codeplex.com/?p=wcfsecurityguide)的详细白皮书。 本白皮书介绍了与 web 服务、关键的 WCF 安全概念、intranet 应用程序方案和 internet 应用程序方案相关的基本安全概念。  
  
## <a name="industry-wide-security-specifications"></a>业界级安全规范  
  
### <a name="public-key-infrastructure"></a>公钥基础结构  

公钥基础结构（PKI）是数字证书、证书颁发机构以及其他注册机构的系统，通过使用公钥加密对电子事务中涉及的每个参与方进行验证和身份验证。
  
### <a name="kerberos-protocol"></a>Kerberos 协议  
 *Kerberos 协议*是一种用于创建在 Windows 域上对用户进行身份验证的安全机制的规范。 它允许用户建立针对域中的其他实体的安全上下文。 Windows 2000 及版本更高的平台默认情况下使用 Kerberos 协议。 在创建将与 intranet 客户端进行交互的服务时，理解系统的机制非常有用。 此外，由于*Web Services 安全性 Kerberos 绑定*已广泛发布，因此可以使用 kerberos 协议与 Internet 客户端通信（即 kerberos 协议是可互操作的）。 有关如何在 Windows 中实现 Kerberos 协议的详细信息，请参阅[Microsoft kerberos](/windows/win32/secauthn/microsoft-kerberos)。  
  
### <a name="x509-certificates"></a>X.509 证书  
 X.509 证书是安全应用程序中使用的主要凭据形式。 有关 x.509 证书的详细信息，请参阅[X.509 公钥证书](/windows/win32/seccertenroll/about-x-509-public-key-certificates)。 X.509 证书存储在证书存储区中。 运行 Windows 的计算机有多种证书存储区，每一种都针对不同的用途。 有关不同存储的详细信息，请参阅[证书存储](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))。  
  
## <a name="web-services-security-specifications"></a>Web 服务安全规范  
 系统定义的绑定支持许多常用 Web 服务安全规范。 有关系统提供的绑定和它们支持的 web 服务规范的完整列表，请参阅：[系统提供的互操作性绑定支持的 Web 服务协议](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>访问控制机制  
 WCF 提供了多种服务或操作的访问控制方式。 其中包括：  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. ASP.NET 成员身份提供程序  
  
3. ASP.NET 角色提供程序  
  
4. 授权管理器  
  
5. 标识模型  
  
 有关这些主题的详细信息，请参阅[访问控制机制](access-control-mechanisms.md)  
  
## <a name="see-also"></a>另请参阅

- [安全性概述](security-overview.md)
- [Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
