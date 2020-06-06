---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400066"
---
# \<persistenceProvider>
<span data-ttu-id="bf27a-101">指定要使用的持久性提供程序实现的类型以及用于持久性操作的超时值。</span><span class="sxs-lookup"><span data-stu-id="bf27a-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="bf27a-102">语法</span><span class="sxs-lookup"><span data-stu-id="bf27a-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf27a-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bf27a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="bf27a-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bf27a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf27a-105">特性</span><span class="sxs-lookup"><span data-stu-id="bf27a-105">Attributes</span></span>  
  
|<span data-ttu-id="bf27a-106">属性</span><span class="sxs-lookup"><span data-stu-id="bf27a-106">Attribute</span></span>|<span data-ttu-id="bf27a-107">说明</span><span class="sxs-lookup"><span data-stu-id="bf27a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf27a-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="bf27a-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="bf27a-109">一个 <xref:System.TimeSpan> 值，指定用于持久性操作的超时值。</span><span class="sxs-lookup"><span data-stu-id="bf27a-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="bf27a-110">默认值为 "00:00:30"。</span><span class="sxs-lookup"><span data-stu-id="bf27a-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="bf27a-111">type</span><span class="sxs-lookup"><span data-stu-id="bf27a-111">type</span></span>|<span data-ttu-id="bf27a-112">一个字符串，指定要使用的永久性提供程序工厂的类型。</span><span class="sxs-lookup"><span data-stu-id="bf27a-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf27a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="bf27a-113">Child Elements</span></span>  
 <span data-ttu-id="bf27a-114">无。</span><span class="sxs-lookup"><span data-stu-id="bf27a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf27a-115">父元素</span><span class="sxs-lookup"><span data-stu-id="bf27a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bf27a-116">元素</span><span class="sxs-lookup"><span data-stu-id="bf27a-116">Element</span></span>|<span data-ttu-id="bf27a-117">描述</span><span class="sxs-lookup"><span data-stu-id="bf27a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bf27a-118">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="bf27a-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf27a-119">注解</span><span class="sxs-lookup"><span data-stu-id="bf27a-119">Remarks</span></span>  
 <span data-ttu-id="bf27a-120">此元素指定要用于序列化 WCF 服务的状态的永久性提供程序。</span><span class="sxs-lookup"><span data-stu-id="bf27a-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="bf27a-121">它应该与 `wsHttpContextBinding` 一起使用，后者在 HTTP 头中传递状态信息。</span><span class="sxs-lookup"><span data-stu-id="bf27a-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf27a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf27a-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
