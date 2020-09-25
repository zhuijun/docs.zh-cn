---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 35596f32bf0e0de9081bc0d4c33fb370c7ab708b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173778"
---
# \<comContract>

<span data-ttu-id="53e4e-101">指定 COM+ 集成服务协定。</span><span class="sxs-lookup"><span data-stu-id="53e4e-101">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="53e4e-102">语法</span><span class="sxs-lookup"><span data-stu-id="53e4e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53e4e-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="53e4e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="53e4e-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="53e4e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53e4e-105">特性</span><span class="sxs-lookup"><span data-stu-id="53e4e-105">Attributes</span></span>  
  
|<span data-ttu-id="53e4e-106">属性</span><span class="sxs-lookup"><span data-stu-id="53e4e-106">Attribute</span></span>|<span data-ttu-id="53e4e-107">描述</span><span class="sxs-lookup"><span data-stu-id="53e4e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53e4e-108">contract</span><span class="sxs-lookup"><span data-stu-id="53e4e-108">contract</span></span>|<span data-ttu-id="53e4e-109">一个包含协定类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="53e4e-109">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="53e4e-110">name</span><span class="sxs-lookup"><span data-stu-id="53e4e-110">name</span></span>|<span data-ttu-id="53e4e-111">一个包含协定名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="53e4e-111">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="53e4e-112">命名空间</span><span class="sxs-lookup"><span data-stu-id="53e4e-112">namespace</span></span>|<span data-ttu-id="53e4e-113">一个包含协定命名空间的字符串。</span><span class="sxs-lookup"><span data-stu-id="53e4e-113">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="53e4e-114">requiresSession</span><span class="sxs-lookup"><span data-stu-id="53e4e-114">requiresSession</span></span>|<span data-ttu-id="53e4e-115">一个布尔值，指定是否只能在会话绑定上使用该协定。</span><span class="sxs-lookup"><span data-stu-id="53e4e-115">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="53e4e-116">在初始化服务时，集成运行库可以确保此设置与要使用的绑定的类型一致。</span><span class="sxs-lookup"><span data-stu-id="53e4e-116">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="53e4e-117">如果协定的一个或多个绑定存在冲突，则会生成异常。</span><span class="sxs-lookup"><span data-stu-id="53e4e-117">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="53e4e-118">如果此属性为 `false`、使用的是单向通道并且存在任何 [out] 参数，则也会生成异常。</span><span class="sxs-lookup"><span data-stu-id="53e4e-118">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53e4e-119">子元素</span><span class="sxs-lookup"><span data-stu-id="53e4e-119">Child Elements</span></span>  
  
|<span data-ttu-id="53e4e-120">元素</span><span class="sxs-lookup"><span data-stu-id="53e4e-120">Element</span></span>|<span data-ttu-id="53e4e-121">描述</span><span class="sxs-lookup"><span data-stu-id="53e4e-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53e4e-122">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="53e4e-122">persistableTypes</span></span>|<span data-ttu-id="53e4e-123">所有持久类型。</span><span class="sxs-lookup"><span data-stu-id="53e4e-123">All the persistable types.</span></span>|  
|<span data-ttu-id="53e4e-124">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="53e4e-124">userDefinedTypes</span></span>|<span data-ttu-id="53e4e-125">一个要包括在服务协定中的用户定义的类型 (UDT) 的集合。</span><span class="sxs-lookup"><span data-stu-id="53e4e-125">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="53e4e-126">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="53e4e-126">exposedMethods</span></span>|<span data-ttu-id="53e4e-127">一个在 COM+ 组件上的接口作为 Web 服务公开时所公开的 COM+ 方法的集合。</span><span class="sxs-lookup"><span data-stu-id="53e4e-127">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53e4e-128">父元素</span><span class="sxs-lookup"><span data-stu-id="53e4e-128">Parent Elements</span></span>  
  
|<span data-ttu-id="53e4e-129">元素</span><span class="sxs-lookup"><span data-stu-id="53e4e-129">Element</span></span>|<span data-ttu-id="53e4e-130">描述</span><span class="sxs-lookup"><span data-stu-id="53e4e-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53e4e-131">comContracts</span><span class="sxs-lookup"><span data-stu-id="53e4e-131">comContracts</span></span>|<span data-ttu-id="53e4e-132">包含 `comContract` 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="53e4e-132">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e4e-133">备注</span><span class="sxs-lookup"><span data-stu-id="53e4e-133">Remarks</span></span>  

 <span data-ttu-id="53e4e-134">COM + 集成服务协定当前仅限于 `http://tempuri.org` 命名空间，协定名称派生自支持的 COM 接口。</span><span class="sxs-lookup"><span data-stu-id="53e4e-134">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="53e4e-135">但是，可以使用配置文件中的 `comContracts` 节以及 `comContract` 元素来指定替代服务协定。</span><span class="sxs-lookup"><span data-stu-id="53e4e-135">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="53e4e-136">例如，可以使用下面的配置来指定服务协定的命名空间、协定名称、要包含的用户定义类型以及其他设置。</span><span class="sxs-lookup"><span data-stu-id="53e4e-136">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="53e4e-137">在初始化服务时，指定的命名空间和协定名称将应用到生成的服务说明。</span><span class="sxs-lookup"><span data-stu-id="53e4e-137">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e4e-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="53e4e-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="53e4e-139">与 COM + 应用程序集成</span><span class="sxs-lookup"><span data-stu-id="53e4e-139">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="53e4e-140">如何：配置 COM+ 服务设置</span><span class="sxs-lookup"><span data-stu-id="53e4e-140">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
