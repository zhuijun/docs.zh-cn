---
title: <behaviors> 的工作流
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 21974f77526f55a47c014a285efd3bbac6fc1f7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189599"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="967c3-102">\<behaviors> 的工作流</span><span class="sxs-lookup"><span data-stu-id="967c3-102">\<behaviors> of workflow</span></span>

<span data-ttu-id="967c3-103">此元素包含 **serviceBehaviors** 集合。</span><span class="sxs-lookup"><span data-stu-id="967c3-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="967c3-104">集合中的每个元素定义工作流服务所使用的行为元素。</span><span class="sxs-lookup"><span data-stu-id="967c3-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="967c3-105">每个行为元素都由其唯一 **名称** 属性标识。</span><span class="sxs-lookup"><span data-stu-id="967c3-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="967c3-106">语法</span><span class="sxs-lookup"><span data-stu-id="967c3-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="967c3-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="967c3-107">Attributes and Elements</span></span>  

 <span data-ttu-id="967c3-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="967c3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="967c3-109">特性</span><span class="sxs-lookup"><span data-stu-id="967c3-109">Attributes</span></span>  

 <span data-ttu-id="967c3-110">无</span><span class="sxs-lookup"><span data-stu-id="967c3-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="967c3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="967c3-111">Child Elements</span></span>  
  
|<span data-ttu-id="967c3-112">元素</span><span class="sxs-lookup"><span data-stu-id="967c3-112">Element</span></span>|<span data-ttu-id="967c3-113">描述</span><span class="sxs-lookup"><span data-stu-id="967c3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="967c3-114">此配置节表示为特定工作流服务定义的所有行为。</span><span class="sxs-lookup"><span data-stu-id="967c3-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="967c3-115">父元素</span><span class="sxs-lookup"><span data-stu-id="967c3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="967c3-116">元素</span><span class="sxs-lookup"><span data-stu-id="967c3-116">Element</span></span>|<span data-ttu-id="967c3-117">描述</span><span class="sxs-lookup"><span data-stu-id="967c3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="967c3-118">所有工作流配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="967c3-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="967c3-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="967c3-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="967c3-120">使用行为配置和扩展运行时</span><span class="sxs-lookup"><span data-stu-id="967c3-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
