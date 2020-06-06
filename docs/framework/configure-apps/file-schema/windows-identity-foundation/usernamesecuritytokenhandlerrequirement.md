---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251737"
---
# \<userNameSecurityTokenHandlerRequirement>
<span data-ttu-id="5208d-101">提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 类或派生类的配置。</span><span class="sxs-lookup"><span data-stu-id="5208d-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="5208d-102">语法</span><span class="sxs-lookup"><span data-stu-id="5208d-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5208d-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5208d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5208d-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5208d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5208d-105">特性</span><span class="sxs-lookup"><span data-stu-id="5208d-105">Attributes</span></span>  
  
|<span data-ttu-id="5208d-106">属性</span><span class="sxs-lookup"><span data-stu-id="5208d-106">Attribute</span></span>|<span data-ttu-id="5208d-107">说明</span><span class="sxs-lookup"><span data-stu-id="5208d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5208d-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="5208d-108">membershipProviderName</span></span>|<span data-ttu-id="5208d-109">指定 <xref:System.Web.Security.MembershipProvider> 应该由安全令牌处理程序使用的。</span><span class="sxs-lookup"><span data-stu-id="5208d-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5208d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="5208d-110">Child Elements</span></span>  
 <span data-ttu-id="5208d-111">无</span><span class="sxs-lookup"><span data-stu-id="5208d-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5208d-112">父元素</span><span class="sxs-lookup"><span data-stu-id="5208d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5208d-113">元素</span><span class="sxs-lookup"><span data-stu-id="5208d-113">Element</span></span>|<span data-ttu-id="5208d-114">描述</span><span class="sxs-lookup"><span data-stu-id="5208d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="5208d-115">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="5208d-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5208d-116">注解</span><span class="sxs-lookup"><span data-stu-id="5208d-116">Remarks</span></span>  
 <span data-ttu-id="5208d-117">`<userNameSecurityTokenHandlerRequirement>` <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 从配置中初始化对象时，元素设置属性。</span><span class="sxs-lookup"><span data-stu-id="5208d-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5208d-118">示例</span><span class="sxs-lookup"><span data-stu-id="5208d-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
