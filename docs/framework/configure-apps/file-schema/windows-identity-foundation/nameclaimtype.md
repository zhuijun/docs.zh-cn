---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251942"
---
# \<nameClaimType>
<span data-ttu-id="c3577-101">设置指定属性的声明类型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c3577-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c3577-102">声明类型用于 <xref:System.Security.Claims.Claim> 在 <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 此标记处理程序的方法返回的对象集合中搜索。</span><span class="sxs-lookup"><span data-stu-id="c3577-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="c3577-103">然后，将匹配声明的值设置为 <xref:System.Security.Principal.IIdentity> 从此标记处理程序生成的的名称。</span><span class="sxs-lookup"><span data-stu-id="c3577-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="c3577-104">语法</span><span class="sxs-lookup"><span data-stu-id="c3577-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3577-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c3577-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c3577-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c3577-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3577-107">特性</span><span class="sxs-lookup"><span data-stu-id="c3577-107">Attributes</span></span>  
  
|<span data-ttu-id="c3577-108">属性</span><span class="sxs-lookup"><span data-stu-id="c3577-108">Attribute</span></span>|<span data-ttu-id="c3577-109">说明</span><span class="sxs-lookup"><span data-stu-id="c3577-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3577-110">值</span><span class="sxs-lookup"><span data-stu-id="c3577-110">value</span></span>|<span data-ttu-id="c3577-111">一个字符串，指定表示要用于属性的声明的声明类型的 URI <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c3577-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c3577-112">必需。</span><span class="sxs-lookup"><span data-stu-id="c3577-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3577-113">子元素</span><span class="sxs-lookup"><span data-stu-id="c3577-113">Child Elements</span></span>  
 <span data-ttu-id="c3577-114">无</span><span class="sxs-lookup"><span data-stu-id="c3577-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3577-115">父元素</span><span class="sxs-lookup"><span data-stu-id="c3577-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c3577-116">元素</span><span class="sxs-lookup"><span data-stu-id="c3577-116">Element</span></span>|<span data-ttu-id="c3577-117">描述</span><span class="sxs-lookup"><span data-stu-id="c3577-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="c3577-118">为 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 类、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 类或其中任何一个类的派生类提供配置。</span><span class="sxs-lookup"><span data-stu-id="c3577-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3577-119">注解</span><span class="sxs-lookup"><span data-stu-id="c3577-119">Remarks</span></span>  
 <span data-ttu-id="c3577-120">`<nameClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 从配置中初始化对象时，元素设置属性。</span><span class="sxs-lookup"><span data-stu-id="c3577-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3577-121">示例</span><span class="sxs-lookup"><span data-stu-id="c3577-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3577-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3577-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
