---
ms.openlocfilehash: 207dba9327cfd6debd15c5573697f8950b6c2c95
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218216"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a><span data-ttu-id="bb942-101">默认情况下，TLS 1.x 将 SCH_SEND_AUX_RECORD 标记传递给基础 SCHANNEL API</span><span class="sxs-lookup"><span data-stu-id="bb942-101">TLS 1.x by default passes the SCH_SEND_AUX_RECORD flag to the underlying SCHANNEL API</span></span>

#### <a name="details"></a><span data-ttu-id="bb942-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="bb942-102">Details</span></span>

<span data-ttu-id="bb942-103">使用 TLS 1.x 时，.NET Framework 依赖于基础 Windows SCHANNEL API。</span><span class="sxs-lookup"><span data-stu-id="bb942-103">When using TLS 1.x, the .NET Framework relies on the underlying Windows SCHANNEL API.</span></span> <span data-ttu-id="bb942-104">从 .NET Framework 4.6 开始，[SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) 标记默认传递给 SCHANNEL。</span><span class="sxs-lookup"><span data-stu-id="bb942-104">Starting with .NET Framework 4.6, the [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) flag is passed by default to SCHANNEL.</span></span> <span data-ttu-id="bb942-105">这会导致 SCHANNEL 将要加密的数据拆分为两个单独的记录，第一个为 1 个字节，第二个为 <em>n</em>-1 个字节。在极少数情况下，如果假定数据驻留在一个记录中，则客户端与现有服务器之间的通信会中断。</span><span class="sxs-lookup"><span data-stu-id="bb942-105">This causes SCHANNEL to split data to be encrypted into two separate records, the first as a single byte and the second as <em>n</em>-1 bytes.In rare cases, this breaks communication between clients and existing servers that make the assumption that the data resides in a single record.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bb942-106">建议</span><span class="sxs-lookup"><span data-stu-id="bb942-106">Suggestion</span></span>

<span data-ttu-id="bb942-107">如果此更改中断了与现有服务器的通信，则可以将以下开关添加到应用配置文件的 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素，禁止发送 [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) 标记并还原之前不将数据拆分为单独记录的行为：</span><span class="sxs-lookup"><span data-stu-id="bb942-107">If this change breaks communication with an existing server, you can disable sending the [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) flag and restore the previous behavior of not splitting data into separate records by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="bb942-108">此设置仅用于后向兼容性。</span><span class="sxs-lookup"><span data-stu-id="bb942-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="bb942-109">否则不建议使用它。</span><span class="sxs-lookup"><span data-stu-id="bb942-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="bb942-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="bb942-110">Name</span></span>    | <span data-ttu-id="bb942-111">“值”</span><span class="sxs-lookup"><span data-stu-id="bb942-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bb942-112">范围</span><span class="sxs-lookup"><span data-stu-id="bb942-112">Scope</span></span>   | <span data-ttu-id="bb942-113">边缘</span><span class="sxs-lookup"><span data-stu-id="bb942-113">Edge</span></span>        |
| <span data-ttu-id="bb942-114">Version</span><span class="sxs-lookup"><span data-stu-id="bb942-114">Version</span></span> | <span data-ttu-id="bb942-115">4.6</span><span class="sxs-lookup"><span data-stu-id="bb942-115">4.6</span></span>         |
| <span data-ttu-id="bb942-116">类型</span><span class="sxs-lookup"><span data-stu-id="bb942-116">Type</span></span>    | <span data-ttu-id="bb942-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="bb942-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="bb942-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="bb942-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
