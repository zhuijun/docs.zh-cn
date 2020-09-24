---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 7398cd538bb240e78413575f7c28abe7f797d05c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162200"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="4557a-102">\<security> 的 \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4557a-102">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="4557a-103">定义的安全功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="4557a-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="4557a-104">语法</span><span class="sxs-lookup"><span data-stu-id="4557a-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4557a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4557a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4557a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4557a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4557a-107">特性</span><span class="sxs-lookup"><span data-stu-id="4557a-107">Attributes</span></span>  
  
|<span data-ttu-id="4557a-108">属性</span><span class="sxs-lookup"><span data-stu-id="4557a-108">Attribute</span></span>|<span data-ttu-id="4557a-109">描述</span><span class="sxs-lookup"><span data-stu-id="4557a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4557a-110">mode</span><span class="sxs-lookup"><span data-stu-id="4557a-110">mode</span></span>|<span data-ttu-id="4557a-111">可有可无.</span><span class="sxs-lookup"><span data-stu-id="4557a-111">-   Optional.</span></span> <span data-ttu-id="4557a-112">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="4557a-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="4557a-113">默认值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="4557a-113">The default value is `Message`.</span></span> <span data-ttu-id="4557a-114">此属性的类型为 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="4557a-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4557a-115">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="4557a-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="4557a-116">值</span><span class="sxs-lookup"><span data-stu-id="4557a-116">Value</span></span>|<span data-ttu-id="4557a-117">描述</span><span class="sxs-lookup"><span data-stu-id="4557a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4557a-118">无</span><span class="sxs-lookup"><span data-stu-id="4557a-118">None</span></span>|<span data-ttu-id="4557a-119">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="4557a-119">Security is disabled.</span></span>|  
|<span data-ttu-id="4557a-120">消息</span><span class="sxs-lookup"><span data-stu-id="4557a-120">Message</span></span>|<span data-ttu-id="4557a-121">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="4557a-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4557a-122">子元素</span><span class="sxs-lookup"><span data-stu-id="4557a-122">Child Elements</span></span>  
  
|<span data-ttu-id="4557a-123">元素</span><span class="sxs-lookup"><span data-stu-id="4557a-123">Element</span></span>|<span data-ttu-id="4557a-124">描述</span><span class="sxs-lookup"><span data-stu-id="4557a-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="4557a-125">定义消息级安全性设置。</span><span class="sxs-lookup"><span data-stu-id="4557a-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="4557a-126">此元素的类型为 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="4557a-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4557a-127">父元素</span><span class="sxs-lookup"><span data-stu-id="4557a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4557a-128">元素</span><span class="sxs-lookup"><span data-stu-id="4557a-128">Element</span></span>|<span data-ttu-id="4557a-129">描述</span><span class="sxs-lookup"><span data-stu-id="4557a-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4557a-130">定义的所有绑定功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="4557a-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4557a-131">备注</span><span class="sxs-lookup"><span data-stu-id="4557a-131">Remarks</span></span>  

 <span data-ttu-id="4557a-132">双向绑定向服务公开客户端的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="4557a-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="4557a-133">客户端应使用安全来确保仅连接到自己信任的服务。</span><span class="sxs-lookup"><span data-stu-id="4557a-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4557a-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="4557a-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="4557a-135">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="4557a-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4557a-136">绑定</span><span class="sxs-lookup"><span data-stu-id="4557a-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4557a-137">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="4557a-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4557a-138">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="4557a-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
