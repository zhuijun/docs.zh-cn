---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152536"
---
# \<sessionTokenRequirement>
<span data-ttu-id="0c016-101">提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 类或派生类的配置。</span><span class="sxs-lookup"><span data-stu-id="0c016-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="0c016-102">语法</span><span class="sxs-lookup"><span data-stu-id="0c016-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c016-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0c016-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0c016-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0c016-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c016-105">特性</span><span class="sxs-lookup"><span data-stu-id="0c016-105">Attributes</span></span>  
  
|<span data-ttu-id="0c016-106">属性</span><span class="sxs-lookup"><span data-stu-id="0c016-106">Attribute</span></span>|<span data-ttu-id="0c016-107">说明</span><span class="sxs-lookup"><span data-stu-id="0c016-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c016-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="0c016-108">lifetime</span></span>|<span data-ttu-id="0c016-109">指定会话令牌的生存期。</span><span class="sxs-lookup"><span data-stu-id="0c016-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c016-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0c016-110">Child Elements</span></span>  
 <span data-ttu-id="0c016-111">无</span><span class="sxs-lookup"><span data-stu-id="0c016-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c016-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0c016-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0c016-113">元素</span><span class="sxs-lookup"><span data-stu-id="0c016-113">Element</span></span>|<span data-ttu-id="0c016-114">描述</span><span class="sxs-lookup"><span data-stu-id="0c016-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="0c016-115">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="0c016-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c016-116">示例</span><span class="sxs-lookup"><span data-stu-id="0c016-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
