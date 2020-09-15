---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614374"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="8a475-101">使用 DataContractJsonSerializer 控制字符的序列化现在与 ECMAScript V6 和 V8 兼容</span><span class="sxs-lookup"><span data-stu-id="8a475-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="8a475-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8a475-102">Details</span></span>

<span data-ttu-id="8a475-103">在 .NET Framework 4.6.2 及更低版本中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> 未按与 ECMAScript V6 和 V8 标准兼容的方式对一些特殊控制字符（如 \b、\f 和 \t）进行序列化。</span><span class="sxs-lookup"><span data-stu-id="8a475-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="8a475-104">从 .NET Framework 4.7 开始，这些控制字符的序列化与 ECMAScript V6 和 V8 兼容。</span><span class="sxs-lookup"><span data-stu-id="8a475-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8a475-105">建议</span><span class="sxs-lookup"><span data-stu-id="8a475-105">Suggestion</span></span>

<span data-ttu-id="8a475-106">对面向 .NET Framework 4.7 的应用，默认启用此功能。</span><span class="sxs-lookup"><span data-stu-id="8a475-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="8a475-107">如果不需要此行为，可以在 app.config 或 web.config 文件的 `<runtime>` 部分中添加下面的代码行，从而选择禁用此功能：</span><span class="sxs-lookup"><span data-stu-id="8a475-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="8a475-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="8a475-108">Name</span></span>    | <span data-ttu-id="8a475-109">“值”</span><span class="sxs-lookup"><span data-stu-id="8a475-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8a475-110">范围</span><span class="sxs-lookup"><span data-stu-id="8a475-110">Scope</span></span>   | <span data-ttu-id="8a475-111">边缘</span><span class="sxs-lookup"><span data-stu-id="8a475-111">Edge</span></span>        |
| <span data-ttu-id="8a475-112">Version</span><span class="sxs-lookup"><span data-stu-id="8a475-112">Version</span></span> | <span data-ttu-id="8a475-113">4.7</span><span class="sxs-lookup"><span data-stu-id="8a475-113">4.7</span></span>         |
| <span data-ttu-id="8a475-114">类型</span><span class="sxs-lookup"><span data-stu-id="8a475-114">Type</span></span>    | <span data-ttu-id="8a475-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="8a475-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8a475-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8a475-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
