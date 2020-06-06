---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252051"
---
# \<claimTypeRequired>
<span data-ttu-id="eadca-101">指定传入安全令牌所需的声明集。</span><span class="sxs-lookup"><span data-stu-id="eadca-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="eadca-102">语法</span><span class="sxs-lookup"><span data-stu-id="eadca-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eadca-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="eadca-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eadca-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eadca-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eadca-105">特性</span><span class="sxs-lookup"><span data-stu-id="eadca-105">Attributes</span></span>  
 <span data-ttu-id="eadca-106">无</span><span class="sxs-lookup"><span data-stu-id="eadca-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eadca-107">子元素</span><span class="sxs-lookup"><span data-stu-id="eadca-107">Child Elements</span></span>  
  
|<span data-ttu-id="eadca-108">元素</span><span class="sxs-lookup"><span data-stu-id="eadca-108">Element</span></span>|<span data-ttu-id="eadca-109">说明</span><span class="sxs-lookup"><span data-stu-id="eadca-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="eadca-110">为传入安全令牌指定一个可选的或必需的声明。</span><span class="sxs-lookup"><span data-stu-id="eadca-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eadca-111">父元素</span><span class="sxs-lookup"><span data-stu-id="eadca-111">Parent Elements</span></span>  
  
|<span data-ttu-id="eadca-112">元素</span><span class="sxs-lookup"><span data-stu-id="eadca-112">Element</span></span>|<span data-ttu-id="eadca-113">说明</span><span class="sxs-lookup"><span data-stu-id="eadca-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="eadca-114">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="eadca-114">Specifies service-level identity settings.</span></span>|
