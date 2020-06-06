---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855068"
---
# \<persistableType>
<span data-ttu-id="a6ecc-101">指定所有永久类型。</span><span class="sxs-lookup"><span data-stu-id="a6ecc-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="a6ecc-102">语法</span><span class="sxs-lookup"><span data-stu-id="a6ecc-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="a6ecc-103">类型</span><span class="sxs-lookup"><span data-stu-id="a6ecc-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6ecc-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a6ecc-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a6ecc-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a6ecc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6ecc-106">特性</span><span class="sxs-lookup"><span data-stu-id="a6ecc-106">Attributes</span></span>  
  
|<span data-ttu-id="a6ecc-107">属性</span><span class="sxs-lookup"><span data-stu-id="a6ecc-107">Attribute</span></span>|<span data-ttu-id="a6ecc-108">说明</span><span class="sxs-lookup"><span data-stu-id="a6ecc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6ecc-109">id</span><span class="sxs-lookup"><span data-stu-id="a6ecc-109">id</span></span>|<span data-ttu-id="a6ecc-110">一个必需的属性，包含一个指定持久类型唯一标识符的字符串。</span><span class="sxs-lookup"><span data-stu-id="a6ecc-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="a6ecc-111">NAME</span><span class="sxs-lookup"><span data-stu-id="a6ecc-111">name</span></span>|<span data-ttu-id="a6ecc-112">一个可选属性，包含一个指定持久类型名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="a6ecc-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6ecc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a6ecc-113">Child Elements</span></span>  
 <span data-ttu-id="a6ecc-114">无</span><span class="sxs-lookup"><span data-stu-id="a6ecc-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6ecc-115">父元素</span><span class="sxs-lookup"><span data-stu-id="a6ecc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a6ecc-116">元素</span><span class="sxs-lookup"><span data-stu-id="a6ecc-116">Element</span></span>|<span data-ttu-id="a6ecc-117">描述</span><span class="sxs-lookup"><span data-stu-id="a6ecc-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="a6ecc-118">一个 `persistableType` 元素集合。</span><span class="sxs-lookup"><span data-stu-id="a6ecc-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6ecc-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6ecc-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="a6ecc-120">与 COM + 应用程序集成</span><span class="sxs-lookup"><span data-stu-id="a6ecc-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a6ecc-121">如何：配置 COM+ 服务设置</span><span class="sxs-lookup"><span data-stu-id="a6ecc-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
