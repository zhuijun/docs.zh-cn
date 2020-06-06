---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252045"
---
# \<clear>
<span data-ttu-id="f4240-101">清除当前标记处理程序集合中的所有安全标记处理程序。</span><span class="sxs-lookup"><span data-stu-id="f4240-101">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="f4240-102">语法</span><span class="sxs-lookup"><span data-stu-id="f4240-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4240-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f4240-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f4240-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f4240-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4240-105">特性</span><span class="sxs-lookup"><span data-stu-id="f4240-105">Attributes</span></span>  
 <span data-ttu-id="f4240-106">无</span><span class="sxs-lookup"><span data-stu-id="f4240-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4240-107">子元素</span><span class="sxs-lookup"><span data-stu-id="f4240-107">Child Elements</span></span>  
 <span data-ttu-id="f4240-108">无</span><span class="sxs-lookup"><span data-stu-id="f4240-108">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4240-109">父元素</span><span class="sxs-lookup"><span data-stu-id="f4240-109">Parent Elements</span></span>  
  
|<span data-ttu-id="f4240-110">元素</span><span class="sxs-lookup"><span data-stu-id="f4240-110">Element</span></span>|<span data-ttu-id="f4240-111">说明</span><span class="sxs-lookup"><span data-stu-id="f4240-111">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="f4240-112">指定注册到终结点的安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="f4240-112">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
