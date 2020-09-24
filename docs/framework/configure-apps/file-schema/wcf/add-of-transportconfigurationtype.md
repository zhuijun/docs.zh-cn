---
title: <add> 的 <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 9bef44ed39ee892080342058206f779b38fb460d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151150"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="6ba5c-102">\<add> 的 \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="6ba5c-102">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="6ba5c-103">此元素是一个键/值对，可标识特定传输的类型。</span><span class="sxs-lookup"><span data-stu-id="6ba5c-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6ba5c-104">语法</span><span class="sxs-lookup"><span data-stu-id="6ba5c-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ba5c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6ba5c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6ba5c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ba5c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ba5c-107">特性</span><span class="sxs-lookup"><span data-stu-id="6ba5c-107">Attributes</span></span>  
  
|<span data-ttu-id="6ba5c-108">属性</span><span class="sxs-lookup"><span data-stu-id="6ba5c-108">Attribute</span></span>|<span data-ttu-id="6ba5c-109">说明</span><span class="sxs-lookup"><span data-stu-id="6ba5c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ba5c-110">name</span><span class="sxs-lookup"><span data-stu-id="6ba5c-110">name</span></span>|<span data-ttu-id="6ba5c-111">必需的字符串属性。</span><span class="sxs-lookup"><span data-stu-id="6ba5c-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="6ba5c-112">包含一个唯一标识传输类型的用户定义的键。</span><span class="sxs-lookup"><span data-stu-id="6ba5c-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="6ba5c-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="6ba5c-113">transportConfigurationType</span></span>|<span data-ttu-id="6ba5c-114">一个包含实现特定传输的类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="6ba5c-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ba5c-115">子元素</span><span class="sxs-lookup"><span data-stu-id="6ba5c-115">Child Elements</span></span>  

 <span data-ttu-id="6ba5c-116">无</span><span class="sxs-lookup"><span data-stu-id="6ba5c-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ba5c-117">父元素</span><span class="sxs-lookup"><span data-stu-id="6ba5c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6ba5c-118">元素</span><span class="sxs-lookup"><span data-stu-id="6ba5c-118">Element</span></span>|<span data-ttu-id="6ba5c-119">描述</span><span class="sxs-lookup"><span data-stu-id="6ba5c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="6ba5c-120">一个实现特定传输的类型的集合。</span><span class="sxs-lookup"><span data-stu-id="6ba5c-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ba5c-121">示例</span><span class="sxs-lookup"><span data-stu-id="6ba5c-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="6ba5c-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ba5c-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="6ba5c-123">承载</span><span class="sxs-lookup"><span data-stu-id="6ba5c-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
