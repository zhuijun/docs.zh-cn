---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 9991430f09cb6a63d0a3cdde24a4ff03d3dd746d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165047"
---
# \<issuerNameRegistry>

<span data-ttu-id="4da54-101">配置标记处理程序集合中的处理程序使用的颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="4da54-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="4da54-102">语法</span><span class="sxs-lookup"><span data-stu-id="4da54-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4da54-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4da54-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4da54-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4da54-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4da54-105">特性</span><span class="sxs-lookup"><span data-stu-id="4da54-105">Attributes</span></span>  
  
|<span data-ttu-id="4da54-106">属性</span><span class="sxs-lookup"><span data-stu-id="4da54-106">Attribute</span></span>|<span data-ttu-id="4da54-107">说明</span><span class="sxs-lookup"><span data-stu-id="4da54-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4da54-108">type</span><span class="sxs-lookup"><span data-stu-id="4da54-108">type</span></span>|<span data-ttu-id="4da54-109">派生自类的类型 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="4da54-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="4da54-110">有关如何指定自定义的详细信息 `type` ，请参阅 [自定义类型引用]。</span><span class="sxs-lookup"><span data-stu-id="4da54-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4da54-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4da54-111">Child Elements</span></span>  
  
|<span data-ttu-id="4da54-112">元素</span><span class="sxs-lookup"><span data-stu-id="4da54-112">Element</span></span>|<span data-ttu-id="4da54-113">描述</span><span class="sxs-lookup"><span data-stu-id="4da54-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="4da54-114">当 `type` 属性指定基于配置的颁发者名称注册表 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 类) 时， [\<trustedIssuers>](trustedissuers.md) 必须指定元素。</span><span class="sxs-lookup"><span data-stu-id="4da54-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="4da54-115">[\<trustedIssuers>](trustedissuers.md)元素可以将 `<add>` 、 `<clear>` 或 `<remove>` 元素作为子元素。</span><span class="sxs-lookup"><span data-stu-id="4da54-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4da54-116">父元素</span><span class="sxs-lookup"><span data-stu-id="4da54-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4da54-117">元素</span><span class="sxs-lookup"><span data-stu-id="4da54-117">Element</span></span>|<span data-ttu-id="4da54-118">描述</span><span class="sxs-lookup"><span data-stu-id="4da54-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="4da54-119">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="4da54-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4da54-120">备注</span><span class="sxs-lookup"><span data-stu-id="4da54-120">Remarks</span></span>  

 <span data-ttu-id="4da54-121">使用颁发者名称注册表验证所有颁发者令牌。</span><span class="sxs-lookup"><span data-stu-id="4da54-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="4da54-122">这是从类派生的对象 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="4da54-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="4da54-123">颁发者名称注册表用于将助记键名称关联到验证相应颁发者生成的令牌签名所需的加密材料。</span><span class="sxs-lookup"><span data-stu-id="4da54-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="4da54-124">颁发者名称注册表维护依赖方 (RP) 应用程序信任的颁发者的列表。</span><span class="sxs-lookup"><span data-stu-id="4da54-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="4da54-125">颁发者名称注册表的类型是使用属性指定的 `type` 。</span><span class="sxs-lookup"><span data-stu-id="4da54-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="4da54-126">`<issuerNameRegistry>`元素可以有一个或多个子元素，这些子元素提供指定类型的配置。</span><span class="sxs-lookup"><span data-stu-id="4da54-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="4da54-127">通过重写方法来提供处理这些子元素的逻辑 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4da54-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="4da54-128">WIF 提供单一颁发者名称注册表类型，即 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 类。</span><span class="sxs-lookup"><span data-stu-id="4da54-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="4da54-129">此类使用在配置中指定的一组受信任的颁发者证书。</span><span class="sxs-lookup"><span data-stu-id="4da54-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="4da54-130">它需要一个子配置元素， `<trustedIssuers>` 在该元素下配置受信任的颁发者证书的集合。</span><span class="sxs-lookup"><span data-stu-id="4da54-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="4da54-131">受信任的证书是使用 "证书指纹" 的 "ASN" 编码形式指定的，并且通过使用 `<add>` 、或元素在集合中添加或删除 `<clear>` `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="4da54-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="4da54-132">`<issuerNameRegistry>`元素由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="4da54-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4da54-133">将 `<issuerNameRegistry>` 元素指定为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已不推荐使用，但仍支持向后兼容。</span><span class="sxs-lookup"><span data-stu-id="4da54-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="4da54-134">元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="4da54-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4da54-135">示例</span><span class="sxs-lookup"><span data-stu-id="4da54-135">Example</span></span>  

 <span data-ttu-id="4da54-136">下面的 XML 演示如何指定基于配置的颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="4da54-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4da54-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="4da54-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
