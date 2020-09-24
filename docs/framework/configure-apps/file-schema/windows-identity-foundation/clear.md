---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: 0f043442fb8edd9bf95a839a26cc42e8122d9100
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167062"
---
# \<clear>

<span data-ttu-id="b5ed7-101">清除当前标记处理程序集合中的所有安全标记处理程序。</span><span class="sxs-lookup"><span data-stu-id="b5ed7-101">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="b5ed7-102">语法</span><span class="sxs-lookup"><span data-stu-id="b5ed7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5ed7-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b5ed7-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b5ed7-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b5ed7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5ed7-105">特性</span><span class="sxs-lookup"><span data-stu-id="b5ed7-105">Attributes</span></span>  

 <span data-ttu-id="b5ed7-106">无</span><span class="sxs-lookup"><span data-stu-id="b5ed7-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5ed7-107">子元素</span><span class="sxs-lookup"><span data-stu-id="b5ed7-107">Child Elements</span></span>  

 <span data-ttu-id="b5ed7-108">无</span><span class="sxs-lookup"><span data-stu-id="b5ed7-108">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5ed7-109">父元素</span><span class="sxs-lookup"><span data-stu-id="b5ed7-109">Parent Elements</span></span>  
  
|<span data-ttu-id="b5ed7-110">元素</span><span class="sxs-lookup"><span data-stu-id="b5ed7-110">Element</span></span>|<span data-ttu-id="b5ed7-111">描述</span><span class="sxs-lookup"><span data-stu-id="b5ed7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="b5ed7-112">指定注册到终结点的安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="b5ed7-112">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
