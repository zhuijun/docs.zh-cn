---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497144"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="73a50-101">MEF 目录实现 IEnumerable，因此不能再用于创建序列化程序</span><span class="sxs-lookup"><span data-stu-id="73a50-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="73a50-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="73a50-102">Details</span></span>

<span data-ttu-id="73a50-103">从 .NET Framework 4.5 开始，MEF 目录实现 IEnumerable，因此不能再用于创建序列化程序（<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 对象）。</span><span class="sxs-lookup"><span data-stu-id="73a50-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="73a50-104">尝试对 MEF 目录进行序列化会引发异常。</span><span class="sxs-lookup"><span data-stu-id="73a50-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73a50-105">建议</span><span class="sxs-lookup"><span data-stu-id="73a50-105">Suggestion</span></span>

<span data-ttu-id="73a50-106">不能再使用 MEF 创建序列化程序</span><span class="sxs-lookup"><span data-stu-id="73a50-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="73a50-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="73a50-107">Name</span></span>    | <span data-ttu-id="73a50-108">“值”</span><span class="sxs-lookup"><span data-stu-id="73a50-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="73a50-109">范围</span><span class="sxs-lookup"><span data-stu-id="73a50-109">Scope</span></span>   |<span data-ttu-id="73a50-110">主要</span><span class="sxs-lookup"><span data-stu-id="73a50-110">Major</span></span>|
|<span data-ttu-id="73a50-111">Version</span><span class="sxs-lookup"><span data-stu-id="73a50-111">Version</span></span>|<span data-ttu-id="73a50-112">4.5</span><span class="sxs-lookup"><span data-stu-id="73a50-112">4.5</span></span>|
|<span data-ttu-id="73a50-113">类型</span><span class="sxs-lookup"><span data-stu-id="73a50-113">Type</span></span>|<span data-ttu-id="73a50-114">运行时</span><span class="sxs-lookup"><span data-stu-id="73a50-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="73a50-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="73a50-115">Affected APIs</span></span>

<span data-ttu-id="73a50-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="73a50-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
