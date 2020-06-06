---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399553"
---
# \<serviceTimeouts>
<span data-ttu-id="85657-101">指定服务的超时。</span><span class="sxs-lookup"><span data-stu-id="85657-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="85657-102">语法</span><span class="sxs-lookup"><span data-stu-id="85657-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="85657-103">类型</span><span class="sxs-lookup"><span data-stu-id="85657-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85657-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="85657-104">Attributes and Elements</span></span>  
 <span data-ttu-id="85657-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85657-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85657-106">特性</span><span class="sxs-lookup"><span data-stu-id="85657-106">Attributes</span></span>  
  
|<span data-ttu-id="85657-107">属性</span><span class="sxs-lookup"><span data-stu-id="85657-107">Attribute</span></span>|<span data-ttu-id="85657-108">说明</span><span class="sxs-lookup"><span data-stu-id="85657-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="85657-109">一个 <xref:System.TimeSpan> 值，指定事务从客户端流动到服务器所必须经历的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="85657-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="85657-110">默认值为 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="85657-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85657-111">子元素</span><span class="sxs-lookup"><span data-stu-id="85657-111">Child Elements</span></span>  
 <span data-ttu-id="85657-112">无。</span><span class="sxs-lookup"><span data-stu-id="85657-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85657-113">父元素</span><span class="sxs-lookup"><span data-stu-id="85657-113">Parent Elements</span></span>  
  
|<span data-ttu-id="85657-114">元素</span><span class="sxs-lookup"><span data-stu-id="85657-114">Element</span></span>|<span data-ttu-id="85657-115">描述</span><span class="sxs-lookup"><span data-stu-id="85657-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="85657-116">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="85657-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85657-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85657-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
