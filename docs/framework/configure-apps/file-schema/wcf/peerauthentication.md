---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 118159617a7f4c27ecc5e8fe077c28cfefac8537
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397619"
---
# \<peerAuthentication>
<span data-ttu-id="68d1d-101">指定对等节点使用的对等证书的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="68d1d-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="68d1d-102">语法</span><span class="sxs-lookup"><span data-stu-id="68d1d-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68d1d-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="68d1d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="68d1d-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="68d1d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68d1d-105">特性</span><span class="sxs-lookup"><span data-stu-id="68d1d-105">Attributes</span></span>  
  
|<span data-ttu-id="68d1d-106">属性</span><span class="sxs-lookup"><span data-stu-id="68d1d-106">Attribute</span></span>|<span data-ttu-id="68d1d-107">说明</span><span class="sxs-lookup"><span data-stu-id="68d1d-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="68d1d-108">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="68d1d-108">Optional enumeration.</span></span> <span data-ttu-id="68d1d-109">指定用来验证凭据的三种模式之一。</span><span class="sxs-lookup"><span data-stu-id="68d1d-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="68d1d-110">此属性的类型为 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="68d1d-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="68d1d-111">如果设置为 `Custom`，则还必须提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="68d1d-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="68d1d-112">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="68d1d-112">Optional string.</span></span> <span data-ttu-id="68d1d-113">指定用于验证自定义类型的类型和程序集。</span><span class="sxs-lookup"><span data-stu-id="68d1d-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="68d1d-114">当 `certificateValidationMode` 设置为 `Custom` 时，必须设置此属性。</span><span class="sxs-lookup"><span data-stu-id="68d1d-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="68d1d-115">此属性的类型为 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="68d1d-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="68d1d-116">Windows Communication Foundation （WCF）提供了一个默认的对等证书验证程序，用于验证对等证书是否针对 "受信任人" 存储。</span><span class="sxs-lookup"><span data-stu-id="68d1d-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="68d1d-117">它还验证证书是否与有效的根相联系。</span><span class="sxs-lookup"><span data-stu-id="68d1d-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="68d1d-118">您可以实现自定义验证程序以指定不同的行为，并使用该属性指向自定义验证程序。</span><span class="sxs-lookup"><span data-stu-id="68d1d-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="68d1d-119">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="68d1d-119">Optional enumeration.</span></span> <span data-ttu-id="68d1d-120">指定证书吊销模式。</span><span class="sxs-lookup"><span data-stu-id="68d1d-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="68d1d-121">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="68d1d-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="68d1d-122">系统通过在吊销证书列表中进行查找来验证对等证书尚未吊销。</span><span class="sxs-lookup"><span data-stu-id="68d1d-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="68d1d-123">可以联机执行该检查，也可以根据缓存的吊销列表执行该检查。</span><span class="sxs-lookup"><span data-stu-id="68d1d-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="68d1d-124">将此属性设置为 NoCheck 可禁用吊销检查。</span><span class="sxs-lookup"><span data-stu-id="68d1d-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="68d1d-125">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="68d1d-125">Optional enumeration.</span></span> <span data-ttu-id="68d1d-126">指定 WCF 安全系统验证对等证书的受信任存储区位置。</span><span class="sxs-lookup"><span data-stu-id="68d1d-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="68d1d-127">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="68d1d-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68d1d-128">子元素</span><span class="sxs-lookup"><span data-stu-id="68d1d-128">Child Elements</span></span>  
 <span data-ttu-id="68d1d-129">无。</span><span class="sxs-lookup"><span data-stu-id="68d1d-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68d1d-130">父元素</span><span class="sxs-lookup"><span data-stu-id="68d1d-130">Parent Elements</span></span>  
  
|<span data-ttu-id="68d1d-131">元素</span><span class="sxs-lookup"><span data-stu-id="68d1d-131">Element</span></span>|<span data-ttu-id="68d1d-132">描述</span><span class="sxs-lookup"><span data-stu-id="68d1d-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="68d1d-133">指定对等节点的当前凭据。</span><span class="sxs-lookup"><span data-stu-id="68d1d-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68d1d-134">注解</span><span class="sxs-lookup"><span data-stu-id="68d1d-134">Remarks</span></span>  
 <span data-ttu-id="68d1d-135">`<authentication>` 元素与 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 类相对应。</span><span class="sxs-lookup"><span data-stu-id="68d1d-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="68d1d-136">此元素指定一个验证程序，在网格中执行邻居对等身份验证的过程中将调用该验证程序。</span><span class="sxs-lookup"><span data-stu-id="68d1d-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="68d1d-137">当新对等方尝试建立邻居连接时，它会将自己的凭据传递到响应的对等方。</span><span class="sxs-lookup"><span data-stu-id="68d1d-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="68d1d-138">将调用响应方的验证程序来验证远程方的凭据。</span><span class="sxs-lookup"><span data-stu-id="68d1d-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="68d1d-139">每当在网格中建立对等连接时，对等方将会相互进行身份验证，这意味着会同时在两方调用验证程序。</span><span class="sxs-lookup"><span data-stu-id="68d1d-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d1d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68d1d-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="68d1d-141">使用证书</span><span class="sxs-lookup"><span data-stu-id="68d1d-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="68d1d-142">对等网络</span><span class="sxs-lookup"><span data-stu-id="68d1d-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="68d1d-143">[对等通道消息身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="68d1d-143">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="68d1d-144">[对等通道自定义身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="68d1d-144">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="68d1d-145">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="68d1d-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
