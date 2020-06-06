---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854925"
---
# \<transportConfigurationTypes>
<span data-ttu-id="e8646-101">表示一个配置元素集合，这些元素标识了特定传输的类型。</span><span class="sxs-lookup"><span data-stu-id="e8646-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="e8646-102">这可以用于添加自定义 WAS 协议。</span><span class="sxs-lookup"><span data-stu-id="e8646-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="e8646-103">语法</span><span class="sxs-lookup"><span data-stu-id="e8646-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8646-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e8646-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e8646-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e8646-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8646-106">特性</span><span class="sxs-lookup"><span data-stu-id="e8646-106">Attributes</span></span>  
  
|<span data-ttu-id="e8646-107">属性</span><span class="sxs-lookup"><span data-stu-id="e8646-107">Attribute</span></span>|<span data-ttu-id="e8646-108">说明</span><span class="sxs-lookup"><span data-stu-id="e8646-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8646-109">name</span><span class="sxs-lookup"><span data-stu-id="e8646-109">name</span></span>|<span data-ttu-id="e8646-110">传输的名称</span><span class="sxs-lookup"><span data-stu-id="e8646-110">The name of the transport</span></span>|  
|<span data-ttu-id="e8646-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="e8646-111">transportConfigurationType</span></span>|<span data-ttu-id="e8646-112">实现传输的类型</span><span class="sxs-lookup"><span data-stu-id="e8646-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8646-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e8646-113">Child Elements</span></span>  
  
|<span data-ttu-id="e8646-114">元素</span><span class="sxs-lookup"><span data-stu-id="e8646-114">Element</span></span>|<span data-ttu-id="e8646-115">描述</span><span class="sxs-lookup"><span data-stu-id="e8646-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="e8646-116">添加一个用于标识特定传输的类型的配置元素。</span><span class="sxs-lookup"><span data-stu-id="e8646-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8646-117">父元素</span><span class="sxs-lookup"><span data-stu-id="e8646-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e8646-118">元素</span><span class="sxs-lookup"><span data-stu-id="e8646-118">Element</span></span>|<span data-ttu-id="e8646-119">描述</span><span class="sxs-lookup"><span data-stu-id="e8646-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="e8646-120">定义服务承载环境要为特定传输实例化的类型。</span><span class="sxs-lookup"><span data-stu-id="e8646-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8646-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8646-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="e8646-122">承载</span><span class="sxs-lookup"><span data-stu-id="e8646-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
