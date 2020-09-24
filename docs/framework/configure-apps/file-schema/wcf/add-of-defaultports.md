---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 2c6b5de51e6508965daf6022a47d12d8d73f2a4d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149122"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="9ad2d-102">\<add> 的 \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="9ad2d-102">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="9ad2d-103">客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="9ad2d-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9ad2d-104">语法</span><span class="sxs-lookup"><span data-stu-id="9ad2d-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad2d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9ad2d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9ad2d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9ad2d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ad2d-107">特性</span><span class="sxs-lookup"><span data-stu-id="9ad2d-107">Attributes</span></span>  
  
|<span data-ttu-id="9ad2d-108">属性</span><span class="sxs-lookup"><span data-stu-id="9ad2d-108">Attribute</span></span>|<span data-ttu-id="9ad2d-109">描述</span><span class="sxs-lookup"><span data-stu-id="9ad2d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ad2d-110">port</span><span class="sxs-lookup"><span data-stu-id="9ad2d-110">port</span></span>|<span data-ttu-id="9ad2d-111">一个整数，指定默认通信端口号。</span><span class="sxs-lookup"><span data-stu-id="9ad2d-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="9ad2d-112">scheme</span><span class="sxs-lookup"><span data-stu-id="9ad2d-112">scheme</span></span>|<span data-ttu-id="9ad2d-113">一个字符串，指定与通信端口关联的协议设置组。</span><span class="sxs-lookup"><span data-stu-id="9ad2d-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ad2d-114">子元素</span><span class="sxs-lookup"><span data-stu-id="9ad2d-114">Child Elements</span></span>  

 <span data-ttu-id="9ad2d-115">无。</span><span class="sxs-lookup"><span data-stu-id="9ad2d-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ad2d-116">父元素</span><span class="sxs-lookup"><span data-stu-id="9ad2d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9ad2d-117">元素</span><span class="sxs-lookup"><span data-stu-id="9ad2d-117">Element</span></span>|<span data-ttu-id="9ad2d-118">描述</span><span class="sxs-lookup"><span data-stu-id="9ad2d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="9ad2d-119">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="9ad2d-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ad2d-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ad2d-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
