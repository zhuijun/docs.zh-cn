---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617520"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="8084e-101">HttpRuntime.AppDomainAppPath 引发 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="8084e-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="8084e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8084e-102">Details</span></span>

<span data-ttu-id="8084e-103">在 .NET Framework 4.6.2 中，当检索包含空字符的 `P:System.Web.HttpRuntime.AppDomainAppPath` 值时，运行时会引发 `T:System.NullReferenceException`。在 .NET Framework 4.6.1 及早期版本中，运行时将引发 `T:System.ArgumentNullException`。</span><span class="sxs-lookup"><span data-stu-id="8084e-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8084e-104">建议</span><span class="sxs-lookup"><span data-stu-id="8084e-104">Suggestion</span></span>

<span data-ttu-id="8084e-105">可执行以下任一操作来应对此更改：</span><span class="sxs-lookup"><span data-stu-id="8084e-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="8084e-106">如果应用程序是在 .NET Framework 4.6.2 上运行，请处理 `T:System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="8084e-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="8084e-107">升级到 .NET Framework 4.7，这将还原以前的行为并引发 `T:System.ArgumentNullException`。</span><span class="sxs-lookup"><span data-stu-id="8084e-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="8084e-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="8084e-108">Name</span></span>    | <span data-ttu-id="8084e-109">“值”</span><span class="sxs-lookup"><span data-stu-id="8084e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8084e-110">范围</span><span class="sxs-lookup"><span data-stu-id="8084e-110">Scope</span></span>   | <span data-ttu-id="8084e-111">边缘</span><span class="sxs-lookup"><span data-stu-id="8084e-111">Edge</span></span>        |
| <span data-ttu-id="8084e-112">Version</span><span class="sxs-lookup"><span data-stu-id="8084e-112">Version</span></span> | <span data-ttu-id="8084e-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8084e-113">4.6.2</span></span>       |
| <span data-ttu-id="8084e-114">类型</span><span class="sxs-lookup"><span data-stu-id="8084e-114">Type</span></span>    | <span data-ttu-id="8084e-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="8084e-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8084e-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8084e-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
