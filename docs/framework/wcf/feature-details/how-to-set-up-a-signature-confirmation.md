---
title: 如何：设置签名确认
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586905"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="8c686-102">如何：设置签名确认</span><span class="sxs-lookup"><span data-stu-id="8c686-102">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="8c686-103">*签名确认*是一种机制，用于消息发起方确保收到的答复是为了响应发送方的原始消息。</span><span class="sxs-lookup"><span data-stu-id="8c686-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="8c686-104">WS-Security 1.1 规范中对签名确认进行了定义。</span><span class="sxs-lookup"><span data-stu-id="8c686-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="8c686-105">如果终结点支持 WS-Security 1.0，则不能使用签名确认。</span><span class="sxs-lookup"><span data-stu-id="8c686-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="8c686-106">下面的过程指定如何使用 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 来启用签名确认。</span><span class="sxs-lookup"><span data-stu-id="8c686-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="8c686-107">可以对 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 使用相同的过程。</span><span class="sxs-lookup"><span data-stu-id="8c686-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="8c686-108">此过程基于[如何：使用 SecurityBindingElement 创建自定义绑定](how-to-create-a-custom-binding-using-the-securitybindingelement.md)中的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="8c686-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="8c686-109">在代码中启用签名确认</span><span class="sxs-lookup"><span data-stu-id="8c686-109">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="8c686-110">创建 <xref:System.ServiceModel.Channels.BindingElementCollection> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="8c686-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="8c686-111">创建类的实例 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 。</span><span class="sxs-lookup"><span data-stu-id="8c686-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="8c686-112">将 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8c686-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="8c686-113">将安全元素添加到绑定集合中。</span><span class="sxs-lookup"><span data-stu-id="8c686-113">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="8c686-114">按照[如何：使用 SecurityBindingElement 创建自定义绑定](how-to-create-a-custom-binding-using-the-securitybindingelement.md)中的说明创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="8c686-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="8c686-115">在配置中启用签名确认</span><span class="sxs-lookup"><span data-stu-id="8c686-115">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="8c686-116">将 `<customBinding>` 元素添加到配置文件的 `<bindings>` 节。</span><span class="sxs-lookup"><span data-stu-id="8c686-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="8c686-117">添加一个 `<binding>` 元素，并将 name 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="8c686-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="8c686-118">添加一个适当的编码元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="8c686-119">下面的示例添加了一个 `<TextMessageEncoding>` 元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-119">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="8c686-120">添加一个 `<security>` 子元素并将 `requireSignatureConfirmation` 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8c686-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="8c686-121">可选。</span><span class="sxs-lookup"><span data-stu-id="8c686-121">Optional.</span></span> <span data-ttu-id="8c686-122">若要在启动过程中启用签名确认，请添加一个 [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 子元素，并将 `requireSignatureConfirmation` 属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="8c686-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="8c686-123">添加一个适当的传输元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-123">Add an appropriate transport element.</span></span> <span data-ttu-id="8c686-124">下面的示例添加一个 [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) ：</span><span class="sxs-lookup"><span data-stu-id="8c686-124">The following example adds an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md):</span></span>

    ```xml
    <bindings>
      <customBinding>
        <binding name="SignatureConfirmationBinding">
          <security requireSignatureConfirmation="true">
            <secureConversationBootstrap requireSignatureConfirmation="true" />
              </security>
           <textMessageEncoding />
             <httpTransport />
        </binding>
      </customBinding>
    </bindings>
    ```

## <a name="example"></a><span data-ttu-id="8c686-125">示例</span><span class="sxs-lookup"><span data-stu-id="8c686-125">Example</span></span>

<span data-ttu-id="8c686-126">下面的代码创建 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的实例并将 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8c686-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="8c686-127">请注意，此示例不使用上一示例中所示的 `<secureConversationBootstrap>` 元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="8c686-128">此示例演示了使用 Windows（Kerberos 协议）令牌时的签名确认。</span><span class="sxs-lookup"><span data-stu-id="8c686-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="8c686-129">在本例中，在来自服务的所有响应中均返回客户端的签名，并且该签名由客户端进行确认。</span><span class="sxs-lookup"><span data-stu-id="8c686-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="8c686-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c686-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="8c686-131">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="8c686-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="8c686-132">如何：为指定的身份验证模式创建 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8c686-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
