---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619825"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="a3daa-101">不应在自定义功能文件中使用 IPad，因为它现在是浏览器功能</span><span class="sxs-lookup"><span data-stu-id="a3daa-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="a3daa-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a3daa-102">Details</span></span>

<span data-ttu-id="a3daa-103">自 .NET Framework 4.5 起，iPad 是默认 ASP.NET 浏览器功能文件中的标识符，所以它不应在自定义功能文件中使用</span><span class="sxs-lookup"><span data-stu-id="a3daa-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a3daa-104">建议</span><span class="sxs-lookup"><span data-stu-id="a3daa-104">Suggestion</span></span>

<span data-ttu-id="a3daa-105">如果需要特定于 iPad 的功能，则需要修改 iPad 行为，具体方法为 设置预定义网关 refID &quot;IPad&quot; 上的功能，而不是通过用户代理匹配生成新的 &quot;IPad&quot; ID。</span><span class="sxs-lookup"><span data-stu-id="a3daa-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="a3daa-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="a3daa-106">Name</span></span>    | <span data-ttu-id="a3daa-107">“值”</span><span class="sxs-lookup"><span data-stu-id="a3daa-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a3daa-108">范围</span><span class="sxs-lookup"><span data-stu-id="a3daa-108">Scope</span></span>   |<span data-ttu-id="a3daa-109">边缘</span><span class="sxs-lookup"><span data-stu-id="a3daa-109">Edge</span></span>|
|<span data-ttu-id="a3daa-110">Version</span><span class="sxs-lookup"><span data-stu-id="a3daa-110">Version</span></span>|<span data-ttu-id="a3daa-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a3daa-111">4.5</span></span>|
|<span data-ttu-id="a3daa-112">类型</span><span class="sxs-lookup"><span data-stu-id="a3daa-112">Type</span></span>|<span data-ttu-id="a3daa-113">运行时</span><span class="sxs-lookup"><span data-stu-id="a3daa-113">Runtime</span></span>|
