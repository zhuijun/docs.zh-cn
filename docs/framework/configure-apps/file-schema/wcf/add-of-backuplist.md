---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 6d8fd26170059226583a300b1b48b849666db929
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181617"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="cfdeb-102">\<add> 的 \<backupList></span><span class="sxs-lookup"><span data-stu-id="cfdeb-102">\<add> of \<backupList></span></span>

<span data-ttu-id="cfdeb-103">表示定义备份终结点元素的配置元素。</span><span class="sxs-lookup"><span data-stu-id="cfdeb-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cfdeb-104">语法</span><span class="sxs-lookup"><span data-stu-id="cfdeb-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfdeb-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cfdeb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cfdeb-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cfdeb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfdeb-107">特性</span><span class="sxs-lookup"><span data-stu-id="cfdeb-107">Attributes</span></span>  
  
|<span data-ttu-id="cfdeb-108">属性</span><span class="sxs-lookup"><span data-stu-id="cfdeb-108">Attribute</span></span>|<span data-ttu-id="cfdeb-109">说明</span><span class="sxs-lookup"><span data-stu-id="cfdeb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfdeb-110">name</span><span class="sxs-lookup"><span data-stu-id="cfdeb-110">name</span></span>|<span data-ttu-id="cfdeb-111">一个字符串，指定备份终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="cfdeb-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfdeb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="cfdeb-112">Child Elements</span></span>  

 <span data-ttu-id="cfdeb-113">无。</span><span class="sxs-lookup"><span data-stu-id="cfdeb-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfdeb-114">父元素</span><span class="sxs-lookup"><span data-stu-id="cfdeb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cfdeb-115">元素</span><span class="sxs-lookup"><span data-stu-id="cfdeb-115">Element</span></span>|<span data-ttu-id="cfdeb-116">描述</span><span class="sxs-lookup"><span data-stu-id="cfdeb-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="cfdeb-117">包含当无法访问主终结点时路由服务将使用的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="cfdeb-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cfdeb-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="cfdeb-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
