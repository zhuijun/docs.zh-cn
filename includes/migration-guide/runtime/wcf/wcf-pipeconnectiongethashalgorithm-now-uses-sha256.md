---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770952"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="25dd3-101">WCF PipeConnection.GetHashAlgorithm 现在使用 SHA256</span><span class="sxs-lookup"><span data-stu-id="25dd3-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="25dd3-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="25dd3-102">Details</span></span>

<span data-ttu-id="25dd3-103">从 .NET Framework 4.7.1 开始，Windows Communication Foundation 使用 SHA256 哈希为命名管道生成随机名称。</span><span class="sxs-lookup"><span data-stu-id="25dd3-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="25dd3-104">在 .NET Framework 4.7 和更早版本中，它使用 SHA1 哈希。</span><span class="sxs-lookup"><span data-stu-id="25dd3-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25dd3-105">建议</span><span class="sxs-lookup"><span data-stu-id="25dd3-105">Suggestion</span></span>

<span data-ttu-id="25dd3-106">如果在 .NET Framework 4.7.1 或更高版本中遇到此更改的兼容性问题，则可以通过将以下行添加到 app.config 文件的 `<runtime>` 部分选择弃用此更改：</span><span class="sxs-lookup"><span data-stu-id="25dd3-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

Not detectable via API analysis.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
