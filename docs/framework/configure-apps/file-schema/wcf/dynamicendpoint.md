---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 6f9cb127deb5651ed27a0ef5802512fb5b6c7b54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190093"
---
# \<dynamicEndpoint>

<span data-ttu-id="ec2c6-101">此配置元素定义一个标准终结点，应用程序通过利用该终结点包含的信息，能够充当可在运行时动态查找终结点地址的客户端程序。</span><span class="sxs-lookup"><span data-stu-id="ec2c6-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="ec2c6-102">语法</span><span class="sxs-lookup"><span data-stu-id="ec2c6-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec2c6-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ec2c6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ec2c6-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ec2c6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec2c6-105">特性</span><span class="sxs-lookup"><span data-stu-id="ec2c6-105">Attributes</span></span>  

 <span data-ttu-id="ec2c6-106">无。</span><span class="sxs-lookup"><span data-stu-id="ec2c6-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec2c6-107">子元素</span><span class="sxs-lookup"><span data-stu-id="ec2c6-107">Child Elements</span></span>  
  
|<span data-ttu-id="ec2c6-108">元素</span><span class="sxs-lookup"><span data-stu-id="ec2c6-108">Element</span></span>|<span data-ttu-id="ec2c6-109">描述</span><span class="sxs-lookup"><span data-stu-id="ec2c6-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="ec2c6-110">包含应用程序以客户端形式参与服务发现过程所需的设置。</span><span class="sxs-lookup"><span data-stu-id="ec2c6-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec2c6-111">父元素</span><span class="sxs-lookup"><span data-stu-id="ec2c6-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ec2c6-112">元素</span><span class="sxs-lookup"><span data-stu-id="ec2c6-112">Element</span></span>|<span data-ttu-id="ec2c6-113">描述</span><span class="sxs-lookup"><span data-stu-id="ec2c6-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ec2c6-114">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="ec2c6-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec2c6-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="ec2c6-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
