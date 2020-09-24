---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 1b5427210142c70c31c5f736c9b5e281dca53f33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150864"
---
# \<claimType>

<span data-ttu-id="c05c3-101">为传入安全令牌指定一个可选的或必需的声明。</span><span class="sxs-lookup"><span data-stu-id="c05c3-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="c05c3-102">语法</span><span class="sxs-lookup"><span data-stu-id="c05c3-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c05c3-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c05c3-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c05c3-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c05c3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c05c3-105">特性</span><span class="sxs-lookup"><span data-stu-id="c05c3-105">Attributes</span></span>  
  
|<span data-ttu-id="c05c3-106">属性</span><span class="sxs-lookup"><span data-stu-id="c05c3-106">Attribute</span></span>|<span data-ttu-id="c05c3-107">说明</span><span class="sxs-lookup"><span data-stu-id="c05c3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c05c3-108">type</span><span class="sxs-lookup"><span data-stu-id="c05c3-108">type</span></span>|<span data-ttu-id="c05c3-109">声明类型。</span><span class="sxs-lookup"><span data-stu-id="c05c3-109">The claim type.</span></span> <span data-ttu-id="c05c3-110">通常为 URI。</span><span class="sxs-lookup"><span data-stu-id="c05c3-110">Typically a URI.</span></span> <span data-ttu-id="c05c3-111">必需。</span><span class="sxs-lookup"><span data-stu-id="c05c3-111">Required.</span></span>|  
|<span data-ttu-id="c05c3-112">可选</span><span class="sxs-lookup"><span data-stu-id="c05c3-112">optional</span></span>|<span data-ttu-id="c05c3-113">指定声明类型是否为可选的布尔值。</span><span class="sxs-lookup"><span data-stu-id="c05c3-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="c05c3-114">可选。</span><span class="sxs-lookup"><span data-stu-id="c05c3-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c05c3-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c05c3-115">Child Elements</span></span>  

 <span data-ttu-id="c05c3-116">无</span><span class="sxs-lookup"><span data-stu-id="c05c3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c05c3-117">父元素</span><span class="sxs-lookup"><span data-stu-id="c05c3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c05c3-118">元素</span><span class="sxs-lookup"><span data-stu-id="c05c3-118">Element</span></span>|<span data-ttu-id="c05c3-119">描述</span><span class="sxs-lookup"><span data-stu-id="c05c3-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="c05c3-120">指定传入安全令牌所需的声明集。</span><span class="sxs-lookup"><span data-stu-id="c05c3-120">Specifies the set of required claims for incoming security tokens.</span></span>|
