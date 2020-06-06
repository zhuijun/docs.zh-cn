---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399711"
---
# \<serviceAuthenticationManager>
<span data-ttu-id="ea6bb-101">提供一个工作流配置元素，该元素在服务级别建立传输、消息或发起方的有效性。</span><span class="sxs-lookup"><span data-stu-id="ea6bb-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="ea6bb-102">语法</span><span class="sxs-lookup"><span data-stu-id="ea6bb-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea6bb-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ea6bb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ea6bb-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ea6bb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea6bb-105">特性</span><span class="sxs-lookup"><span data-stu-id="ea6bb-105">Attributes</span></span>  
  
|<span data-ttu-id="ea6bb-106">属性</span><span class="sxs-lookup"><span data-stu-id="ea6bb-106">Attribute</span></span>|<span data-ttu-id="ea6bb-107">说明</span><span class="sxs-lookup"><span data-stu-id="ea6bb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea6bb-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="ea6bb-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="ea6bb-109">一个字符串，指定当前行为的身份验证策略类型。</span><span class="sxs-lookup"><span data-stu-id="ea6bb-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea6bb-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ea6bb-110">Child Elements</span></span>  
 <span data-ttu-id="ea6bb-111">无。</span><span class="sxs-lookup"><span data-stu-id="ea6bb-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea6bb-112">父元素</span><span class="sxs-lookup"><span data-stu-id="ea6bb-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ea6bb-113">元素</span><span class="sxs-lookup"><span data-stu-id="ea6bb-113">Element</span></span>|<span data-ttu-id="ea6bb-114">描述</span><span class="sxs-lookup"><span data-stu-id="ea6bb-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ea6bb-115">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="ea6bb-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea6bb-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea6bb-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
