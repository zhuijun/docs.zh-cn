---
title: <add> 的 <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850531"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="d2b2d-102">\<add> 的 \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="d2b2d-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="d2b2d-103">一个配置元素，指定要搜索的服务的协定名称以及搜索服务时通常使用的条件。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="d2b2d-104">如果指定多个协定名称，则只有与全部协定都匹配的服务终结点才会进行答复。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="d2b2d-105">请注意，在 Windows Communication Foundation （WCF）中，一个终结点只能支持一个协定。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d2b2d-106">语法</span><span class="sxs-lookup"><span data-stu-id="d2b2d-106">Syntax</span></span>  
  
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
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2b2d-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d2b2d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d2b2d-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2b2d-109">特性</span><span class="sxs-lookup"><span data-stu-id="d2b2d-109">Attributes</span></span>  
  
|<span data-ttu-id="d2b2d-110">属性</span><span class="sxs-lookup"><span data-stu-id="d2b2d-110">Attribute</span></span>|<span data-ttu-id="d2b2d-111">说明</span><span class="sxs-lookup"><span data-stu-id="d2b2d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2b2d-112">name</span><span class="sxs-lookup"><span data-stu-id="d2b2d-112">name</span></span>|<span data-ttu-id="d2b2d-113">一个字符串，指定协定类型的名称。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="d2b2d-114">namespace</span><span class="sxs-lookup"><span data-stu-id="d2b2d-114">namespace</span></span>|<span data-ttu-id="d2b2d-115">一个字符串，指定协定类型的命名空间。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2b2d-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d2b2d-116">Child Elements</span></span>  
 <span data-ttu-id="d2b2d-117">无</span><span class="sxs-lookup"><span data-stu-id="d2b2d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2b2d-118">父元素</span><span class="sxs-lookup"><span data-stu-id="d2b2d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d2b2d-119">元素</span><span class="sxs-lookup"><span data-stu-id="d2b2d-119">Element</span></span>|<span data-ttu-id="d2b2d-120">描述</span><span class="sxs-lookup"><span data-stu-id="d2b2d-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="d2b2d-121">协定类型名称的集合。</span><span class="sxs-lookup"><span data-stu-id="d2b2d-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2b2d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2b2d-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
