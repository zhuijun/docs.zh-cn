---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: a7c1e06c74bd3ba62d52ef833b8ffb6a8fd594fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167166"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="2222b-101">提供一个工作流配置元素，该元素在服务级别建立传输、消息或发起方的有效性。</span><span class="sxs-lookup"><span data-stu-id="2222b-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="2222b-102">语法</span><span class="sxs-lookup"><span data-stu-id="2222b-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2222b-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2222b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="2222b-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2222b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2222b-105">特性</span><span class="sxs-lookup"><span data-stu-id="2222b-105">Attributes</span></span>  
  
|<span data-ttu-id="2222b-106">属性</span><span class="sxs-lookup"><span data-stu-id="2222b-106">Attribute</span></span>|<span data-ttu-id="2222b-107">描述</span><span class="sxs-lookup"><span data-stu-id="2222b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2222b-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="2222b-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="2222b-109">一个字符串，指定当前行为的身份验证策略类型。</span><span class="sxs-lookup"><span data-stu-id="2222b-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2222b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="2222b-110">Child Elements</span></span>  

 <span data-ttu-id="2222b-111">无。</span><span class="sxs-lookup"><span data-stu-id="2222b-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2222b-112">父元素</span><span class="sxs-lookup"><span data-stu-id="2222b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2222b-113">元素</span><span class="sxs-lookup"><span data-stu-id="2222b-113">Element</span></span>|<span data-ttu-id="2222b-114">描述</span><span class="sxs-lookup"><span data-stu-id="2222b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2222b-115">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="2222b-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2222b-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="2222b-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
