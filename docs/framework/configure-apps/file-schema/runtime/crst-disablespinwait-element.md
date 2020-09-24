---
title: <Crst_DisableSpinWait> 元素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 45052d99bb297ac39d058fa405fe57a7c991f738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151345"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="4b427-102">\<Crst_DisableSpinWait> 元素</span><span class="sxs-lookup"><span data-stu-id="4b427-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="4b427-103">指定是否在争用时禁用临界区等待。</span><span class="sxs-lookup"><span data-stu-id="4b427-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="4b427-104">语法</span><span class="sxs-lookup"><span data-stu-id="4b427-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b427-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4b427-105">Attributes and Elements</span></span>

<span data-ttu-id="4b427-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4b427-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b427-107">特性</span><span class="sxs-lookup"><span data-stu-id="4b427-107">Attributes</span></span>  
  
|<span data-ttu-id="4b427-108">属性</span><span class="sxs-lookup"><span data-stu-id="4b427-108">Attribute</span></span>|<span data-ttu-id="4b427-109">描述</span><span class="sxs-lookup"><span data-stu-id="4b427-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b427-110">**enabled**</span><span class="sxs-lookup"><span data-stu-id="4b427-110">**enabled**</span></span>|<span data-ttu-id="4b427-111">指定禁用已争用的关键部分时，是否旋转等待。</span><span class="sxs-lookup"><span data-stu-id="4b427-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4b427-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="4b427-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="4b427-113">值</span><span class="sxs-lookup"><span data-stu-id="4b427-113">Value</span></span>|<span data-ttu-id="4b427-114">描述</span><span class="sxs-lookup"><span data-stu-id="4b427-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b427-115">1</span><span class="sxs-lookup"><span data-stu-id="4b427-115">1</span></span>|<span data-ttu-id="4b427-116">禁用在无法获取关键部分时等待自旋。</span><span class="sxs-lookup"><span data-stu-id="4b427-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="4b427-117">0</span><span class="sxs-lookup"><span data-stu-id="4b427-117">0</span></span>|<span data-ttu-id="4b427-118">不要在无法获取关键节时禁用自旋等待。</span><span class="sxs-lookup"><span data-stu-id="4b427-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="4b427-119">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="4b427-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b427-120">子元素</span><span class="sxs-lookup"><span data-stu-id="4b427-120">Child Elements</span></span>  

 <span data-ttu-id="4b427-121">无。</span><span class="sxs-lookup"><span data-stu-id="4b427-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b427-122">父元素</span><span class="sxs-lookup"><span data-stu-id="4b427-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4b427-123">元素</span><span class="sxs-lookup"><span data-stu-id="4b427-123">Element</span></span>|<span data-ttu-id="4b427-124">描述</span><span class="sxs-lookup"><span data-stu-id="4b427-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4b427-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="4b427-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4b427-126">包含有关各种运行时配置设置的信息。</span><span class="sxs-lookup"><span data-stu-id="4b427-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4b427-127">示例</span><span class="sxs-lookup"><span data-stu-id="4b427-127">Example</span></span>  

<span data-ttu-id="4b427-128">下面的示例在争用时在关键部分禁用自旋。</span><span class="sxs-lookup"><span data-stu-id="4b427-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b427-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="4b427-129">See also</span></span>

- [<span data-ttu-id="4b427-130">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="4b427-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4b427-131">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="4b427-131">Configuration File Schema</span></span>](../index.md)
