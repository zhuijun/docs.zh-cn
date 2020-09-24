---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 1a231a60d29cc6a4460de69a98753c23c0386027
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170033"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="ad3c4-102">\<security> 的 \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="ad3c4-102">\<security> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="ad3c4-103">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="ad3c4-104">语法</span><span class="sxs-lookup"><span data-stu-id="ad3c4-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad3c4-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ad3c4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ad3c4-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad3c4-107">特性</span><span class="sxs-lookup"><span data-stu-id="ad3c4-107">Attributes</span></span>  
  
|<span data-ttu-id="ad3c4-108">属性</span><span class="sxs-lookup"><span data-stu-id="ad3c4-108">Attribute</span></span>|<span data-ttu-id="ad3c4-109">描述</span><span class="sxs-lookup"><span data-stu-id="ad3c4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad3c4-110">mode</span><span class="sxs-lookup"><span data-stu-id="ad3c4-110">mode</span></span>|<span data-ttu-id="ad3c4-111">指定应用于此绑定的安全类型。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="ad3c4-112">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="ad3c4-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ad3c4-113">-None：这将禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-113">-   None: This disables security.</span></span><br /><span data-ttu-id="ad3c4-114">-Transport：使用基于传输的基础安全性提供安全性。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="ad3c4-115">可以使用此模式控制保护级别。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="ad3c4-116">-默认值为 Transport。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-116">-   The default value is Transport.</span></span> <span data-ttu-id="ad3c4-117">此属性的类型为 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad3c4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ad3c4-118">Child Elements</span></span>  
  
|<span data-ttu-id="ad3c4-119">元素</span><span class="sxs-lookup"><span data-stu-id="ad3c4-119">Element</span></span>|<span data-ttu-id="ad3c4-120">描述</span><span class="sxs-lookup"><span data-stu-id="ad3c4-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad3c4-121">运输</span><span class="sxs-lookup"><span data-stu-id="ad3c4-121">transport</span></span>|<span data-ttu-id="ad3c4-122">定义传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="ad3c4-123">此元素的类型为 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad3c4-124">父元素</span><span class="sxs-lookup"><span data-stu-id="ad3c4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ad3c4-125">元素</span><span class="sxs-lookup"><span data-stu-id="ad3c4-125">Element</span></span>|<span data-ttu-id="ad3c4-126">描述</span><span class="sxs-lookup"><span data-stu-id="ad3c4-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad3c4-127">binding</span><span class="sxs-lookup"><span data-stu-id="ad3c4-127">binding</span></span>|<span data-ttu-id="ad3c4-128">的绑定元素 [\<netNamedPipeBinding>](netnamedpipebinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="ad3c4-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad3c4-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad3c4-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="ad3c4-130">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="ad3c4-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ad3c4-131">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="ad3c4-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ad3c4-132">绑定</span><span class="sxs-lookup"><span data-stu-id="ad3c4-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ad3c4-133">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="ad3c4-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ad3c4-134">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="ad3c4-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
