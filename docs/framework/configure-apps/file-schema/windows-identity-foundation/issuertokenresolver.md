---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 946ae8601e1e4563becd0b346b6c792724405a45
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165034"
---
# \<issuerTokenResolver>

<span data-ttu-id="99dec-101">注册由标记处理程序集合中的处理程序使用的颁发者令牌解析程序。</span><span class="sxs-lookup"><span data-stu-id="99dec-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="99dec-102">颁发者令牌解析器用于解析传入令牌和消息的签名令牌。</span><span class="sxs-lookup"><span data-stu-id="99dec-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="99dec-103">语法</span><span class="sxs-lookup"><span data-stu-id="99dec-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99dec-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="99dec-104">Attributes and Elements</span></span>  

 <span data-ttu-id="99dec-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="99dec-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99dec-106">特性</span><span class="sxs-lookup"><span data-stu-id="99dec-106">Attributes</span></span>  
  
|<span data-ttu-id="99dec-107">属性</span><span class="sxs-lookup"><span data-stu-id="99dec-107">Attribute</span></span>|<span data-ttu-id="99dec-108">说明</span><span class="sxs-lookup"><span data-stu-id="99dec-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99dec-109">type</span><span class="sxs-lookup"><span data-stu-id="99dec-109">type</span></span>|<span data-ttu-id="99dec-110">指定颁发者令牌解析程序的类型。</span><span class="sxs-lookup"><span data-stu-id="99dec-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="99dec-111">必须是 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 类或派生自类的类型 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="99dec-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="99dec-112">必需。</span><span class="sxs-lookup"><span data-stu-id="99dec-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99dec-113">子元素</span><span class="sxs-lookup"><span data-stu-id="99dec-113">Child Elements</span></span>  

 <span data-ttu-id="99dec-114">无</span><span class="sxs-lookup"><span data-stu-id="99dec-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99dec-115">父元素</span><span class="sxs-lookup"><span data-stu-id="99dec-115">Parent Elements</span></span>  
  
|<span data-ttu-id="99dec-116">元素</span><span class="sxs-lookup"><span data-stu-id="99dec-116">Element</span></span>|<span data-ttu-id="99dec-117">描述</span><span class="sxs-lookup"><span data-stu-id="99dec-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="99dec-118">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="99dec-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99dec-119">备注</span><span class="sxs-lookup"><span data-stu-id="99dec-119">Remarks</span></span>  

 <span data-ttu-id="99dec-120">颁发者令牌解析器用于解析传入令牌和消息的签名令牌。</span><span class="sxs-lookup"><span data-stu-id="99dec-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="99dec-121">它用于检索用于检查签名的加密材料。</span><span class="sxs-lookup"><span data-stu-id="99dec-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="99dec-122">您必须指定 `type` 属性。</span><span class="sxs-lookup"><span data-stu-id="99dec-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="99dec-123">指定的类型可以是 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 或从类派生的自定义类型 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="99dec-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="99dec-124">某些标记处理程序允许您在配置中指定颁发者令牌解析器设置。</span><span class="sxs-lookup"><span data-stu-id="99dec-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="99dec-125">各个标记处理程序上的设置将替代在安全令牌处理程序集合中指定的设置。</span><span class="sxs-lookup"><span data-stu-id="99dec-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99dec-126">将 `<issuerTokenResolver>` 元素指定为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已不推荐使用，但仍支持向后兼容。</span><span class="sxs-lookup"><span data-stu-id="99dec-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="99dec-127">元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="99dec-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99dec-128">示例</span><span class="sxs-lookup"><span data-stu-id="99dec-128">Example</span></span>  

 <span data-ttu-id="99dec-129">下面的 XML 显示基于从派生的自定义类的颁发者令牌解析程序的配置 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="99dec-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="99dec-130">令牌解析程序将维护从 `<AddAudienceKeyPair>`) 为类定义 (自定义配置元素初始化的受众密钥对字典。</span><span class="sxs-lookup"><span data-stu-id="99dec-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="99dec-131">类将重写 <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> 方法来处理此元素。</span><span class="sxs-lookup"><span data-stu-id="99dec-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="99dec-132">下面的示例显示了替代：但对于简洁起见，它调用的方法不会显示。</span><span class="sxs-lookup"><span data-stu-id="99dec-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="99dec-133">有关完整的示例，请参阅 `CustomToken` 示例。</span><span class="sxs-lookup"><span data-stu-id="99dec-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="99dec-134">示例</span><span class="sxs-lookup"><span data-stu-id="99dec-134">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="99dec-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="99dec-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
