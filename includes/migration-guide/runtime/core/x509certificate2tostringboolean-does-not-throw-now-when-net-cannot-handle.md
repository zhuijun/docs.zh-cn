---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621140"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="22a30-101">现在，当 .NET 无法处理证书时，不会引发 X509Certificate2.ToString(Boolean)</span><span class="sxs-lookup"><span data-stu-id="22a30-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="22a30-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="22a30-102">Details</span></span>

<span data-ttu-id="22a30-103">在 .NET Framework 4.5.2 及更早版本中，如果为详细参数传递了 <code>true</code>，并且安装了 .NET Framework 不支持的证书，则会引发此方法。</span><span class="sxs-lookup"><span data-stu-id="22a30-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="22a30-104">现在，该方法将取得成功，并返回省略证书无法访问部分的有效字符串。</span><span class="sxs-lookup"><span data-stu-id="22a30-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="22a30-105">建议</span><span class="sxs-lookup"><span data-stu-id="22a30-105">Suggestion</span></span>

<span data-ttu-id="22a30-106">应更新任何依赖 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> 的代码，以希望返回的字符串会排除在某些情况下，API 之前曾引发的某些证书数据（例如公钥、私钥和扩展）。</span><span class="sxs-lookup"><span data-stu-id="22a30-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="22a30-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="22a30-107">Name</span></span>    | <span data-ttu-id="22a30-108">值</span><span class="sxs-lookup"><span data-stu-id="22a30-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="22a30-109">范围</span><span class="sxs-lookup"><span data-stu-id="22a30-109">Scope</span></span>   |<span data-ttu-id="22a30-110">边缘</span><span class="sxs-lookup"><span data-stu-id="22a30-110">Edge</span></span>|
|<span data-ttu-id="22a30-111">Version</span><span class="sxs-lookup"><span data-stu-id="22a30-111">Version</span></span>|<span data-ttu-id="22a30-112">4.6</span><span class="sxs-lookup"><span data-stu-id="22a30-112">4.6</span></span>|
|<span data-ttu-id="22a30-113">类型</span><span class="sxs-lookup"><span data-stu-id="22a30-113">Type</span></span>|<span data-ttu-id="22a30-114">运行时</span><span class="sxs-lookup"><span data-stu-id="22a30-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22a30-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="22a30-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
