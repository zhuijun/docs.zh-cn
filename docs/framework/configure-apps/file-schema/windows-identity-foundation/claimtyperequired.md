---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: a86265ba3963ebc8bea880befbcf80345529116d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203847"
---
# \<claimTypeRequired>

<span data-ttu-id="3ce7a-101">指定传入安全令牌所需的声明集。</span><span class="sxs-lookup"><span data-stu-id="3ce7a-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="3ce7a-102">语法</span><span class="sxs-lookup"><span data-stu-id="3ce7a-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ce7a-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3ce7a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3ce7a-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ce7a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ce7a-105">特性</span><span class="sxs-lookup"><span data-stu-id="3ce7a-105">Attributes</span></span>  

 <span data-ttu-id="3ce7a-106">无</span><span class="sxs-lookup"><span data-stu-id="3ce7a-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ce7a-107">子元素</span><span class="sxs-lookup"><span data-stu-id="3ce7a-107">Child Elements</span></span>  
  
|<span data-ttu-id="3ce7a-108">元素</span><span class="sxs-lookup"><span data-stu-id="3ce7a-108">Element</span></span>|<span data-ttu-id="3ce7a-109">描述</span><span class="sxs-lookup"><span data-stu-id="3ce7a-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="3ce7a-110">为传入安全令牌指定一个可选的或必需的声明。</span><span class="sxs-lookup"><span data-stu-id="3ce7a-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ce7a-111">父元素</span><span class="sxs-lookup"><span data-stu-id="3ce7a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3ce7a-112">元素</span><span class="sxs-lookup"><span data-stu-id="3ce7a-112">Element</span></span>|<span data-ttu-id="3ce7a-113">描述</span><span class="sxs-lookup"><span data-stu-id="3ce7a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="3ce7a-114">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="3ce7a-114">Specifies service-level identity settings.</span></span>|
