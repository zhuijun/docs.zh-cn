---
title: 如何：创建支持凭据
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: b181ac72c9f197e9e404f7aa0f04e254abac10da
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557393"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="e8bbb-102">如何：创建支持凭据</span><span class="sxs-lookup"><span data-stu-id="e8bbb-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="e8bbb-103">自定义安全方案可能要求提供多个凭据。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="e8bbb-104">例如，某个服务可能要求客户端不仅提供用户名和密码，还要提供能够证明客户端用户已满 18 岁的凭据。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="e8bbb-105">第二个凭据是 *支持凭据*。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="e8bbb-106">本主题说明如何在 Windows Communication Foundation (WCF) 客户端中实现此类凭据。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8bbb-107">支持凭据的规范是 WS-SecurityPolicy 规范的一部分。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="e8bbb-108">有关详细信息，请参阅 [Web Services 安全性规范](/previous-versions/dotnet/articles/ms951273(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-108">For more information, see [Web Services Security Specifications](/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="e8bbb-109">支持令牌</span><span class="sxs-lookup"><span data-stu-id="e8bbb-109">Supporting Tokens</span></span>  
 <span data-ttu-id="e8bbb-110">简而言之，使用消息安全性时，始终使用 *主凭据* 来保护消息 (例如，x.509 证书或 Kerberos 票证) 。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="e8bbb-111">根据规范的定义，安全绑定使用 *令牌* 来保护消息交换。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="e8bbb-112">*令牌*是安全凭据的表示形式。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="e8bbb-113">安全绑定使用在安全绑定策略中标识的主令牌来创建签名。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="e8bbb-114">此签名称为 *消息签名*。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="e8bbb-115">还可以指定其他令牌，以扩充与消息签名相关联的令牌所提供的声明。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="e8bbb-116">认可、签名和加密</span><span class="sxs-lookup"><span data-stu-id="e8bbb-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="e8bbb-117">支持凭据会导致在消息内传输 *支持令牌* 。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="e8bbb-118">WS-SecurityPolicy 规范定义了四种将支持令牌附加到消息的方法，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="e8bbb-119">目的</span><span class="sxs-lookup"><span data-stu-id="e8bbb-119">Purpose</span></span>|<span data-ttu-id="e8bbb-120">说明</span><span class="sxs-lookup"><span data-stu-id="e8bbb-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8bbb-121">有符号</span><span class="sxs-lookup"><span data-stu-id="e8bbb-121">Signed</span></span>|<span data-ttu-id="e8bbb-122">支持令牌包含在安全标头中，并由消息签名进行签名。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="e8bbb-123">认可</span><span class="sxs-lookup"><span data-stu-id="e8bbb-123">Endorsing</span></span>|<span data-ttu-id="e8bbb-124">*认可令牌*对消息签名进行签名。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="e8bbb-125">签名和认可</span><span class="sxs-lookup"><span data-stu-id="e8bbb-125">Signed and Endorsing</span></span>|<span data-ttu-id="e8bbb-126">签名的认可令牌对从消息签名生成的整个 `ds:Signature` 元素进行签名，并由该消息签名对自己进行签名；也就是说，两种令牌（用于消息签名的令牌和已签名的认可令牌）互相进行签名。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="e8bbb-127">签名和加密</span><span class="sxs-lookup"><span data-stu-id="e8bbb-127">Signed and Encrypting</span></span>|<span data-ttu-id="e8bbb-128">签名的加密支持令牌是在 `wsse:SecurityHeader` 中出现时还进行加密的签名支持令牌。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="e8bbb-129">对支持凭据进行编程</span><span class="sxs-lookup"><span data-stu-id="e8bbb-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="e8bbb-130">若要创建使用支持令牌的服务，必须创建 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="e8bbb-131"> (有关详细信息，请参阅 [如何：使用 SecurityBindingElement 创建自定义绑定](how-to-create-a-custom-binding-using-the-securitybindingelement.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="e8bbb-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="e8bbb-132">创建自定义绑定的第一步是创建一个安全绑定元素，该元素可以是以下三种类型之一：</span><span class="sxs-lookup"><span data-stu-id="e8bbb-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="e8bbb-133">所有类都继承自 <xref:System.ServiceModel.Channels.SecurityBindingElement>，它包含四个相关属性：</span><span class="sxs-lookup"><span data-stu-id="e8bbb-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="e8bbb-134">作用域</span><span class="sxs-lookup"><span data-stu-id="e8bbb-134">Scopes</span></span>  
 <span data-ttu-id="e8bbb-135">支持凭据存在两个范围：</span><span class="sxs-lookup"><span data-stu-id="e8bbb-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="e8bbb-136">支持*令牌的终结*点支持终结点的所有操作。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="e8bbb-137">即，每当调用任何终结点操作，都可以使用该支持令牌表示的凭据。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="e8bbb-138">支持*令牌的操作*仅支持特定的终结点操作。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="e8bbb-139">正如属性名所指示的那样，支持凭据可能是必需的，也可能是可选的。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="e8bbb-140">即，如果支持凭据存在，则使用支持凭据（尽管不是必需的），但如果支持凭据不存在，身份验证也不会失败。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e8bbb-141">过程</span><span class="sxs-lookup"><span data-stu-id="e8bbb-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="e8bbb-142">创建一个包含支持凭据的自定义绑定</span><span class="sxs-lookup"><span data-stu-id="e8bbb-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="e8bbb-143">创建一个安全绑定元素。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-143">Create a security binding element.</span></span> <span data-ttu-id="e8bbb-144">下面的示例创建一个 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>，该元素具有 `UserNameForCertificate` 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="e8bbb-145">使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="e8bbb-146">将支持参数添加到由适当的属性（`Endorsing`、`Signed`、`SignedEncrypted` 或 `SignedEndorsed`）返回的类型集合中。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="e8bbb-147"><xref:System.ServiceModel.Security.Tokens> 命名空间中的类型包括常用类型，如 <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8bbb-148">示例</span><span class="sxs-lookup"><span data-stu-id="e8bbb-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e8bbb-149">说明</span><span class="sxs-lookup"><span data-stu-id="e8bbb-149">Description</span></span>  
 <span data-ttu-id="e8bbb-150">下面的示例创建 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的一个实例，并将 <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> 类的一个实例添加到 Endorsing 属性返回的集合中。</span><span class="sxs-lookup"><span data-stu-id="e8bbb-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e8bbb-151">代码</span><span class="sxs-lookup"><span data-stu-id="e8bbb-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8bbb-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8bbb-152">See also</span></span>

- [<span data-ttu-id="e8bbb-153">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="e8bbb-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
