---
ms.openlocfilehash: 57f68c10d5d1edc9b8deaca2f4fe7edda2dd69b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619869"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="09474-101">System.ServiceModel.Web.WebServiceHost 对象不再添加默认终结点</span><span class="sxs-lookup"><span data-stu-id="09474-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="09474-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="09474-102">Details</span></span>

<span data-ttu-id="09474-103">如果显式终结点已由应用程序代码添加，则 <xref:System.ServiceModel.Web.WebServiceHost> 对象不再添加默认终结点。</span><span class="sxs-lookup"><span data-stu-id="09474-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="09474-104">建议</span><span class="sxs-lookup"><span data-stu-id="09474-104">Suggestion</span></span>

<span data-ttu-id="09474-105">如果用户希望能够连接到默认终结点，并且其他显式终结点已添加到 <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>，则还应显式添加默认终结点（使用 <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>）。</span><span class="sxs-lookup"><span data-stu-id="09474-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="09474-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="09474-106">Name</span></span>    | <span data-ttu-id="09474-107">“值”</span><span class="sxs-lookup"><span data-stu-id="09474-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="09474-108">范围</span><span class="sxs-lookup"><span data-stu-id="09474-108">Scope</span></span>   |<span data-ttu-id="09474-109">次要</span><span class="sxs-lookup"><span data-stu-id="09474-109">Minor</span></span>|
|<span data-ttu-id="09474-110">Version</span><span class="sxs-lookup"><span data-stu-id="09474-110">Version</span></span>|<span data-ttu-id="09474-111">4.5</span><span class="sxs-lookup"><span data-stu-id="09474-111">4.5</span></span>|
|<span data-ttu-id="09474-112">类型</span><span class="sxs-lookup"><span data-stu-id="09474-112">Type</span></span>|<span data-ttu-id="09474-113">运行时</span><span class="sxs-lookup"><span data-stu-id="09474-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09474-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="09474-114">Affected APIs</span></span>

-<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li></ul>|
