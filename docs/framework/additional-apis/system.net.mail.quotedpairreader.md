---
title: QuotedPairReader 类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990437"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="dbd20-102">QuotedPairReader 类</span><span class="sxs-lookup"><span data-stu-id="dbd20-102">QuotedPairReader class</span></span>

<span data-ttu-id="dbd20-103">确定在带引号的字符串中用引号（转义）括起来的字符。</span><span class="sxs-lookup"><span data-stu-id="dbd20-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="dbd20-104">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="dbd20-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="dbd20-105">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="dbd20-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dbd20-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="dbd20-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="dbd20-107">CountQuotedChars 方法</span><span class="sxs-lookup"><span data-stu-id="dbd20-107">CountQuotedChars method</span></span>

<span data-ttu-id="dbd20-108">计算指定字符串中连续带引号的字符数（包括多个前面带引号的反斜杠）。</span><span class="sxs-lookup"><span data-stu-id="dbd20-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="dbd20-109">例如，给定的字符串 `a\\\b` 和索引 `4` ，该方法返回 `4` ，因为带有引号， `b` 因此是前面三个反斜杠。</span><span class="sxs-lookup"><span data-stu-id="dbd20-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="dbd20-110">参数</span><span class="sxs-lookup"><span data-stu-id="dbd20-110">Parameters</span></span>

- <span data-ttu-id="dbd20-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="dbd20-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="dbd20-112">用于对连续带引号字符进行计数的数据字符串。</span><span class="sxs-lookup"><span data-stu-id="dbd20-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="dbd20-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="dbd20-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="dbd20-114">指定字符串中的位置，最多包含和包括应对哪些连续的带引号字符进行计数。</span><span class="sxs-lookup"><span data-stu-id="dbd20-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="dbd20-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="dbd20-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="dbd20-116">`true`允许转义 Unicode 字符;否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="dbd20-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="dbd20-117">返回值</span><span class="sxs-lookup"><span data-stu-id="dbd20-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="dbd20-118">`0`如果指定索引处的字符未转义，则为; 否则为。否则，则为，最多包含中的字符（包括字符） `index` 。</span><span class="sxs-lookup"><span data-stu-id="dbd20-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="dbd20-119">例外</span><span class="sxs-lookup"><span data-stu-id="dbd20-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="dbd20-120">找到了一个转义的 Unicode 字符，但不允许这样做。</span><span class="sxs-lookup"><span data-stu-id="dbd20-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbd20-121">要求</span><span class="sxs-lookup"><span data-stu-id="dbd20-121">Requirements</span></span>

<span data-ttu-id="dbd20-122">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dbd20-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dbd20-123">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="dbd20-123">**Assembly:** System (in System.dll)</span></span>
