---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850024"
---
# \<comContract>
<span data-ttu-id="9aafe-101">指定 COM+ 集成服务协定。</span><span class="sxs-lookup"><span data-stu-id="9aafe-101">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="9aafe-102">语法</span><span class="sxs-lookup"><span data-stu-id="9aafe-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9aafe-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9aafe-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9aafe-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9aafe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aafe-105">特性</span><span class="sxs-lookup"><span data-stu-id="9aafe-105">Attributes</span></span>  
  
|<span data-ttu-id="9aafe-106">属性</span><span class="sxs-lookup"><span data-stu-id="9aafe-106">Attribute</span></span>|<span data-ttu-id="9aafe-107">说明</span><span class="sxs-lookup"><span data-stu-id="9aafe-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9aafe-108">contract</span><span class="sxs-lookup"><span data-stu-id="9aafe-108">contract</span></span>|<span data-ttu-id="9aafe-109">一个包含协定类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="9aafe-109">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="9aafe-110">NAME</span><span class="sxs-lookup"><span data-stu-id="9aafe-110">name</span></span>|<span data-ttu-id="9aafe-111">一个包含协定名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="9aafe-111">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="9aafe-112">namespace</span><span class="sxs-lookup"><span data-stu-id="9aafe-112">namespace</span></span>|<span data-ttu-id="9aafe-113">一个包含协定命名空间的字符串。</span><span class="sxs-lookup"><span data-stu-id="9aafe-113">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="9aafe-114">requiresSession</span><span class="sxs-lookup"><span data-stu-id="9aafe-114">requiresSession</span></span>|<span data-ttu-id="9aafe-115">一个布尔值，指定是否只能在会话绑定上使用该协定。</span><span class="sxs-lookup"><span data-stu-id="9aafe-115">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="9aafe-116">在初始化服务时，集成运行库可以确保此设置与要使用的绑定的类型一致。</span><span class="sxs-lookup"><span data-stu-id="9aafe-116">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="9aafe-117">如果协定的一个或多个绑定存在冲突，则会生成异常。</span><span class="sxs-lookup"><span data-stu-id="9aafe-117">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="9aafe-118">如果此属性为 `false`、使用的是单向通道并且存在任何 [out] 参数，则也会生成异常。</span><span class="sxs-lookup"><span data-stu-id="9aafe-118">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9aafe-119">子元素</span><span class="sxs-lookup"><span data-stu-id="9aafe-119">Child Elements</span></span>  
  
|<span data-ttu-id="9aafe-120">元素</span><span class="sxs-lookup"><span data-stu-id="9aafe-120">Element</span></span>|<span data-ttu-id="9aafe-121">描述</span><span class="sxs-lookup"><span data-stu-id="9aafe-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9aafe-122">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="9aafe-122">persistableTypes</span></span>|<span data-ttu-id="9aafe-123">所有持久类型。</span><span class="sxs-lookup"><span data-stu-id="9aafe-123">All the persistable types.</span></span>|  
|<span data-ttu-id="9aafe-124">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="9aafe-124">userDefinedTypes</span></span>|<span data-ttu-id="9aafe-125">一个要包括在服务协定中的用户定义的类型 (UDT) 的集合。</span><span class="sxs-lookup"><span data-stu-id="9aafe-125">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="9aafe-126">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="9aafe-126">exposedMethods</span></span>|<span data-ttu-id="9aafe-127">一个在 COM+ 组件上的接口作为 Web 服务公开时所公开的 COM+ 方法的集合。</span><span class="sxs-lookup"><span data-stu-id="9aafe-127">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9aafe-128">父元素</span><span class="sxs-lookup"><span data-stu-id="9aafe-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9aafe-129">元素</span><span class="sxs-lookup"><span data-stu-id="9aafe-129">Element</span></span>|<span data-ttu-id="9aafe-130">描述</span><span class="sxs-lookup"><span data-stu-id="9aafe-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9aafe-131">comContracts</span><span class="sxs-lookup"><span data-stu-id="9aafe-131">comContracts</span></span>|<span data-ttu-id="9aafe-132">包含 `comContract` 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="9aafe-132">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aafe-133">注解</span><span class="sxs-lookup"><span data-stu-id="9aafe-133">Remarks</span></span>  
 <span data-ttu-id="9aafe-134">COM + 集成服务协定当前仅限于 `http://tempuri.org` 命名空间，协定名称派生自支持的 COM 接口。</span><span class="sxs-lookup"><span data-stu-id="9aafe-134">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="9aafe-135">但是，可以使用配置文件中的 `comContracts` 节以及 `comContract` 元素来指定替代服务协定。</span><span class="sxs-lookup"><span data-stu-id="9aafe-135">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="9aafe-136">例如，可以使用下面的配置来指定服务协定的命名空间、协定名称、要包含的用户定义类型以及其他设置。</span><span class="sxs-lookup"><span data-stu-id="9aafe-136">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="9aafe-137">在初始化服务时，指定的命名空间和协定名称将应用到生成的服务说明。</span><span class="sxs-lookup"><span data-stu-id="9aafe-137">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aafe-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9aafe-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="9aafe-139">与 COM + 应用程序集成</span><span class="sxs-lookup"><span data-stu-id="9aafe-139">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="9aafe-140">如何：配置 COM+ 服务设置</span><span class="sxs-lookup"><span data-stu-id="9aafe-140">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
