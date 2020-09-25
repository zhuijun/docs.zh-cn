---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: a49b41c04c8f184188b62e04c3b232bd33752fca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185517"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="ee02a-101">提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 类或派生类的配置。</span><span class="sxs-lookup"><span data-stu-id="ee02a-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="ee02a-102">语法</span><span class="sxs-lookup"><span data-stu-id="ee02a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee02a-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ee02a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ee02a-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ee02a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee02a-105">特性</span><span class="sxs-lookup"><span data-stu-id="ee02a-105">Attributes</span></span>  
  
|<span data-ttu-id="ee02a-106">属性</span><span class="sxs-lookup"><span data-stu-id="ee02a-106">Attribute</span></span>|<span data-ttu-id="ee02a-107">描述</span><span class="sxs-lookup"><span data-stu-id="ee02a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee02a-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="ee02a-108">membershipProviderName</span></span>|<span data-ttu-id="ee02a-109">指定 <xref:System.Web.Security.MembershipProvider> 应该由安全令牌处理程序使用的。</span><span class="sxs-lookup"><span data-stu-id="ee02a-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee02a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ee02a-110">Child Elements</span></span>  

 <span data-ttu-id="ee02a-111">无</span><span class="sxs-lookup"><span data-stu-id="ee02a-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee02a-112">父元素</span><span class="sxs-lookup"><span data-stu-id="ee02a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ee02a-113">元素</span><span class="sxs-lookup"><span data-stu-id="ee02a-113">Element</span></span>|<span data-ttu-id="ee02a-114">描述</span><span class="sxs-lookup"><span data-stu-id="ee02a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="ee02a-115">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="ee02a-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee02a-116">备注</span><span class="sxs-lookup"><span data-stu-id="ee02a-116">Remarks</span></span>  

 <span data-ttu-id="ee02a-117">`<userNameSecurityTokenHandlerRequirement>` <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 从配置中初始化对象时，元素设置属性。</span><span class="sxs-lookup"><span data-stu-id="ee02a-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee02a-118">示例</span><span class="sxs-lookup"><span data-stu-id="ee02a-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
