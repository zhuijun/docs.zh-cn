---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152575"
---
# \<serviceTokenResolver>
<span data-ttu-id="22cfc-101">注册令牌处理程序集合中的处理程序使用的服务令牌解析程序。</span><span class="sxs-lookup"><span data-stu-id="22cfc-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="22cfc-102">服务令牌解析器用于解析传入令牌和消息的加密令牌。</span><span class="sxs-lookup"><span data-stu-id="22cfc-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="22cfc-103">语法</span><span class="sxs-lookup"><span data-stu-id="22cfc-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22cfc-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="22cfc-104">Attributes and Elements</span></span>  
 <span data-ttu-id="22cfc-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="22cfc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22cfc-106">特性</span><span class="sxs-lookup"><span data-stu-id="22cfc-106">Attributes</span></span>  
  
|<span data-ttu-id="22cfc-107">属性</span><span class="sxs-lookup"><span data-stu-id="22cfc-107">Attribute</span></span>|<span data-ttu-id="22cfc-108">说明</span><span class="sxs-lookup"><span data-stu-id="22cfc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22cfc-109">type</span><span class="sxs-lookup"><span data-stu-id="22cfc-109">type</span></span>|<span data-ttu-id="22cfc-110">指定服务令牌解析程序的类型。</span><span class="sxs-lookup"><span data-stu-id="22cfc-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="22cfc-111"><xref:System.IdentityModel.Selectors.SecurityTokenResolver>类型或派生自类的类型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="22cfc-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="22cfc-112">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用]。</span><span class="sxs-lookup"><span data-stu-id="22cfc-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="22cfc-113">必需。</span><span class="sxs-lookup"><span data-stu-id="22cfc-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22cfc-114">子元素</span><span class="sxs-lookup"><span data-stu-id="22cfc-114">Child Elements</span></span>  
 <span data-ttu-id="22cfc-115">无</span><span class="sxs-lookup"><span data-stu-id="22cfc-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22cfc-116">父元素</span><span class="sxs-lookup"><span data-stu-id="22cfc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="22cfc-117">元素</span><span class="sxs-lookup"><span data-stu-id="22cfc-117">Element</span></span>|<span data-ttu-id="22cfc-118">描述</span><span class="sxs-lookup"><span data-stu-id="22cfc-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="22cfc-119">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="22cfc-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22cfc-120">注解</span><span class="sxs-lookup"><span data-stu-id="22cfc-120">Remarks</span></span>  
 <span data-ttu-id="22cfc-121">服务令牌解析程序可用于解析传入令牌和消息的加密令牌。</span><span class="sxs-lookup"><span data-stu-id="22cfc-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="22cfc-122">它用于检索应该用于解密传入令牌的密钥。</span><span class="sxs-lookup"><span data-stu-id="22cfc-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="22cfc-123">您必须指定 `type` 属性。</span><span class="sxs-lookup"><span data-stu-id="22cfc-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="22cfc-124">指定的类型可以是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 或从类派生的自定义类型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="22cfc-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="22cfc-125">某些标记处理程序允许您在配置中指定服务令牌解析器设置。</span><span class="sxs-lookup"><span data-stu-id="22cfc-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="22cfc-126">各个标记处理程序上的设置将替代在安全令牌处理程序集合中指定的设置。</span><span class="sxs-lookup"><span data-stu-id="22cfc-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22cfc-127">将 `<serviceTokenResolver>` 元素指定为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已不推荐使用，但仍支持向后兼容。</span><span class="sxs-lookup"><span data-stu-id="22cfc-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="22cfc-128">元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="22cfc-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22cfc-129">示例</span><span class="sxs-lookup"><span data-stu-id="22cfc-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
