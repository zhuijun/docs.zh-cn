---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251927"
---
# \<remove>
<span data-ttu-id="b109a-101">从标记处理程序集合中删除指定的安全令牌处理程序。</span><span class="sxs-lookup"><span data-stu-id="b109a-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="b109a-102">语法</span><span class="sxs-lookup"><span data-stu-id="b109a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b109a-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b109a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b109a-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b109a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b109a-105">特性</span><span class="sxs-lookup"><span data-stu-id="b109a-105">Attributes</span></span>  
  
|<span data-ttu-id="b109a-106">属性</span><span class="sxs-lookup"><span data-stu-id="b109a-106">Attribute</span></span>|<span data-ttu-id="b109a-107">说明</span><span class="sxs-lookup"><span data-stu-id="b109a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b109a-108">type</span><span class="sxs-lookup"><span data-stu-id="b109a-108">type</span></span>|<span data-ttu-id="b109a-109">要移除的令牌处理程序的 CLR 类型名称。</span><span class="sxs-lookup"><span data-stu-id="b109a-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="b109a-110">有关如何指定属性的详细信息 `type` ，请参阅[自定义类型引用](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="b109a-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="b109a-111">必需。</span><span class="sxs-lookup"><span data-stu-id="b109a-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b109a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b109a-112">Child Elements</span></span>  
 <span data-ttu-id="b109a-113">无</span><span class="sxs-lookup"><span data-stu-id="b109a-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b109a-114">父元素</span><span class="sxs-lookup"><span data-stu-id="b109a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b109a-115">元素</span><span class="sxs-lookup"><span data-stu-id="b109a-115">Element</span></span>|<span data-ttu-id="b109a-116">描述</span><span class="sxs-lookup"><span data-stu-id="b109a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="b109a-117">指定注册到终结点的安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="b109a-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b109a-118">示例</span><span class="sxs-lookup"><span data-stu-id="b109a-118">Example</span></span>  
 <span data-ttu-id="b109a-119">下面的 XML 演示 `<add>` 如何使用和元素将 `<remove>` 默认会话标记处理程序替换为自定义会话标记处理程序。</span><span class="sxs-lookup"><span data-stu-id="b109a-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="b109a-120">XML 是从示例获取的 `ClaimsAwareWebFarm` 。</span><span class="sxs-lookup"><span data-stu-id="b109a-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
