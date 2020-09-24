---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4560c55cee5caf975e83ce9d4dc0b379ab905f8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156844"
---
# \<sessionTokenRequirement>

<span data-ttu-id="3926f-101">提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 类或派生类的配置。</span><span class="sxs-lookup"><span data-stu-id="3926f-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="3926f-102">语法</span><span class="sxs-lookup"><span data-stu-id="3926f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3926f-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3926f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3926f-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3926f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3926f-105">特性</span><span class="sxs-lookup"><span data-stu-id="3926f-105">Attributes</span></span>  
  
|<span data-ttu-id="3926f-106">属性</span><span class="sxs-lookup"><span data-stu-id="3926f-106">Attribute</span></span>|<span data-ttu-id="3926f-107">描述</span><span class="sxs-lookup"><span data-stu-id="3926f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3926f-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="3926f-108">lifetime</span></span>|<span data-ttu-id="3926f-109">指定会话令牌的生存期。</span><span class="sxs-lookup"><span data-stu-id="3926f-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3926f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="3926f-110">Child Elements</span></span>  

 <span data-ttu-id="3926f-111">无</span><span class="sxs-lookup"><span data-stu-id="3926f-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3926f-112">父元素</span><span class="sxs-lookup"><span data-stu-id="3926f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3926f-113">元素</span><span class="sxs-lookup"><span data-stu-id="3926f-113">Element</span></span>|<span data-ttu-id="3926f-114">描述</span><span class="sxs-lookup"><span data-stu-id="3926f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="3926f-115">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="3926f-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3926f-116">示例</span><span class="sxs-lookup"><span data-stu-id="3926f-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
