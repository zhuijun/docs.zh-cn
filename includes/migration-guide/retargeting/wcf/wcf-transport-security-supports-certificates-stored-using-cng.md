---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614358"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="82064-101">WCF 传输安全性支持使用 CNG 存储的证书</span><span class="sxs-lookup"><span data-stu-id="82064-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="82064-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="82064-102">Details</span></span>

<span data-ttu-id="82064-103">从面向 .NET Framework 4.6.2 的应用起，WCF 传输安全性支持使用 Windows 加密库 (CNG) 存储的证书。</span><span class="sxs-lookup"><span data-stu-id="82064-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="82064-104">此支持仅限于将证书与指数长度不超过 32 位的公钥结合使用。</span><span class="sxs-lookup"><span data-stu-id="82064-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="82064-105">当应用程序面向 .NET Framework 4.6.2 时，此功能默认启用。在旧版 .NET framework 中，尝试将 X509 证书与 CSG 密钥存储提供程序结合使用会引发异常。</span><span class="sxs-lookup"><span data-stu-id="82064-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="82064-106">建议</span><span class="sxs-lookup"><span data-stu-id="82064-106">Suggestion</span></span>

<span data-ttu-id="82064-107">应用如果面向 .NET Framework 4.6.1 和更早版本，但在 .NET Framework 4.6.2 上运行，则可通过将以下行添加到 app.config 或 web.config 文件的 `<runtime>` 部分来启用对 CNG 证书的支持：</span><span class="sxs-lookup"><span data-stu-id="82064-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="82064-108">也可以使用以下代码以编程方式完成此操作：</span><span class="sxs-lookup"><span data-stu-id="82064-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="82064-109">请注意，鉴于有此更改，将不再执行任何依赖无法尝试使用 CNG 证书启动安全通信的异常处理代码。</span><span class="sxs-lookup"><span data-stu-id="82064-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="82064-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="82064-110">Name</span></span>    | <span data-ttu-id="82064-111">“值”</span><span class="sxs-lookup"><span data-stu-id="82064-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="82064-112">范围</span><span class="sxs-lookup"><span data-stu-id="82064-112">Scope</span></span>   | <span data-ttu-id="82064-113">次要</span><span class="sxs-lookup"><span data-stu-id="82064-113">Minor</span></span>       |
| <span data-ttu-id="82064-114">Version</span><span class="sxs-lookup"><span data-stu-id="82064-114">Version</span></span> | <span data-ttu-id="82064-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="82064-115">4.6.2</span></span>       |
| <span data-ttu-id="82064-116">类型</span><span class="sxs-lookup"><span data-stu-id="82064-116">Type</span></span>    | <span data-ttu-id="82064-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="82064-117">Retargeting</span></span> |
