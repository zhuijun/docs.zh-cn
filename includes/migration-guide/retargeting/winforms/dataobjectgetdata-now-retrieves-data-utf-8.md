---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616024"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a><span data-ttu-id="7f081-101">DataObject.GetData 现在将数据检索为 UTF-8</span><span class="sxs-lookup"><span data-stu-id="7f081-101">DataObject.GetData now retrieves data as UTF-8</span></span>

#### <a name="details"></a><span data-ttu-id="7f081-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="7f081-102">Details</span></span>

<span data-ttu-id="7f081-103">对于面向 .NET Framework 4 或者在 .NET Framework 4.5.1 或更早版本上运行的应用，`DataObject.GetData` 将 HTML 格式的数据检索为 ASCII 字符串。</span><span class="sxs-lookup"><span data-stu-id="7f081-103">For apps that target the .NET Framework 4 or that run on the .NET Framework 4.5.1 or earlier versions, `DataObject.GetData` retrieves HTML-formatted data as an ASCII string.</span></span> <span data-ttu-id="7f081-104">因此，非 ASCII 字符（ASCII 代码大于 0x7F 的字符）由两个随机字符表示。</span><span class="sxs-lookup"><span data-stu-id="7f081-104">As a result, non-ASCII characters (characters whose ASCII codes are greater than 0x7F) are represented by two random characters.</span></span><p/><span data-ttu-id="7f081-105">对于面向 .NET Framework 4.5 或更高版本以及在 .NET Framework 4.5.2 上运行的应用，`DataObject.GetData` 将 HTML 格式的数据检索为 UTF-8，从而可以正确表示大于 0x7F 的字符。</span><span class="sxs-lookup"><span data-stu-id="7f081-105">For apps that target the .NET Framework 4.5 or later and run on the .NET Framework 4.5.2, `DataObject.GetData` retrieves HTML-formatted data as UTF-8, which represents characters greater than 0x7F correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7f081-106">建议</span><span class="sxs-lookup"><span data-stu-id="7f081-106">Suggestion</span></span>

<span data-ttu-id="7f081-107">如果使用 HTML 格式的字符串实现了编码问题的解决方法（例如，通过将其传递到 <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 来显式编码从剪贴板检索的 HTML 字符串），而且要将应用的目标从版本 4 重定为 4.5，则应该删除该解决方法。如果出于某种原因需要使用以前的版本，该应用可面向 .NET Framework 4.0 来获取该行为。</span><span class="sxs-lookup"><span data-stu-id="7f081-107">If you implemented a workaround for the encoding problem with HTML-formatted strings (for example, by explicitly encoding the HTML string retrieved from the Clipboard by passing it to <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) and you're retargeting your app from version 4 to 4.5, that workaround should be removed.If the old behavior is needed for some reason, the app can target the .NET Framework 4.0 to get that behavior.</span></span>

| <span data-ttu-id="7f081-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="7f081-108">Name</span></span>    | <span data-ttu-id="7f081-109">“值”</span><span class="sxs-lookup"><span data-stu-id="7f081-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7f081-110">范围</span><span class="sxs-lookup"><span data-stu-id="7f081-110">Scope</span></span>   | <span data-ttu-id="7f081-111">边缘</span><span class="sxs-lookup"><span data-stu-id="7f081-111">Edge</span></span>        |
| <span data-ttu-id="7f081-112">Version</span><span class="sxs-lookup"><span data-stu-id="7f081-112">Version</span></span> | <span data-ttu-id="7f081-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="7f081-113">4.5.2</span></span>       |
| <span data-ttu-id="7f081-114">类型</span><span class="sxs-lookup"><span data-stu-id="7f081-114">Type</span></span>    | <span data-ttu-id="7f081-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="7f081-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7f081-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="7f081-116">Affected APIs</span></span>

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
