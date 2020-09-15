---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614351"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="b54d4-101">DeflateStream 使用本机 API 进行解压缩</span><span class="sxs-lookup"><span data-stu-id="b54d4-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="b54d4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b54d4-102">Details</span></span>

<span data-ttu-id="b54d4-103">从 .NET Framework 4.7.2 开始，`T:System.IO.Compression.DeflateStream` 类中解压缩的实现已更改为默认使用本机 Windows API。</span><span class="sxs-lookup"><span data-stu-id="b54d4-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="b54d4-104">通常情况下，这能大大地提高性能。</span><span class="sxs-lookup"><span data-stu-id="b54d4-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="b54d4-105">所有面向 .NET Framework 4.7.2 或更高版本的 .NET 应用程序均使用本机实现。此更改可能会导致某些行为差异，其中包括：</span><span class="sxs-lookup"><span data-stu-id="b54d4-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="b54d4-106">异常消息可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="b54d4-106">Exception messages may be different.</span></span> <span data-ttu-id="b54d4-107">但是，引发的异常类型保持不变。</span><span class="sxs-lookup"><span data-stu-id="b54d4-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="b54d4-108">可能以不同的方式处理某些特殊情况（例如没有足够的内存完成操作）。</span><span class="sxs-lookup"><span data-stu-id="b54d4-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="b54d4-109">分析 gzip 标头存在一些已知差异（注意：仅影响用于解压缩的 `GZipStream` 集）：</span><span class="sxs-lookup"><span data-stu-id="b54d4-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="b54d4-110">分析无效标头时出现异常可能在不同的时间引发。</span><span class="sxs-lookup"><span data-stu-id="b54d4-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="b54d4-111">本机实现强制根据规范设置 gzip 标头（即 [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)）内的一些保留标记值，这可能导致其在忽略先前无效值的情况下引发异常。</span><span class="sxs-lookup"><span data-stu-id="b54d4-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b54d4-112">建议</span><span class="sxs-lookup"><span data-stu-id="b54d4-112">Suggestion</span></span>

<span data-ttu-id="b54d4-113">如果借助本机 API 解压缩对应用行为产生负面影响，则可通过将 `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` 开关添加到 app.config 文件的 `runtime` 部分并将其设置为 `true`，选择弃用此功能：</span><span class="sxs-lookup"><span data-stu-id="b54d4-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="b54d4-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="b54d4-114">Name</span></span>    | <span data-ttu-id="b54d4-115">“值”</span><span class="sxs-lookup"><span data-stu-id="b54d4-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b54d4-116">范围</span><span class="sxs-lookup"><span data-stu-id="b54d4-116">Scope</span></span>   | <span data-ttu-id="b54d4-117">次要</span><span class="sxs-lookup"><span data-stu-id="b54d4-117">Minor</span></span>       |
| <span data-ttu-id="b54d4-118">版本</span><span class="sxs-lookup"><span data-stu-id="b54d4-118">Version</span></span> | <span data-ttu-id="b54d4-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b54d4-119">4.7.2</span></span>       |
| <span data-ttu-id="b54d4-120">类型</span><span class="sxs-lookup"><span data-stu-id="b54d4-120">Type</span></span>    | <span data-ttu-id="b54d4-121">重定目标</span><span class="sxs-lookup"><span data-stu-id="b54d4-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b54d4-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b54d4-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
