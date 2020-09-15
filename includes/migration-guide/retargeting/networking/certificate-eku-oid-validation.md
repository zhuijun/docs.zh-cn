---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615608"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="07158-101">证书 EKU OID 验证</span><span class="sxs-lookup"><span data-stu-id="07158-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="07158-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="07158-102">Details</span></span>

<span data-ttu-id="07158-103">从 .NET Framework 4.6 开始，<xref:System.Net.Security.SslStream> 或 <xref:System.Net.ServicePointManager> 类执行增强型密钥使用 (EKU) 对象标识符 (OID) 验证。</span><span class="sxs-lookup"><span data-stu-id="07158-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="07158-104">增强型密钥使用 (EKU) 扩展是指示使用密钥的应用程序的对象标识符 (OID) 的集合。</span><span class="sxs-lookup"><span data-stu-id="07158-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="07158-105">EKU OID 验证使用远程证书回叫来确保远程证书具有用于预期目的的正确 OID。</span><span class="sxs-lookup"><span data-stu-id="07158-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="07158-106">建议</span><span class="sxs-lookup"><span data-stu-id="07158-106">Suggestion</span></span>

<span data-ttu-id="07158-107">如果无需此更改，则可通过将以下开关添加到应用配置文件的 [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 中的 [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 来禁用证书 EKU OID 验证：</span><span class="sxs-lookup"><span data-stu-id="07158-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="07158-108">此设置仅用于后向兼容性。</span><span class="sxs-lookup"><span data-stu-id="07158-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="07158-109">否则不建议使用它。</span><span class="sxs-lookup"><span data-stu-id="07158-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="07158-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="07158-110">Name</span></span>    | <span data-ttu-id="07158-111">“值”</span><span class="sxs-lookup"><span data-stu-id="07158-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="07158-112">范围</span><span class="sxs-lookup"><span data-stu-id="07158-112">Scope</span></span>   | <span data-ttu-id="07158-113">次要</span><span class="sxs-lookup"><span data-stu-id="07158-113">Minor</span></span>       |
| <span data-ttu-id="07158-114">Version</span><span class="sxs-lookup"><span data-stu-id="07158-114">Version</span></span> | <span data-ttu-id="07158-115">4.6</span><span class="sxs-lookup"><span data-stu-id="07158-115">4.6</span></span>         |
| <span data-ttu-id="07158-116">类型</span><span class="sxs-lookup"><span data-stu-id="07158-116">Type</span></span>    | <span data-ttu-id="07158-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="07158-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="07158-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="07158-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
