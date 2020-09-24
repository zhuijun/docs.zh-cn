---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: c4ba7b6f2a9b9092c5f24d424c6de2b0f510ac88
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164995"
---
# \<remove>

<span data-ttu-id="774b9-101">从标记处理程序集合中删除指定的安全令牌处理程序。</span><span class="sxs-lookup"><span data-stu-id="774b9-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="774b9-102">语法</span><span class="sxs-lookup"><span data-stu-id="774b9-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="774b9-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="774b9-103">Attributes and Elements</span></span>  

 <span data-ttu-id="774b9-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="774b9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="774b9-105">特性</span><span class="sxs-lookup"><span data-stu-id="774b9-105">Attributes</span></span>  
  
|<span data-ttu-id="774b9-106">属性</span><span class="sxs-lookup"><span data-stu-id="774b9-106">Attribute</span></span>|<span data-ttu-id="774b9-107">说明</span><span class="sxs-lookup"><span data-stu-id="774b9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="774b9-108">type</span><span class="sxs-lookup"><span data-stu-id="774b9-108">type</span></span>|<span data-ttu-id="774b9-109">要移除的令牌处理程序的 CLR 类型名称。</span><span class="sxs-lookup"><span data-stu-id="774b9-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="774b9-110">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="774b9-110">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="774b9-111">必需。</span><span class="sxs-lookup"><span data-stu-id="774b9-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="774b9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="774b9-112">Child Elements</span></span>  

 <span data-ttu-id="774b9-113">无</span><span class="sxs-lookup"><span data-stu-id="774b9-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="774b9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="774b9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="774b9-115">元素</span><span class="sxs-lookup"><span data-stu-id="774b9-115">Element</span></span>|<span data-ttu-id="774b9-116">描述</span><span class="sxs-lookup"><span data-stu-id="774b9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="774b9-117">指定注册到终结点的安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="774b9-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="774b9-118">示例</span><span class="sxs-lookup"><span data-stu-id="774b9-118">Example</span></span>  

 <span data-ttu-id="774b9-119">下面的 XML 演示 `<add>` 如何使用和元素将 `<remove>` 默认会话标记处理程序替换为自定义会话标记处理程序。</span><span class="sxs-lookup"><span data-stu-id="774b9-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="774b9-120">XML 是从示例获取的 `ClaimsAwareWebFarm` 。</span><span class="sxs-lookup"><span data-stu-id="774b9-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
