---
ms.openlocfilehash: cf34c5df1badcfd86d8a07bafdf1b759234712e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496670"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="40d47-101">HttpRequest.ContentEncoding 属性禁止使用 UTF7</span><span class="sxs-lookup"><span data-stu-id="40d47-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="40d47-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="40d47-102">Details</span></span>

<span data-ttu-id="40d47-103">从 .NET Framework 4.5 开始，<xref:System.Web.HttpRequest?displayProperty=fullName> 正文禁止使用 UTF-7 编码。</span><span class="sxs-lookup"><span data-stu-id="40d47-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="40d47-104">在某些情况下，取决于传入的 UTF-7 数据的应用程序数据将不会正确解码。</span><span class="sxs-lookup"><span data-stu-id="40d47-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="40d47-105">建议</span><span class="sxs-lookup"><span data-stu-id="40d47-105">Suggestion</span></span>

<span data-ttu-id="40d47-106">理想情况下，应更新应用程序，使其在 <xref:System.Web.HttpRequest?displayProperty=fullName> 中不使用 UTF-7 编码。</span><span class="sxs-lookup"><span data-stu-id="40d47-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="40d47-107">或者，可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 元素的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 属性还原旧行为。</span><span class="sxs-lookup"><span data-stu-id="40d47-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="40d47-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="40d47-108">Name</span></span>    | <span data-ttu-id="40d47-109">“值”</span><span class="sxs-lookup"><span data-stu-id="40d47-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="40d47-110">范围</span><span class="sxs-lookup"><span data-stu-id="40d47-110">Scope</span></span>   |<span data-ttu-id="40d47-111">边缘</span><span class="sxs-lookup"><span data-stu-id="40d47-111">Edge</span></span>|
|<span data-ttu-id="40d47-112">Version</span><span class="sxs-lookup"><span data-stu-id="40d47-112">Version</span></span>|<span data-ttu-id="40d47-113">4.5</span><span class="sxs-lookup"><span data-stu-id="40d47-113">4.5</span></span>|
|<span data-ttu-id="40d47-114">类型</span><span class="sxs-lookup"><span data-stu-id="40d47-114">Type</span></span>|<span data-ttu-id="40d47-115">运行时</span><span class="sxs-lookup"><span data-stu-id="40d47-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="40d47-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="40d47-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.ContentEncoding`

-->
