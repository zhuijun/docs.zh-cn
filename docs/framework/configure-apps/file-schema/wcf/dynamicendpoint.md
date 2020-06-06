---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855341"
---
# \<dynamicEndpoint>
<span data-ttu-id="feb86-101">此配置元素定义一个标准终结点，应用程序通过利用该终结点包含的信息，能够充当可在运行时动态查找终结点地址的客户端程序。</span><span class="sxs-lookup"><span data-stu-id="feb86-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="feb86-102">语法</span><span class="sxs-lookup"><span data-stu-id="feb86-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="feb86-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="feb86-103">Attributes and Elements</span></span>  
 <span data-ttu-id="feb86-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="feb86-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="feb86-105">特性</span><span class="sxs-lookup"><span data-stu-id="feb86-105">Attributes</span></span>  
 <span data-ttu-id="feb86-106">无。</span><span class="sxs-lookup"><span data-stu-id="feb86-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="feb86-107">子元素</span><span class="sxs-lookup"><span data-stu-id="feb86-107">Child Elements</span></span>  
  
|<span data-ttu-id="feb86-108">元素</span><span class="sxs-lookup"><span data-stu-id="feb86-108">Element</span></span>|<span data-ttu-id="feb86-109">说明</span><span class="sxs-lookup"><span data-stu-id="feb86-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="feb86-110">包含应用程序以客户端形式参与服务发现过程所需的设置。</span><span class="sxs-lookup"><span data-stu-id="feb86-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="feb86-111">父元素</span><span class="sxs-lookup"><span data-stu-id="feb86-111">Parent Elements</span></span>  
  
|<span data-ttu-id="feb86-112">元素</span><span class="sxs-lookup"><span data-stu-id="feb86-112">Element</span></span>|<span data-ttu-id="feb86-113">说明</span><span class="sxs-lookup"><span data-stu-id="feb86-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="feb86-114">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="feb86-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="feb86-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="feb86-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
