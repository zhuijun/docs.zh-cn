---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 27bf9e380df1586b42cbe96a628a794364fae743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204965"
---
# \<behaviorExtensions>

<span data-ttu-id="7a681-101">用户可以使用行为扩展来创建用户定义的行为元素。</span><span class="sxs-lookup"><span data-stu-id="7a681-101">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="7a681-102">这些元素可与标准的 Windows Communication Foundation (WCF) 行为元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="7a681-102">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="7a681-103">`behaviorExtensions` 节定义了元素，使其可用于配置中。</span><span class="sxs-lookup"><span data-stu-id="7a681-103">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="7a681-104">下面是一个典型的行为扩展示例。</span><span class="sxs-lookup"><span data-stu-id="7a681-104">Here is an example of a typical behavior extension.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="7a681-105">若要向元素添加配置功能，需要编写和注册配置元素。</span><span class="sxs-lookup"><span data-stu-id="7a681-105">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="7a681-106">有关这方面的更多信息，请参见 <xref:System.Configuration> 文档。</span><span class="sxs-lookup"><span data-stu-id="7a681-106">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="7a681-107">在定义元素及其配置类型之后，可以使用扩展，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="7a681-107">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a><span data-ttu-id="7a681-108">安全性</span><span class="sxs-lookup"><span data-stu-id="7a681-108">Security</span></span>  

 <span data-ttu-id="7a681-109">强烈建议在 `machine.config` 和 `app.config` 文件中注册类型时使用完全限定的程序集名称。</span><span class="sxs-lookup"><span data-stu-id="7a681-109">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="7a681-110">如果没有唯一定义类型，则 CLR 类型加载程序将按照指定的顺序在以下位置中搜索类型：</span><span class="sxs-lookup"><span data-stu-id="7a681-110">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="7a681-111">如果已经知道类型的程序集，则加载程序将搜索配置文件的重定向位置、GAC、使用配置信息的当前程序集以及应用程序基目录。</span><span class="sxs-lookup"><span data-stu-id="7a681-111">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="7a681-112">如果程序集未知，则加载程序将搜索当前程序集、mscorlib 以及 `TypeResolve` 事件处理程序返回的位置。</span><span class="sxs-lookup"><span data-stu-id="7a681-112">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="7a681-113">通过使用“类型转发”机制和 AppDomain.TypeResolve 事件之类的挂钩，可以修改此 CLR 搜索顺序。</span><span class="sxs-lookup"><span data-stu-id="7a681-113">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="7a681-114">攻击者可以利用 CLR 搜索顺序来执行未授权的代码。</span><span class="sxs-lookup"><span data-stu-id="7a681-114">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="7a681-115">使用完全限定的（强）名称可唯一标识某个类型，进一步提高系统的安全性。</span><span class="sxs-lookup"><span data-stu-id="7a681-115">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="7a681-116">有关详细信息，请参阅 [运行时如何定位程序集](../../../deployment/how-the-runtime-locates-assemblies.md) 和 <xref:System.AppDomain.TypeResolve> 。</span><span class="sxs-lookup"><span data-stu-id="7a681-116">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a681-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a681-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="7a681-118">使用行为配置和扩展运行时</span><span class="sxs-lookup"><span data-stu-id="7a681-118">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
