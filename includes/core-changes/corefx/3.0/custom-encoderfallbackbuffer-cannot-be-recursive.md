---
ms.openlocfilehash: 54ef49755dc0b9d1b821ae7999ab218626d455e1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556317"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="56a50-101">自定义 EncoderFallbackBuffer 实例无法递归回退</span><span class="sxs-lookup"><span data-stu-id="56a50-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="56a50-102">自定义 <xref:System.Text.EncoderFallbackBuffer> 实例无法以递归方式回退。</span><span class="sxs-lookup"><span data-stu-id="56a50-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="56a50-103"><xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的实现必须生成一个可转换为目标编码的字符序列。</span><span class="sxs-lookup"><span data-stu-id="56a50-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="56a50-104">否则会发生异常。</span><span class="sxs-lookup"><span data-stu-id="56a50-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="56a50-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="56a50-105">Change description</span></span>

<span data-ttu-id="56a50-106">在字符到字节的转码操作期间，运行时将检测格式不正确或不可转换的 UTF-16 序列，并将这些字符提供给 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="56a50-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="56a50-107">`Fallback` 方法确定应将哪些字符替换为原始不可转换数据，并通过在循环中调用 <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 来释放这些字符。</span><span class="sxs-lookup"><span data-stu-id="56a50-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="56a50-108">然后，运行时尝试将这些替换字符转码为目标编码。</span><span class="sxs-lookup"><span data-stu-id="56a50-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="56a50-109">如果此操作成功，则运行时继续从原始输入字符串中的中断位置进行转码。</span><span class="sxs-lookup"><span data-stu-id="56a50-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="56a50-110">之前，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的自定义实现可以返回无法转换为目标编码的字符序列。</span><span class="sxs-lookup"><span data-stu-id="56a50-110">Previously, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="56a50-111">如果替换字符无法转码为目标编码，则运行时将使用替换字符再调用一次 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法，并要求 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 方法返回新的替换序列。</span><span class="sxs-lookup"><span data-stu-id="56a50-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="56a50-112">此过程将一直继续，直到运行时最终看到格式正确的、可转换的替换，或直到达到最大递归计数。</span><span class="sxs-lookup"><span data-stu-id="56a50-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="56a50-113">从 .NET Core 3.0 开始，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的自定义实现必须返回可转换为目标编码的字符序列。</span><span class="sxs-lookup"><span data-stu-id="56a50-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="56a50-114">如果替换字符无法转码为目标编码，则引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="56a50-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="56a50-115">运行时将不再对 <xref:System.Text.EncoderFallbackBuffer> 实例进行递归调用。</span><span class="sxs-lookup"><span data-stu-id="56a50-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="56a50-116">仅当满足以下所有三个条件时，此行为才适用：</span><span class="sxs-lookup"><span data-stu-id="56a50-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="56a50-117">运行时检测格式不正确的 UTF-16 序列或无法转换为目标编码的 UTF-16 序列。</span><span class="sxs-lookup"><span data-stu-id="56a50-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="56a50-118">已指定自定义 <xref:System.Text.EncoderFallback>。</span><span class="sxs-lookup"><span data-stu-id="56a50-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="56a50-119">自定义 <xref:System.Text.EncoderFallback> 尝试替换新的格式不正确的或无法转换的 UTF-16 序列。</span><span class="sxs-lookup"><span data-stu-id="56a50-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56a50-120">引入的版本</span><span class="sxs-lookup"><span data-stu-id="56a50-120">Version introduced</span></span>

<span data-ttu-id="56a50-121">3.0</span><span class="sxs-lookup"><span data-stu-id="56a50-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56a50-122">建议操作</span><span class="sxs-lookup"><span data-stu-id="56a50-122">Recommended action</span></span>

<span data-ttu-id="56a50-123">大多数开发人员都不需要执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="56a50-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="56a50-124">如果应用程序使用自定义 <xref:System.Text.EncoderFallback> 和 <xref:System.Text.EncoderFallbackBuffer> 类，请确保 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 的实现使用格式正确的 UTF-16 数据（该数据在运行时第一次调用 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> 方法时可直接转换为目标编码）填充回退缓冲区。</span><span class="sxs-lookup"><span data-stu-id="56a50-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="56a50-125">类别</span><span class="sxs-lookup"><span data-stu-id="56a50-125">Category</span></span>

<span data-ttu-id="56a50-126">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="56a50-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56a50-127">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="56a50-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
