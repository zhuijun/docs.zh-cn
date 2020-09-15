---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614370"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="99662-101">ServiceBase 不传播 OnStart 异常</span><span class="sxs-lookup"><span data-stu-id="99662-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="99662-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="99662-102">Details</span></span>

<span data-ttu-id="99662-103">在 .NET Framework 4.7 和更早版本中，服务启动时引发的异常不会传播到 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> 的调用方。</span><span class="sxs-lookup"><span data-stu-id="99662-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="99662-104">从面向.NET Framework 4.7.1 的应用程序开始，针对启动失败的服务，运行时会将异常传播到 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="99662-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="99662-105">建议</span><span class="sxs-lookup"><span data-stu-id="99662-105">Suggestion</span></span>

<span data-ttu-id="99662-106">服务启动时，如果出现异常，将传播该异常。</span><span class="sxs-lookup"><span data-stu-id="99662-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="99662-107">这有助于诊断服务启动失败的事例。</span><span class="sxs-lookup"><span data-stu-id="99662-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="99662-108">如果不需要此行为，可在应用程序配置文件的 &lt;runtime&gt; 部分中添加以下 &lt;AppContextSwitchOverrides&gt; 元素，从而选择弃用此行为：</span><span class="sxs-lookup"><span data-stu-id="99662-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="99662-109">如果应用程序面向早于 4.7.1 的版本，但你需要此行为，请将以下 &lt;AppContextSwitchOverrides&gt; 元素添加到应用程序配置文件的 &lt;runtime&gt; 部分：</span><span class="sxs-lookup"><span data-stu-id="99662-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="99662-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="99662-110">Name</span></span>    | <span data-ttu-id="99662-111">“值”</span><span class="sxs-lookup"><span data-stu-id="99662-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="99662-112">范围</span><span class="sxs-lookup"><span data-stu-id="99662-112">Scope</span></span>   | <span data-ttu-id="99662-113">次要</span><span class="sxs-lookup"><span data-stu-id="99662-113">Minor</span></span>       |
| <span data-ttu-id="99662-114">Version</span><span class="sxs-lookup"><span data-stu-id="99662-114">Version</span></span> | <span data-ttu-id="99662-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="99662-115">4.7.1</span></span>       |
| <span data-ttu-id="99662-116">类型</span><span class="sxs-lookup"><span data-stu-id="99662-116">Type</span></span>    | <span data-ttu-id="99662-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="99662-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="99662-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="99662-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
