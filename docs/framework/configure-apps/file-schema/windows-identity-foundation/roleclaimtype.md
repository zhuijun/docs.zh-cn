---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 36d727f97597df816779da1c1f7ed5da1a1697f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164930"
---
# \<roleClaimType>

<span data-ttu-id="0149e-101">指定声明类型，该声明类型定义 <xref:System.Security.Claims.ClaimsIdentity> 由标记处理程序的方法返回的对象集合中的角色类型声明 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0149e-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="0149e-102">语法</span><span class="sxs-lookup"><span data-stu-id="0149e-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0149e-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0149e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0149e-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0149e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0149e-105">特性</span><span class="sxs-lookup"><span data-stu-id="0149e-105">Attributes</span></span>  
  
|<span data-ttu-id="0149e-106">属性</span><span class="sxs-lookup"><span data-stu-id="0149e-106">Attribute</span></span>|<span data-ttu-id="0149e-107">说明</span><span class="sxs-lookup"><span data-stu-id="0149e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0149e-108">值</span><span class="sxs-lookup"><span data-stu-id="0149e-108">value</span></span>|<span data-ttu-id="0149e-109">一个字符串，指定表示要用于角色声明类型的声明的声明类型的 URI。</span><span class="sxs-lookup"><span data-stu-id="0149e-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0149e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0149e-110">Child Elements</span></span>  

 <span data-ttu-id="0149e-111">无</span><span class="sxs-lookup"><span data-stu-id="0149e-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0149e-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0149e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0149e-113">元素</span><span class="sxs-lookup"><span data-stu-id="0149e-113">Element</span></span>|<span data-ttu-id="0149e-114">描述</span><span class="sxs-lookup"><span data-stu-id="0149e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="0149e-115">为 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 类、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 类或其中任何一个类的派生类提供配置。</span><span class="sxs-lookup"><span data-stu-id="0149e-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0149e-116">备注</span><span class="sxs-lookup"><span data-stu-id="0149e-116">Remarks</span></span>  

 <span data-ttu-id="0149e-117">`<roleClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 从配置中初始化对象时，元素设置属性。</span><span class="sxs-lookup"><span data-stu-id="0149e-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0149e-118">示例</span><span class="sxs-lookup"><span data-stu-id="0149e-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0149e-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="0149e-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
