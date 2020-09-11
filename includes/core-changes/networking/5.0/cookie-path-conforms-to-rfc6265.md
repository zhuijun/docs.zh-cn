---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465503"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="4f83d-101">Cookie 路径处理现在符合 RFC 6265</span><span class="sxs-lookup"><span data-stu-id="4f83d-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="4f83d-102">[RFC 6265](https://tools.ietf.org/html/rfc6265) 中定义的路径处理算法是针对 <xref:System.Net.Cookie> 和 <xref:System.Net.CookieContainer> 类实现的。</span><span class="sxs-lookup"><span data-stu-id="4f83d-102">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f83d-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="4f83d-103">Version introduced</span></span>

<span data-ttu-id="4f83d-104">5.0</span><span class="sxs-lookup"><span data-stu-id="4f83d-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f83d-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="4f83d-105">Change description</span></span>

- <span data-ttu-id="4f83d-106">无需再将 <xref:System.Net.Cookie.Path> 属性作为请求路径的前缀。</span><span class="sxs-lookup"><span data-stu-id="4f83d-106">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="4f83d-107"><xref:System.Net.Cookie.Path> 的默认值的计算和路径匹配算法是按照 RFC 6265 的[第 5.1.4 节](https://tools.ietf.org/html/rfc6265#section-5.1.4)中的定义实现的。</span><span class="sxs-lookup"><span data-stu-id="4f83d-107">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f83d-108">建议操作</span><span class="sxs-lookup"><span data-stu-id="4f83d-108">Recommended action</span></span>

<span data-ttu-id="4f83d-109">在大多数情况下，无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="4f83d-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="4f83d-110">但是，如果代码依赖于 <xref:System.Net.Cookie.Path> 验证，则需要在代码中实现所需的验证。</span><span class="sxs-lookup"><span data-stu-id="4f83d-110">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="4f83d-111">如果代码依赖于 <xref:System.Net.Cookie.Path> 的默认值计算，请考虑手动提供 <xref:System.Net.Cookie.Path> 值，而不使用默认值。</span><span class="sxs-lookup"><span data-stu-id="4f83d-111">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="4f83d-112">类别</span><span class="sxs-lookup"><span data-stu-id="4f83d-112">Category</span></span>

<span data-ttu-id="4f83d-113">网络</span><span class="sxs-lookup"><span data-stu-id="4f83d-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f83d-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4f83d-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
