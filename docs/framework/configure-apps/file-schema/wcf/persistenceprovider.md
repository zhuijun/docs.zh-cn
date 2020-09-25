---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dbf0ba565d4e3e2d65b4a81eb5d345fa90fb43c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181422"
---
# \<persistenceProvider>

<span data-ttu-id="d034f-101">指定要使用的持久性提供程序实现的类型以及用于持久性操作的超时值。</span><span class="sxs-lookup"><span data-stu-id="d034f-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="d034f-102">语法</span><span class="sxs-lookup"><span data-stu-id="d034f-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d034f-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d034f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d034f-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d034f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d034f-105">特性</span><span class="sxs-lookup"><span data-stu-id="d034f-105">Attributes</span></span>  
  
|<span data-ttu-id="d034f-106">属性</span><span class="sxs-lookup"><span data-stu-id="d034f-106">Attribute</span></span>|<span data-ttu-id="d034f-107">描述</span><span class="sxs-lookup"><span data-stu-id="d034f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d034f-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="d034f-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="d034f-109">一个 <xref:System.TimeSpan> 值，指定用于持久性操作的超时值。</span><span class="sxs-lookup"><span data-stu-id="d034f-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="d034f-110">默认值为 "00:00:30"。</span><span class="sxs-lookup"><span data-stu-id="d034f-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="d034f-111">type</span><span class="sxs-lookup"><span data-stu-id="d034f-111">type</span></span>|<span data-ttu-id="d034f-112">一个字符串，指定要使用的永久性提供程序工厂的类型。</span><span class="sxs-lookup"><span data-stu-id="d034f-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d034f-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d034f-113">Child Elements</span></span>  

 <span data-ttu-id="d034f-114">无。</span><span class="sxs-lookup"><span data-stu-id="d034f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d034f-115">父元素</span><span class="sxs-lookup"><span data-stu-id="d034f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d034f-116">元素</span><span class="sxs-lookup"><span data-stu-id="d034f-116">Element</span></span>|<span data-ttu-id="d034f-117">描述</span><span class="sxs-lookup"><span data-stu-id="d034f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d034f-118">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="d034f-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d034f-119">备注</span><span class="sxs-lookup"><span data-stu-id="d034f-119">Remarks</span></span>  

 <span data-ttu-id="d034f-120">此元素指定要用于序列化 WCF 服务的状态的永久性提供程序。</span><span class="sxs-lookup"><span data-stu-id="d034f-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="d034f-121">它应该与 `wsHttpContextBinding` 一起使用，后者在 HTTP 头中传递状态信息。</span><span class="sxs-lookup"><span data-stu-id="d034f-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d034f-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="d034f-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
