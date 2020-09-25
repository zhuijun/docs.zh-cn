---
title: <messageSenderAuthentication> 元素
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: e7e636571c0dbb1845438c22f7e7509dfc7987f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204783"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="89a1f-102">\<messageSenderAuthentication> 元素</span><span class="sxs-lookup"><span data-stu-id="89a1f-102">\<messageSenderAuthentication> element</span></span>

<span data-ttu-id="89a1f-103">指定用于对等消息发送方的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="89a1f-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="89a1f-104">有关对等编程的详细信息，请参阅对等 [网络](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="89a1f-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="89a1f-105">语法</span><span class="sxs-lookup"><span data-stu-id="89a1f-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89a1f-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="89a1f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="89a1f-107">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="89a1f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89a1f-108">特性</span><span class="sxs-lookup"><span data-stu-id="89a1f-108">Attributes</span></span>  
  
|<span data-ttu-id="89a1f-109">属性</span><span class="sxs-lookup"><span data-stu-id="89a1f-109">Attribute</span></span>|<span data-ttu-id="89a1f-110">描述</span><span class="sxs-lookup"><span data-stu-id="89a1f-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="89a1f-111">一个用于验证自定义类型的类型和程序集。</span><span class="sxs-lookup"><span data-stu-id="89a1f-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="89a1f-112">当 `certificateValidationMode` 设置为 `Custom` 时，必须设置此属性。</span><span class="sxs-lookup"><span data-stu-id="89a1f-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="89a1f-113">指定用来验证凭据的三种模式之一。</span><span class="sxs-lookup"><span data-stu-id="89a1f-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="89a1f-114">如果设置为 `Custom`，则还必须提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="89a1f-115">用于检查吊销证书列表 (CRL) 的一种模式。</span><span class="sxs-lookup"><span data-stu-id="89a1f-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="89a1f-116">两个系统存储位置之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="89a1f-117">在向客户端协商服务证书时使用此值。</span><span class="sxs-lookup"><span data-stu-id="89a1f-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="89a1f-118">针对指定存储位置中的 " **受信任人** " 存储执行验证。</span><span class="sxs-lookup"><span data-stu-id="89a1f-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="89a1f-119">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="89a1f-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="89a1f-120">值</span><span class="sxs-lookup"><span data-stu-id="89a1f-120">Value</span></span>|<span data-ttu-id="89a1f-121">说明</span><span class="sxs-lookup"><span data-stu-id="89a1f-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89a1f-122">字符串</span><span class="sxs-lookup"><span data-stu-id="89a1f-122">String</span></span>|<span data-ttu-id="89a1f-123">可选。</span><span class="sxs-lookup"><span data-stu-id="89a1f-123">Optional.</span></span> <span data-ttu-id="89a1f-124">指定类型名称和程序集以及用于查找类型的其他数据。</span><span class="sxs-lookup"><span data-stu-id="89a1f-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="89a1f-125">至少需要命名空间和类型名称。</span><span class="sxs-lookup"><span data-stu-id="89a1f-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="89a1f-126">可选信息包括：程序集名称、版本号、区域性和公钥标记。</span><span class="sxs-lookup"><span data-stu-id="89a1f-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="89a1f-127">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="89a1f-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="89a1f-128">值</span><span class="sxs-lookup"><span data-stu-id="89a1f-128">Value</span></span>|<span data-ttu-id="89a1f-129">描述</span><span class="sxs-lookup"><span data-stu-id="89a1f-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89a1f-130">枚举</span><span class="sxs-lookup"><span data-stu-id="89a1f-130">Enumeration</span></span>|<span data-ttu-id="89a1f-131">可选。</span><span class="sxs-lookup"><span data-stu-id="89a1f-131">Optional.</span></span> <span data-ttu-id="89a1f-132">下列值之一：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust` 和 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="89a1f-133">默认为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="89a1f-134">默认为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="89a1f-135">有关详细信息，请参阅使用 [证书](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="89a1f-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="89a1f-136">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="89a1f-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="89a1f-137">值</span><span class="sxs-lookup"><span data-stu-id="89a1f-137">Value</span></span>|<span data-ttu-id="89a1f-138">描述</span><span class="sxs-lookup"><span data-stu-id="89a1f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89a1f-139">枚举</span><span class="sxs-lookup"><span data-stu-id="89a1f-139">Enumeration</span></span>|<span data-ttu-id="89a1f-140">下列值之一：`NoCheck`、`Online` 和 `Offline`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="89a1f-141">默认为 `Online`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="89a1f-142">有关详细信息，请参阅使用 [证书](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="89a1f-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="89a1f-143">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="89a1f-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="89a1f-144">值</span><span class="sxs-lookup"><span data-stu-id="89a1f-144">Value</span></span>|<span data-ttu-id="89a1f-145">描述</span><span class="sxs-lookup"><span data-stu-id="89a1f-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89a1f-146">枚举</span><span class="sxs-lookup"><span data-stu-id="89a1f-146">Enumeration</span></span>|<span data-ttu-id="89a1f-147">以下值之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="89a1f-148">默认为 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="89a1f-149">如果客户端应用程序在系统帐户下运行，则证书通常位于 `LocalMachine`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="89a1f-150">如果客户端应用程序在用户帐户下运行，则证书通常位于 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="89a1f-151">默认为 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89a1f-152">子元素</span><span class="sxs-lookup"><span data-stu-id="89a1f-152">Child Elements</span></span>  

 <span data-ttu-id="89a1f-153">无。</span><span class="sxs-lookup"><span data-stu-id="89a1f-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89a1f-154">父元素</span><span class="sxs-lookup"><span data-stu-id="89a1f-154">Parent Elements</span></span>  
  
|<span data-ttu-id="89a1f-155">元素</span><span class="sxs-lookup"><span data-stu-id="89a1f-155">Element</span></span>|<span data-ttu-id="89a1f-156">描述</span><span class="sxs-lookup"><span data-stu-id="89a1f-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="89a1f-157">指定一个用于向对等服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="89a1f-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89a1f-158">备注</span><span class="sxs-lookup"><span data-stu-id="89a1f-158">Remarks</span></span>  

 <span data-ttu-id="89a1f-159">如果选择了消息身份验证，则必须配置此元素。</span><span class="sxs-lookup"><span data-stu-id="89a1f-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="89a1f-160">对于输出通道，每条消息都使用提供的证书进行签名 [\<certificate>](certificate-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="89a1f-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="89a1f-161">在将任一消息传递到应用程序之前，都会使用由此元素的 `customCertificateValidatorType` 属性指定的验证程序对照消息凭据对其进行检查。</span><span class="sxs-lookup"><span data-stu-id="89a1f-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="89a1f-162">验证程序可以接受或拒绝凭据。</span><span class="sxs-lookup"><span data-stu-id="89a1f-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89a1f-163">示例</span><span class="sxs-lookup"><span data-stu-id="89a1f-163">Example</span></span>  

 <span data-ttu-id="89a1f-164">下面的代码将消息发送方验证模式设置为 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="89a1f-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="89a1f-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="89a1f-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="89a1f-166">使用证书</span><span class="sxs-lookup"><span data-stu-id="89a1f-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="89a1f-167">对等网络</span><span class="sxs-lookup"><span data-stu-id="89a1f-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="89a1f-168">[对等通道消息身份验证](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="89a1f-168">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="89a1f-169">[对等通道自定义身份验证](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="89a1f-169">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="89a1f-170">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="89a1f-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
