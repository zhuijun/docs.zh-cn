---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770943"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="20382-101">WCF MsmqSecureHashAlgorithm 现在的默认值为 SHA256</span><span class="sxs-lookup"><span data-stu-id="20382-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="20382-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="20382-102">Details</span></span>

<span data-ttu-id="20382-103">自 .NET Framework 4.7.1 起，Msmq 消息 WCF 中的默认消息签名算法为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="20382-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="20382-104">在 .NET Framework 4.7 和更低版本中，默认消息签名算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="20382-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20382-105">建议</span><span class="sxs-lookup"><span data-stu-id="20382-105">Suggestion</span></span>

<span data-ttu-id="20382-106">如果在 .NET Framework 4.7.1 或更高版本中遇到此更改的兼容性问题，可以将以下行添加到 app.config 文件的 `<runtime>` 部分，以选择退出更改：</span><span class="sxs-lookup"><span data-stu-id="20382-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| <span data-ttu-id="20382-107">名称</span><span class="sxs-lookup"><span data-stu-id="20382-107">Name</span></span>    | <span data-ttu-id="20382-108">值</span><span class="sxs-lookup"><span data-stu-id="20382-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="20382-109">范围</span><span class="sxs-lookup"><span data-stu-id="20382-109">Scope</span></span>   | <span data-ttu-id="20382-110">次要</span><span class="sxs-lookup"><span data-stu-id="20382-110">Minor</span></span>   |
| <span data-ttu-id="20382-111">Version</span><span class="sxs-lookup"><span data-stu-id="20382-111">Version</span></span> | <span data-ttu-id="20382-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="20382-112">4.7.1</span></span>   |
| <span data-ttu-id="20382-113">类型</span><span class="sxs-lookup"><span data-stu-id="20382-113">Type</span></span>    | <span data-ttu-id="20382-114">运行时</span><span class="sxs-lookup"><span data-stu-id="20382-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="20382-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="20382-115">Affected APIs</span></span>

<span data-ttu-id="20382-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="20382-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
