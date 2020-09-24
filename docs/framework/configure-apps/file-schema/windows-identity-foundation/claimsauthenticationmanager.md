---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 9e099b8de486631702548b8a035a46a7e0f4eb30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158469"
---
# \<claimsAuthenticationManager>

<span data-ttu-id="2b37c-101">为传入声明注册声明身份验证管理器。</span><span class="sxs-lookup"><span data-stu-id="2b37c-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="2b37c-102">语法</span><span class="sxs-lookup"><span data-stu-id="2b37c-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b37c-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2b37c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="2b37c-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2b37c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b37c-105">特性</span><span class="sxs-lookup"><span data-stu-id="2b37c-105">Attributes</span></span>  
  
|<span data-ttu-id="2b37c-106">属性</span><span class="sxs-lookup"><span data-stu-id="2b37c-106">Attribute</span></span>|<span data-ttu-id="2b37c-107">说明</span><span class="sxs-lookup"><span data-stu-id="2b37c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b37c-108">type</span><span class="sxs-lookup"><span data-stu-id="2b37c-108">type</span></span>|<span data-ttu-id="2b37c-109">指定从类派生的自定义类型 <xref:System.Security.Claims.ClaimsAuthenticationManager> 。</span><span class="sxs-lookup"><span data-stu-id="2b37c-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="2b37c-110">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用]。</span><span class="sxs-lookup"><span data-stu-id="2b37c-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b37c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2b37c-111">Child Elements</span></span>  

 <span data-ttu-id="2b37c-112">如果没有 `type` 属性，或者如果 `type` 特性引用 <xref:System.Security.Claims.ClaimsAuthenticationManager> 类，则 `<claimsAuthenticationManager>` 元素不采用子元素; 但是，从派生的类 <xref:System.Security.Claims.ClaimsAuthenticationManager> 可以定义子配置元素。</span><span class="sxs-lookup"><span data-stu-id="2b37c-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b37c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="2b37c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2b37c-114">元素</span><span class="sxs-lookup"><span data-stu-id="2b37c-114">Element</span></span>|<span data-ttu-id="2b37c-115">描述</span><span class="sxs-lookup"><span data-stu-id="2b37c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="2b37c-116">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="2b37c-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b37c-117">备注</span><span class="sxs-lookup"><span data-stu-id="2b37c-117">Remarks</span></span>  

 <span data-ttu-id="2b37c-118">通过类提供的默认行为会 <xref:System.Security.Claims.ClaimsAuthenticationManager> 回显传入声明。</span><span class="sxs-lookup"><span data-stu-id="2b37c-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="2b37c-119">如果未 `type` 指定任何特性或 `type` 特性指定了 <xref:System.Security.Claims.ClaimsAuthenticationManager> 类，则元素不 `<claimsAuthenticationManager>` 采用子元素。</span><span class="sxs-lookup"><span data-stu-id="2b37c-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="2b37c-120">可以指定 `type` 用于注册派生自类的类型的属性， <xref:System.Security.Claims.ClaimsAuthenticationManager> 以实现自定义行为。</span><span class="sxs-lookup"><span data-stu-id="2b37c-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="2b37c-121">派生类可以 `<claimsAuthenticationManager>` 通过重写 <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> 方法来处理这些元素，从而支持通过元素的子元素进行的配置。</span><span class="sxs-lookup"><span data-stu-id="2b37c-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="2b37c-122">为子元素定义的架构位于类的设计器中。</span><span class="sxs-lookup"><span data-stu-id="2b37c-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="2b37c-123">`<claimsAuthenticationManager>`元素设置 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="2b37c-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b37c-124">示例</span><span class="sxs-lookup"><span data-stu-id="2b37c-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
