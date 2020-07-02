---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619859"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="a16eb-101">写入到 PrintSystemJobInfo.JobStream 的数据必须采用 XPS 格式</span><span class="sxs-lookup"><span data-stu-id="a16eb-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="a16eb-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a16eb-102">Details</span></span>

<span data-ttu-id="a16eb-103"><xref:System.Printing.PrintSystemJobInfo.JobStream> 属性公开打印作业的流。</span><span class="sxs-lookup"><span data-stu-id="a16eb-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="a16eb-104">通过写入到此流，用户可以将原始数据发送到基础操作系统打印组件。从 Windows 操作系统的 Windows 8 和更高版本上的 .NET Framework 4.5 起，写入到此流的数据必须采用作为包流的 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="a16eb-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a16eb-105">建议</span><span class="sxs-lookup"><span data-stu-id="a16eb-105">Suggestion</span></span>

<span data-ttu-id="a16eb-106">若要输出打印内容，可以执行下列任一操作：</span><span class="sxs-lookup"><span data-stu-id="a16eb-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="a16eb-107">使用 <xref:System.Windows.Xps.XpsDocumentWriter> 类输出打印内容。</span><span class="sxs-lookup"><span data-stu-id="a16eb-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="a16eb-108">这是建议的替代项。</span><span class="sxs-lookup"><span data-stu-id="a16eb-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="a16eb-109">确保发送给 <xref:System.Printing.PrintSystemJobInfo.JobStream> 属性返回的流的数据作为包流采用 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="a16eb-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="a16eb-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="a16eb-110">Name</span></span>    | <span data-ttu-id="a16eb-111">“值”</span><span class="sxs-lookup"><span data-stu-id="a16eb-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a16eb-112">范围</span><span class="sxs-lookup"><span data-stu-id="a16eb-112">Scope</span></span>   |<span data-ttu-id="a16eb-113">次要</span><span class="sxs-lookup"><span data-stu-id="a16eb-113">Minor</span></span>|
|<span data-ttu-id="a16eb-114">Version</span><span class="sxs-lookup"><span data-stu-id="a16eb-114">Version</span></span>|<span data-ttu-id="a16eb-115">4.5</span><span class="sxs-lookup"><span data-stu-id="a16eb-115">4.5</span></span>|
|<span data-ttu-id="a16eb-116">类型</span><span class="sxs-lookup"><span data-stu-id="a16eb-116">Type</span></span>|<span data-ttu-id="a16eb-117">运行时</span><span class="sxs-lookup"><span data-stu-id="a16eb-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a16eb-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a16eb-118">Affected APIs</span></span>

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
