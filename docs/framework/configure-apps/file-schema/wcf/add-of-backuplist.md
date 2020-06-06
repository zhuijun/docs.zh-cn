---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850553"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="ed778-102">\<add> 的 \<backupList></span><span class="sxs-lookup"><span data-stu-id="ed778-102">\<add> of \<backupList></span></span>
<span data-ttu-id="ed778-103">表示定义备份终结点元素的配置元素。</span><span class="sxs-lookup"><span data-stu-id="ed778-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ed778-104">语法</span><span class="sxs-lookup"><span data-stu-id="ed778-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed778-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ed778-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ed778-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ed778-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed778-107">特性</span><span class="sxs-lookup"><span data-stu-id="ed778-107">Attributes</span></span>  
  
|<span data-ttu-id="ed778-108">属性</span><span class="sxs-lookup"><span data-stu-id="ed778-108">Attribute</span></span>|<span data-ttu-id="ed778-109">说明</span><span class="sxs-lookup"><span data-stu-id="ed778-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed778-110">name</span><span class="sxs-lookup"><span data-stu-id="ed778-110">name</span></span>|<span data-ttu-id="ed778-111">一个字符串，指定备份终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="ed778-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed778-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ed778-112">Child Elements</span></span>  
 <span data-ttu-id="ed778-113">无。</span><span class="sxs-lookup"><span data-stu-id="ed778-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed778-114">父元素</span><span class="sxs-lookup"><span data-stu-id="ed778-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ed778-115">元素</span><span class="sxs-lookup"><span data-stu-id="ed778-115">Element</span></span>|<span data-ttu-id="ed778-116">描述</span><span class="sxs-lookup"><span data-stu-id="ed778-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="ed778-117">包含当无法访问主终结点时路由服务将使用的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="ed778-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed778-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed778-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
