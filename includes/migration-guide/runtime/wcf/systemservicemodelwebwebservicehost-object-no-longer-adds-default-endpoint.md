---
ms.openlocfilehash: 0c3876d30a80501a89f3a37ce24e2f71122c1b44
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496668"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="c375d-101">System.ServiceModel.Web.WebServiceHost 对象不再添加默认终结点</span><span class="sxs-lookup"><span data-stu-id="c375d-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="c375d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c375d-102">Details</span></span>

<span data-ttu-id="c375d-103">如果显式终结点已由应用程序代码添加，则 <xref:System.ServiceModel.Web.WebServiceHost> 对象不再添加默认终结点。</span><span class="sxs-lookup"><span data-stu-id="c375d-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c375d-104">建议</span><span class="sxs-lookup"><span data-stu-id="c375d-104">Suggestion</span></span>

<span data-ttu-id="c375d-105">如果用户希望能够连接到默认终结点，并且其他显式终结点已添加到 <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>，则还应显式添加默认终结点（使用 <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>）。</span><span class="sxs-lookup"><span data-stu-id="c375d-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="c375d-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="c375d-106">Name</span></span>    | <span data-ttu-id="c375d-107">“值”</span><span class="sxs-lookup"><span data-stu-id="c375d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c375d-108">范围</span><span class="sxs-lookup"><span data-stu-id="c375d-108">Scope</span></span>   |<span data-ttu-id="c375d-109">次要</span><span class="sxs-lookup"><span data-stu-id="c375d-109">Minor</span></span>|
|<span data-ttu-id="c375d-110">Version</span><span class="sxs-lookup"><span data-stu-id="c375d-110">Version</span></span>|<span data-ttu-id="c375d-111">4.5</span><span class="sxs-lookup"><span data-stu-id="c375d-111">4.5</span></span>|
|<span data-ttu-id="c375d-112">类型</span><span class="sxs-lookup"><span data-stu-id="c375d-112">Type</span></span>|<span data-ttu-id="c375d-113">运行时</span><span class="sxs-lookup"><span data-stu-id="c375d-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c375d-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c375d-114">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`

-->
