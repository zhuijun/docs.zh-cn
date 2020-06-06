---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251969"
---
# \<issuerNameRegistry>
<span data-ttu-id="cd582-101">配置标记处理程序集合中的处理程序使用的颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="cd582-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="cd582-102">语法</span><span class="sxs-lookup"><span data-stu-id="cd582-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd582-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd582-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cd582-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd582-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd582-105">特性</span><span class="sxs-lookup"><span data-stu-id="cd582-105">Attributes</span></span>  
  
|<span data-ttu-id="cd582-106">属性</span><span class="sxs-lookup"><span data-stu-id="cd582-106">Attribute</span></span>|<span data-ttu-id="cd582-107">说明</span><span class="sxs-lookup"><span data-stu-id="cd582-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd582-108">type</span><span class="sxs-lookup"><span data-stu-id="cd582-108">type</span></span>|<span data-ttu-id="cd582-109">派生自类的类型 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="cd582-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="cd582-110">有关如何指定自定义的详细信息 `type` ，请参阅 [自定义类型引用]。</span><span class="sxs-lookup"><span data-stu-id="cd582-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd582-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cd582-111">Child Elements</span></span>  
  
|<span data-ttu-id="cd582-112">元素</span><span class="sxs-lookup"><span data-stu-id="cd582-112">Element</span></span>|<span data-ttu-id="cd582-113">描述</span><span class="sxs-lookup"><span data-stu-id="cd582-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="cd582-114">当 `type` 属性指定基于配置的颁发者名称注册表（ <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 类）时， [\<trustedIssuers>](trustedissuers.md) 必须指定元素。</span><span class="sxs-lookup"><span data-stu-id="cd582-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="cd582-115">[\<trustedIssuers>](trustedissuers.md)元素可以将 `<add>` 、 `<clear>` 或 `<remove>` 元素作为子元素。</span><span class="sxs-lookup"><span data-stu-id="cd582-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd582-116">父元素</span><span class="sxs-lookup"><span data-stu-id="cd582-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cd582-117">元素</span><span class="sxs-lookup"><span data-stu-id="cd582-117">Element</span></span>|<span data-ttu-id="cd582-118">描述</span><span class="sxs-lookup"><span data-stu-id="cd582-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="cd582-119">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="cd582-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd582-120">注解</span><span class="sxs-lookup"><span data-stu-id="cd582-120">Remarks</span></span>  
 <span data-ttu-id="cd582-121">使用颁发者名称注册表验证所有颁发者令牌。</span><span class="sxs-lookup"><span data-stu-id="cd582-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="cd582-122">这是从类派生的对象 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="cd582-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="cd582-123">颁发者名称注册表用于将助记键名称关联到验证相应颁发者生成的令牌签名所需的加密材料。</span><span class="sxs-lookup"><span data-stu-id="cd582-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="cd582-124">颁发者名称注册表将维护依赖方（RP）应用程序信任的颁发者的列表。</span><span class="sxs-lookup"><span data-stu-id="cd582-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="cd582-125">颁发者名称注册表的类型是使用属性指定的 `type` 。</span><span class="sxs-lookup"><span data-stu-id="cd582-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="cd582-126">`<issuerNameRegistry>`元素可以有一个或多个子元素，这些子元素提供指定类型的配置。</span><span class="sxs-lookup"><span data-stu-id="cd582-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="cd582-127">通过重写方法来提供处理这些子元素的逻辑 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="cd582-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="cd582-128">WIF 提供单一颁发者名称注册表类型，即 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 类。</span><span class="sxs-lookup"><span data-stu-id="cd582-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="cd582-129">此类使用在配置中指定的一组受信任的颁发者证书。</span><span class="sxs-lookup"><span data-stu-id="cd582-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="cd582-130">它需要一个子配置元素， `<trustedIssuers>` 在该元素下配置受信任的颁发者证书的集合。</span><span class="sxs-lookup"><span data-stu-id="cd582-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="cd582-131">受信任的证书是使用 "证书指纹" 的 "ASN" 编码形式指定的，并且通过使用 `<add>` 、或元素在集合中添加或删除 `<clear>` `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="cd582-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="cd582-132">`<issuerNameRegistry>`元素由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="cd582-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd582-133">将 `<issuerNameRegistry>` 元素指定为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已不推荐使用，但仍支持向后兼容。</span><span class="sxs-lookup"><span data-stu-id="cd582-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="cd582-134">元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="cd582-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd582-135">示例</span><span class="sxs-lookup"><span data-stu-id="cd582-135">Example</span></span>  
 <span data-ttu-id="cd582-136">下面的 XML 演示如何指定基于配置的颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="cd582-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd582-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd582-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
