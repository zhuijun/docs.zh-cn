---
title: <message> 的元素 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: ab767a5a1179de81bf9a8adc61799ede2d915ac1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204900"
---
# <a name="message-element-of-nettcpbinding"></a><span data-ttu-id="cd02a-102">\<message> 的元素 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="cd02a-102">\<message> element of \<netTcpBinding></span></span>

<span data-ttu-id="cd02a-103">为使用配置的终结点定义消息级安全性要求的类型 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="cd02a-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="cd02a-104">语法</span><span class="sxs-lookup"><span data-stu-id="cd02a-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd02a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd02a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cd02a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd02a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd02a-107">特性</span><span class="sxs-lookup"><span data-stu-id="cd02a-107">Attributes</span></span>  
  
|<span data-ttu-id="cd02a-108">属性</span><span class="sxs-lookup"><span data-stu-id="cd02a-108">Attribute</span></span>|<span data-ttu-id="cd02a-109">描述</span><span class="sxs-lookup"><span data-stu-id="cd02a-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="cd02a-110">设置消息加密和密钥包装算法。</span><span class="sxs-lookup"><span data-stu-id="cd02a-110">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="cd02a-111">算法和密钥大小由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 类确定。</span><span class="sxs-lookup"><span data-stu-id="cd02a-111">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="cd02a-112">这些算法与“安全策略语言”(WS-SecurityPolicy) 规范中指定的算法一致。</span><span class="sxs-lookup"><span data-stu-id="cd02a-112">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="cd02a-113">下表中显示了可能的值。</span><span class="sxs-lookup"><span data-stu-id="cd02a-113">Possible values are shown in the following table.</span></span> <span data-ttu-id="cd02a-114">默认值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="cd02a-114">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="cd02a-115">如果服务绑定指定的 `algorithmSuite` 值不等于默认值，并且你使用 Svcutil.exe 生成配置文件，则不会正确生成该文件，你必须手动编辑此配置文件，将此属性设置为所需的值。</span><span class="sxs-lookup"><span data-stu-id="cd02a-115">If the service binding specifies an `algorithmSuite` value that is not equal to the default, and you generate the configuration file using Svcutil.exe, then it is not generated correctly, and you must manually edit the configuration file to set this attribute to the desired value.</span></span>|  
|`clientCredentialType`|<span data-ttu-id="cd02a-116">指定要在使用基于消息的安全性执行客户端身份验证时使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="cd02a-116">Specifies the type of credential to be used when performing client authentication using Message-based security.</span></span> <span data-ttu-id="cd02a-117">下表中显示了可能的值。</span><span class="sxs-lookup"><span data-stu-id="cd02a-117">Possible values are shown in the following table.</span></span> <span data-ttu-id="cd02a-118">默认值是 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="cd02a-118">The default value is `UserName`.</span></span> <span data-ttu-id="cd02a-119">此属性的类型为 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="cd02a-119">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="cd02a-120">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="cd02a-120">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="cd02a-121">值</span><span class="sxs-lookup"><span data-stu-id="cd02a-121">Value</span></span>|<span data-ttu-id="cd02a-122">描述</span><span class="sxs-lookup"><span data-stu-id="cd02a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd02a-123">Basic128</span><span class="sxs-lookup"><span data-stu-id="cd02a-123">Basic128</span></span>|<span data-ttu-id="cd02a-124">使用 Aes128 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-124">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-125">Basic192</span><span class="sxs-lookup"><span data-stu-id="cd02a-125">Basic192</span></span>|<span data-ttu-id="cd02a-126">使用 Aes192 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-126">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-127">Basic256</span><span class="sxs-lookup"><span data-stu-id="cd02a-127">Basic256</span></span>|<span data-ttu-id="cd02a-128">使用 Aes256 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-128">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-129">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-129">Basic256Rsa15</span></span>|<span data-ttu-id="cd02a-130">对消息加密使用 Aes256，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-130">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-131">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-131">Basic192Rsa15</span></span>|<span data-ttu-id="cd02a-132">对消息加密使用 Aes192，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-132">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-133">TripleDes</span><span class="sxs-lookup"><span data-stu-id="cd02a-133">TripleDes</span></span>|<span data-ttu-id="cd02a-134">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-134">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-135">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-135">Basic128Rsa15</span></span>|<span data-ttu-id="cd02a-136">对消息加密使用 Aes128，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-136">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-137">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-137">TripleDesRsa15</span></span>|<span data-ttu-id="cd02a-138">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-138">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-139">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="cd02a-139">Basic128Sha256</span></span>|<span data-ttu-id="cd02a-140">对消息加密使用 Aes256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-140">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-141">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="cd02a-141">Basic192Sha256</span></span>|<span data-ttu-id="cd02a-142">对消息加密使用 Aes192，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-142">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-143">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="cd02a-143">Basic256Sha256</span></span>|<span data-ttu-id="cd02a-144">对消息加密使用 Aes256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-144">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-145">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="cd02a-145">TripleDesSha256</span></span>|<span data-ttu-id="cd02a-146">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="cd02a-146">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-147">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-147">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="cd02a-148">对消息加密使用 Aes128，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-148">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-149">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-149">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="cd02a-150">对消息加密使用 Aes192，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-150">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-151">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-151">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="cd02a-152">对消息加密使用 Aes256，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-152">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd02a-153">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd02a-153">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="cd02a-154">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="cd02a-154">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="cd02a-155">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="cd02a-155">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="cd02a-156">值</span><span class="sxs-lookup"><span data-stu-id="cd02a-156">Value</span></span>|<span data-ttu-id="cd02a-157">描述</span><span class="sxs-lookup"><span data-stu-id="cd02a-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd02a-158">无</span><span class="sxs-lookup"><span data-stu-id="cd02a-158">None</span></span>|<span data-ttu-id="cd02a-159">允许服务与匿名客户端交互。</span><span class="sxs-lookup"><span data-stu-id="cd02a-159">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="cd02a-160">对于服务，这表示服务不需要任何客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="cd02a-160">On the service, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="cd02a-161">对于客户端，这表示客户端不提供任何客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="cd02a-161">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="cd02a-162">Windows</span><span class="sxs-lookup"><span data-stu-id="cd02a-162">Windows</span></span>|<span data-ttu-id="cd02a-163">允许 SOAP 交换在已通过身份验证的 Windows 凭据上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="cd02a-163">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span>|  
|<span data-ttu-id="cd02a-164">UserName</span><span class="sxs-lookup"><span data-stu-id="cd02a-164">UserName</span></span>|<span data-ttu-id="cd02a-165">允许服务要求使用 UserName 凭据对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="cd02a-165">Allows the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="cd02a-166">WCF 不支持发送密码摘要，也不支持使用密码派生密钥，然后用这些密钥来确保消息的安全性。</span><span class="sxs-lookup"><span data-stu-id="cd02a-166">WCF does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="cd02a-167">因此，在使用用户名凭据时，WCF 会强制保护传输。</span><span class="sxs-lookup"><span data-stu-id="cd02a-167">As such, WCF enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="cd02a-168">这种凭据模式将产生可互操作的交换或不可互操作的协商，具体取决于 `negotiateServiceCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="cd02a-168">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="cd02a-169">证书</span><span class="sxs-lookup"><span data-stu-id="cd02a-169">Certificate</span></span>|<span data-ttu-id="cd02a-170">允许服务要求使用证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="cd02a-170">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="cd02a-171">如果使用消息安全模式并且将 `negotiateServiceCredential` 属性设置为 `false`，则必须向客户端提供服务证书。</span><span class="sxs-lookup"><span data-stu-id="cd02a-171">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client must be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="cd02a-172">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="cd02a-172">IssuedToken</span></span>|<span data-ttu-id="cd02a-173">指定自定义令牌，该令牌通常由安全令牌服务 (STS) 颁发。</span><span class="sxs-lookup"><span data-stu-id="cd02a-173">Specifies a custom token, usually issued by a Security Token Service (STS).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd02a-174">子元素</span><span class="sxs-lookup"><span data-stu-id="cd02a-174">Child Elements</span></span>  

 <span data-ttu-id="cd02a-175">无</span><span class="sxs-lookup"><span data-stu-id="cd02a-175">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd02a-176">父元素</span><span class="sxs-lookup"><span data-stu-id="cd02a-176">Parent Elements</span></span>  
  
|<span data-ttu-id="cd02a-177">元素</span><span class="sxs-lookup"><span data-stu-id="cd02a-177">Element</span></span>|<span data-ttu-id="cd02a-178">描述</span><span class="sxs-lookup"><span data-stu-id="cd02a-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="cd02a-179">定义 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>的安全功能。</span><span class="sxs-lookup"><span data-stu-id="cd02a-179">Defines the security capabilities for the <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd02a-180">备注</span><span class="sxs-lookup"><span data-stu-id="cd02a-180">Remarks</span></span>  

 <span data-ttu-id="cd02a-181">消息使用消息级安全性实现 SOAP 消息的完整性和保密性，还用于通信对等方的相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="cd02a-181">Message uses message-level security for the integrity and confidentiality of the SOAP message, and for mutual authentication of the communication peers.</span></span> <span data-ttu-id="cd02a-182">如果在绑定上选择此安全模式，则使用消息安全性绑定元素配置信道堆栈，并且 SOAP 消息可按照 WS-Security\* 标准进行保护。</span><span class="sxs-lookup"><span data-stu-id="cd02a-182">If this security mode is selected on a binding, the channel stack is configured with message security binding elements and the SOAP messages are secured in compliance with WS-Security\* standards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd02a-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd02a-183">See also</span></span>

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="cd02a-184">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="cd02a-184">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cd02a-185">绑定</span><span class="sxs-lookup"><span data-stu-id="cd02a-185">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cd02a-186">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="cd02a-186">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cd02a-187">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="cd02a-187">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
