---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400643"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="6f868-102">\<add> 的 \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="6f868-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="6f868-103">客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="6f868-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6f868-104">语法</span><span class="sxs-lookup"><span data-stu-id="6f868-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f868-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6f868-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6f868-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f868-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f868-107">特性</span><span class="sxs-lookup"><span data-stu-id="6f868-107">Attributes</span></span>  
  
|<span data-ttu-id="6f868-108">属性</span><span class="sxs-lookup"><span data-stu-id="6f868-108">Attribute</span></span>|<span data-ttu-id="6f868-109">说明</span><span class="sxs-lookup"><span data-stu-id="6f868-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f868-110">port</span><span class="sxs-lookup"><span data-stu-id="6f868-110">port</span></span>|<span data-ttu-id="6f868-111">一个整数，指定默认通信端口号。</span><span class="sxs-lookup"><span data-stu-id="6f868-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="6f868-112">scheme</span><span class="sxs-lookup"><span data-stu-id="6f868-112">scheme</span></span>|<span data-ttu-id="6f868-113">一个字符串，指定与通信端口关联的协议设置组。</span><span class="sxs-lookup"><span data-stu-id="6f868-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f868-114">子元素</span><span class="sxs-lookup"><span data-stu-id="6f868-114">Child Elements</span></span>  
 <span data-ttu-id="6f868-115">无。</span><span class="sxs-lookup"><span data-stu-id="6f868-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f868-116">父元素</span><span class="sxs-lookup"><span data-stu-id="6f868-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6f868-117">元素</span><span class="sxs-lookup"><span data-stu-id="6f868-117">Element</span></span>|<span data-ttu-id="6f868-118">描述</span><span class="sxs-lookup"><span data-stu-id="6f868-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="6f868-119">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="6f868-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f868-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f868-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
