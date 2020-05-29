---
title: ''
description: 本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。 文中包含示例代码。
ms.date: ''
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords: []
ms.openlocfilehash: f1a5da448b08f9b4f1cf3fa6cba67fb376b00a6f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702276"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="0af11-103">如何在 .NET 中对 JSON 进行序列化和反序列化（封送和拆收）</span><span class="sxs-lookup"><span data-stu-id="0af11-103">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="0af11-104">本文演示如何使用 <xref:System.Text.Json> 命名空间对 JavaScript 对象表示法 (JSON) 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-104">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="0af11-105">如果要从 `Newtonsoft.Json` 移植现有代码，请参阅[如何迁移到 `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="0af11-105">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="0af11-106">方向和示例代码直接使用库，而不是通过框架（如 [ASP.NET Core](/aspnet/core/)）。</span><span class="sxs-lookup"><span data-stu-id="0af11-106">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="0af11-107">大多数序列化示例代码将 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 设置为 `true`，以 JSON 进行优质打印（包含缩进和空格，以提高可读性）。</span><span class="sxs-lookup"><span data-stu-id="0af11-107">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="0af11-108">对于生产用途，通常对于此设置会接受默认值 `false`。</span><span class="sxs-lookup"><span data-stu-id="0af11-108">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="0af11-109">代码示例引用下面的类及其变体：</span><span class="sxs-lookup"><span data-stu-id="0af11-109">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="0af11-110">命名空间</span><span class="sxs-lookup"><span data-stu-id="0af11-110">Namespaces</span></span>

<span data-ttu-id="0af11-111"><xref:System.Text.Json> 命名空间包含所有入口点和主要类型。</span><span class="sxs-lookup"><span data-stu-id="0af11-111">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="0af11-112"><xref:System.Text.Json.Serialization> 命名空间包含用于高级方案的特性和 API，以及特定于序列化和反序列化的自定义。</span><span class="sxs-lookup"><span data-stu-id="0af11-112">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="0af11-113">本文中演示的代码示例要求将 `using` 指令用于其中一个或两个命名空间：</span><span class="sxs-lookup"><span data-stu-id="0af11-113">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="0af11-114">`System.Text.Json`中当前不支持 <xref:System.Runtime.Serialization> 命名空间中的特性。</span><span class="sxs-lookup"><span data-stu-id="0af11-114">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="0af11-115">如何将 .NET 对象编写为 JSON（序列化）</span><span class="sxs-lookup"><span data-stu-id="0af11-115">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="0af11-116">若要将 JSON 编写为字符串或文件，请调用 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0af11-116">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0af11-117">下面的示例将 JSON 创建为字符串：</span><span class="sxs-lookup"><span data-stu-id="0af11-117">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-118">下面的示例使用同步代码创建 JSON 文件：</span><span class="sxs-lookup"><span data-stu-id="0af11-118">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-119">下面的示例使用异步代码创建 JSON 文件：</span><span class="sxs-lookup"><span data-stu-id="0af11-119">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-120">前面的示例对要序列化的类型使用类型推理。</span><span class="sxs-lookup"><span data-stu-id="0af11-120">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="0af11-121">`Serialize()` 的重载采用泛型类型参数：</span><span class="sxs-lookup"><span data-stu-id="0af11-121">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="0af11-122">序列化示例</span><span class="sxs-lookup"><span data-stu-id="0af11-122">Serialization example</span></span>

<span data-ttu-id="0af11-123">下面是包含集合和嵌套类的示例类：</span><span class="sxs-lookup"><span data-stu-id="0af11-123">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="0af11-124">序列化以上类型的实例的 JSON 输出类似于下面的示例。</span><span class="sxs-lookup"><span data-stu-id="0af11-124">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="0af11-125">默认情况下，JSON 输出会缩小：</span><span class="sxs-lookup"><span data-stu-id="0af11-125">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="0af11-126">下面的示例演示进行了格式设置的相同 JSON（即，使用空格和缩进进行优质打印）：</span><span class="sxs-lookup"><span data-stu-id="0af11-126">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a><span data-ttu-id="0af11-127">序列化为 UTF-8</span><span class="sxs-lookup"><span data-stu-id="0af11-127">Serialize to UTF-8</span></span>

<span data-ttu-id="0af11-128">若要序列化为 UTF-8，请调用 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="0af11-128">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-129">还有一个采用 <xref:System.Text.Json.Utf8JsonWriter> 的 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 重载可用。</span><span class="sxs-lookup"><span data-stu-id="0af11-129">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="0af11-130">序列化为 UTF-8 比使用基于字符串的方法大约快 5-10%。</span><span class="sxs-lookup"><span data-stu-id="0af11-130">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="0af11-131">出现这种差别的原因是字节（作为 UTF-8）不需要转换为字符串 (UTF-16)。</span><span class="sxs-lookup"><span data-stu-id="0af11-131">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="0af11-132">序列化行为</span><span class="sxs-lookup"><span data-stu-id="0af11-132">Serialization behavior</span></span>

* <span data-ttu-id="0af11-133">默认情况下，所有公共属性都会序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-133">By default, all public properties are serialized.</span></span> <span data-ttu-id="0af11-134">可以[指定要排除的属性](#exclude-properties-from-serialization)。</span><span class="sxs-lookup"><span data-stu-id="0af11-134">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="0af11-135">[默认编码器](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)会转义非 ASCII 字符、ASCII 范围内的 HTML 敏感字符以及根据 [RFC 8259 JSON 规范](https://tools.ietf.org/html/rfc8259#section-7)必须进行转义的字符。</span><span class="sxs-lookup"><span data-stu-id="0af11-135">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="0af11-136">默认情况下，JSON 会缩小。</span><span class="sxs-lookup"><span data-stu-id="0af11-136">By default, JSON is minified.</span></span> <span data-ttu-id="0af11-137">可以[对 JSON 进行优质打印](#serialize-to-formatted-json)。</span><span class="sxs-lookup"><span data-stu-id="0af11-137">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="0af11-138">默认情况下，JSON 名称的大小写与 .NET 名称匹配。</span><span class="sxs-lookup"><span data-stu-id="0af11-138">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="0af11-139">可以[自定义 JSON 名称大小写](#customize-json-names-and-values)。</span><span class="sxs-lookup"><span data-stu-id="0af11-139">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="0af11-140">检测到循环引用并引发异常。</span><span class="sxs-lookup"><span data-stu-id="0af11-140">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="0af11-141">当前不包括字段。</span><span class="sxs-lookup"><span data-stu-id="0af11-141">Currently, fields are excluded.</span></span>

<span data-ttu-id="0af11-142">支持的类型包括：</span><span class="sxs-lookup"><span data-stu-id="0af11-142">Supported types include:</span></span>

* <span data-ttu-id="0af11-143">映射到 JavaScript 基元的 .NET 基元，如数值类型、字符串和布尔。</span><span class="sxs-lookup"><span data-stu-id="0af11-143">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="0af11-144">用户定义的 [普通旧 CLR 对象 (POCO)](https://stackoverflow.com/questions/250001/poco-definition)。</span><span class="sxs-lookup"><span data-stu-id="0af11-144">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="0af11-145">一维和交错数组 (`ArrayName[][]`)。</span><span class="sxs-lookup"><span data-stu-id="0af11-145">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="0af11-146">`Dictionary<string,TValue>`其中 `TValue` 是 `object`、`JsonElement` 或 POCO。</span><span class="sxs-lookup"><span data-stu-id="0af11-146">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="0af11-147">以下命名空间中的集合。</span><span class="sxs-lookup"><span data-stu-id="0af11-147">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="0af11-148">可以[实现自定义转换器](system-text-json-converters-how-to.md)以处理其他类型或提供内置转换器不支持的功能。</span><span class="sxs-lookup"><span data-stu-id="0af11-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="0af11-149">如何将 JSON 读入 .NET 对象（反序列化）</span><span class="sxs-lookup"><span data-stu-id="0af11-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="0af11-150">若要从字符串或文件进行反序列化，请调用 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0af11-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0af11-151">下面的示例从字符串读取 JSON，并创建前面为[序列化示例](#serialization-example)显示的 `WeatherForecast` 类的实例：</span><span class="sxs-lookup"><span data-stu-id="0af11-151">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="0af11-152">若要使用同步代码从文件进行反序列化，请将文件读入字符串中，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="0af11-153">若要使用异步代码从文件进行反序列化，请调用 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="0af11-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="0af11-154">从 UTF-8 进行反序列化</span><span class="sxs-lookup"><span data-stu-id="0af11-154">Deserialize from UTF-8</span></span>

<span data-ttu-id="0af11-155">若要从 UTF-8 进行反序列化，请调用采用 `Utf8JsonReader` 或 `ReadOnlySpan<byte>` 的 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 重载，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="0af11-155">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="0af11-156">这些示例假设 JSON 处于名为 jsonUtf8Bytes 的字节数组中。</span><span class="sxs-lookup"><span data-stu-id="0af11-156">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="0af11-157">反序列化行为</span><span class="sxs-lookup"><span data-stu-id="0af11-157">Deserialization behavior</span></span>

* <span data-ttu-id="0af11-158">默认情况下，属性名称匹配区分大小写。</span><span class="sxs-lookup"><span data-stu-id="0af11-158">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="0af11-159">可以[指定不区分大小写](#case-insensitive-property-matching)。</span><span class="sxs-lookup"><span data-stu-id="0af11-159">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="0af11-160">如果 JSON 包含只读属性的值，则会忽略该值，并且不引发异常。</span><span class="sxs-lookup"><span data-stu-id="0af11-160">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="0af11-161">不支持在不使用无参数构造函数的情况下反序列化为引用类型。</span><span class="sxs-lookup"><span data-stu-id="0af11-161">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="0af11-162">不支持反序列化为不可变对象或只读属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-162">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="0af11-163">默认情况下，支持将枚举作为数字。</span><span class="sxs-lookup"><span data-stu-id="0af11-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="0af11-164">可以[将枚举名称序列化为字符串](#enums-as-strings)。</span><span class="sxs-lookup"><span data-stu-id="0af11-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="0af11-165">不支持字段。</span><span class="sxs-lookup"><span data-stu-id="0af11-165">Fields aren't supported.</span></span>
* <span data-ttu-id="0af11-166">默认情况下，JSON 中的注释或尾随逗号会引发异常。</span><span class="sxs-lookup"><span data-stu-id="0af11-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="0af11-167">可以[允许注释和尾随逗号](#allow-comments-and-trailing-commas)。</span><span class="sxs-lookup"><span data-stu-id="0af11-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="0af11-168">[默认最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)为 64。</span><span class="sxs-lookup"><span data-stu-id="0af11-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="0af11-169">可以[实现自定义转换器](system-text-json-converters-how-to.md)以提供内置转换器不支持的功能。</span><span class="sxs-lookup"><span data-stu-id="0af11-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="0af11-170">序列化为格式化 JSON</span><span class="sxs-lookup"><span data-stu-id="0af11-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="0af11-171">若要对 JSON 输出进行优质打印，请将 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> 设置为 `true`：</span><span class="sxs-lookup"><span data-stu-id="0af11-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="0af11-172">下面是一个要进行序列化的示例类型，以及进行了优质打印的 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="0af11-173">自定义 JSON 名称和值</span><span class="sxs-lookup"><span data-stu-id="0af11-173">Customize JSON names and values</span></span>

<span data-ttu-id="0af11-174">默认情况下，属性名称和字典键在 JSON 输出中保持不变，包括大小写。</span><span class="sxs-lookup"><span data-stu-id="0af11-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="0af11-175">枚举值表示为数字。</span><span class="sxs-lookup"><span data-stu-id="0af11-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="0af11-176">本部分介绍如何：</span><span class="sxs-lookup"><span data-stu-id="0af11-176">This section explains how to:</span></span>

* [<span data-ttu-id="0af11-177">自定义单个属性名称</span><span class="sxs-lookup"><span data-stu-id="0af11-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="0af11-178">将所有属性名称转换为 camel 大小写</span><span class="sxs-lookup"><span data-stu-id="0af11-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="0af11-179">实现自定义属性命名策略</span><span class="sxs-lookup"><span data-stu-id="0af11-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="0af11-180">将字典键转换为 camel 大小写</span><span class="sxs-lookup"><span data-stu-id="0af11-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="0af11-181">将枚举转换为字符串和 camel 大小写</span><span class="sxs-lookup"><span data-stu-id="0af11-181">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="0af11-182">对于需要对 JSON 属性名称和值进行特殊处理的其他方案，可以[实现自定义转换器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="0af11-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="0af11-183">自定义单个属性名称</span><span class="sxs-lookup"><span data-stu-id="0af11-183">Customize individual property names</span></span>

<span data-ttu-id="0af11-184">若要设置单个属性的名称，请使用 [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 特性。</span><span class="sxs-lookup"><span data-stu-id="0af11-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="0af11-185">下面是要进行序列化的示例类型和生成的 JSON：</span><span class="sxs-lookup"><span data-stu-id="0af11-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0af11-186">此特性设置的属性名称：</span><span class="sxs-lookup"><span data-stu-id="0af11-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="0af11-187">同时适用于两个方向（序列化和反序列化）。</span><span class="sxs-lookup"><span data-stu-id="0af11-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="0af11-188">优先于属性命名策略。</span><span class="sxs-lookup"><span data-stu-id="0af11-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="0af11-189">对所有 JSON 属性名称使用 camel 大小写</span><span class="sxs-lookup"><span data-stu-id="0af11-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="0af11-190">若要对所有 JSON 属性名称使用 camel 大小写，请将 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 设置为 `JsonNamingPolicy.CamelCase`，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="0af11-191">下面是要进行序列化的示例类和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0af11-192">camel 大小写属性命名策略：</span><span class="sxs-lookup"><span data-stu-id="0af11-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="0af11-193">适用于序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="0af11-194">由 `[JsonPropertyName]` 特性替代。</span><span class="sxs-lookup"><span data-stu-id="0af11-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="0af11-195">这便是示例中的 JSON 属性名称 `Wind` 不是 camel 大小写的原因。</span><span class="sxs-lookup"><span data-stu-id="0af11-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="0af11-196">使用自定义 JSON 属性命名策略</span><span class="sxs-lookup"><span data-stu-id="0af11-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="0af11-197">若要使用自定义 JSON 属性命名策略，请创建派生自 <xref:System.Text.Json.JsonNamingPolicy> 的类，并替代 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="0af11-198">然后，将 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 属性设置为命名策略类的实例：</span><span class="sxs-lookup"><span data-stu-id="0af11-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-199">下面是要进行序列化的示例类和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0af11-200">JSON 属性命名策略：</span><span class="sxs-lookup"><span data-stu-id="0af11-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="0af11-201">适用于序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="0af11-202">由 `[JsonPropertyName]` 特性替代。</span><span class="sxs-lookup"><span data-stu-id="0af11-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="0af11-203">这便是示例中的 JSON 属性名称 `Wind` 不是大写的原因。</span><span class="sxs-lookup"><span data-stu-id="0af11-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="0af11-204">Camel 大小写字典键</span><span class="sxs-lookup"><span data-stu-id="0af11-204">Camel case dictionary keys</span></span>

<span data-ttu-id="0af11-205">如果要序列化的对象的属性为 `Dictionary<string,TValue>` 类型，则 `string` 键可转换为 camel 大小写。</span><span class="sxs-lookup"><span data-stu-id="0af11-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="0af11-206">为此，请将 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 设置为 `JsonNamingPolicy.CamelCase`，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-207">使用名为 `TemperatureRanges` 且具有键值对 `"ColdMinTemp", 20` 和 `"HotMinTemp", 40` 的字典序列化对象会产生类似于以下示例的 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="0af11-208">字典键的 camel 大小写命名策略仅适用于序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="0af11-209">如果对字典进行反序列化，即使为 `DictionaryKeyPolicy`指定 `JsonNamingPolicy.CamelCase`，键也会与 JSON 文件匹配。</span><span class="sxs-lookup"><span data-stu-id="0af11-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="0af11-210">作为字符串的枚举</span><span class="sxs-lookup"><span data-stu-id="0af11-210">Enums as strings</span></span>

<span data-ttu-id="0af11-211">默认情况下，枚举会序列化为数字。</span><span class="sxs-lookup"><span data-stu-id="0af11-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="0af11-212">若要将枚举名称序列化为字符串，请使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter>。</span><span class="sxs-lookup"><span data-stu-id="0af11-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="0af11-213">例如，假设需要序列化以下具有枚举的类：</span><span class="sxs-lookup"><span data-stu-id="0af11-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="0af11-214">如果 Summary 为 `Hot`，则默认情况下序列化的 JSON 具有数值 3：</span><span class="sxs-lookup"><span data-stu-id="0af11-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="0af11-215">下面的示例代码序列化枚举名称(而不是数值)，并将名称转换为 camel 大小写：</span><span class="sxs-lookup"><span data-stu-id="0af11-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-216">生成的 JSON 类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="0af11-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="0af11-217">还可以反序列化枚举字符串名称，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="0af11-218">从序列化中排除属性</span><span class="sxs-lookup"><span data-stu-id="0af11-218">Exclude properties from serialization</span></span>

<span data-ttu-id="0af11-219">默认情况下，所有公共属性都会序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="0af11-220">如果不想让某些属性出现在 JSON 输出中，则有几个选项可用。</span><span class="sxs-lookup"><span data-stu-id="0af11-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="0af11-221">本部分介绍如何排除：</span><span class="sxs-lookup"><span data-stu-id="0af11-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="0af11-222">单个属性</span><span class="sxs-lookup"><span data-stu-id="0af11-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="0af11-223">所有只读属性</span><span class="sxs-lookup"><span data-stu-id="0af11-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="0af11-224">所有 null 值属性</span><span class="sxs-lookup"><span data-stu-id="0af11-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="0af11-225">排除单个属性</span><span class="sxs-lookup"><span data-stu-id="0af11-225">Exclude individual properties</span></span>

<span data-ttu-id="0af11-226">若要忽略单个属性，请使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 特性。</span><span class="sxs-lookup"><span data-stu-id="0af11-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="0af11-227">下面是要进行序列化的示例类型和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="0af11-228">排除所有只读属性</span><span class="sxs-lookup"><span data-stu-id="0af11-228">Exclude all read-only properties</span></span>

<span data-ttu-id="0af11-229">如果属性包含公共 getter 而不是公共 setter，则属性为只读。</span><span class="sxs-lookup"><span data-stu-id="0af11-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="0af11-230">若要排除所有只读属性，请将 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 设置为 `true`，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-231">下面是要进行序列化的示例类型和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="0af11-232">此选项仅适用于序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-232">This option applies only to serialization.</span></span> <span data-ttu-id="0af11-233">在反序列化过程中，默认情况下会忽略只读属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="0af11-234">排除所有 null 值属性</span><span class="sxs-lookup"><span data-stu-id="0af11-234">Exclude all null value properties</span></span>

<span data-ttu-id="0af11-235">若要排除所有 null 值属性，请将 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 属性设置为 `true`，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-236">下面是要进行序列化的示例对象和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="0af11-237">Property</span><span class="sxs-lookup"><span data-stu-id="0af11-237">Property</span></span> |<span data-ttu-id="0af11-238">“值”</span><span class="sxs-lookup"><span data-stu-id="0af11-238">Value</span></span>  |
|---
<span data-ttu-id="0af11-239">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-239">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-240">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-240">It includes sample code.'</span></span>
<span data-ttu-id="0af11-241">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-241">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-242">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-242">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-243">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-243">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="0af11-244">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-244">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-245">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-245">It includes sample code.'</span></span>
<span data-ttu-id="0af11-246">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-246">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-247">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-247">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-248">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-248">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="0af11-249">-----|--- title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-249">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-250">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-250">It includes sample code.'</span></span>
<span data-ttu-id="0af11-251">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-251">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-252">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-252">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-253">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-253">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="0af11-254">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-254">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-255">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-255">It includes sample code.'</span></span>
<span data-ttu-id="0af11-256">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-256">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-257">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-257">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-258">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-258">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="0af11-259">-----| | 日期    | 2019/8/1 午夜 12:00:00 -07:00| | TemperatureCelsius| 25 | | 摘要| null|</span><span class="sxs-lookup"><span data-stu-id="0af11-259">-----| | Date    | 8/1/2019 12:00:00 AM -07:00| | TemperatureCelsius| 25 | | Summary| null|</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="0af11-260">此设置适用于序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-260">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="0af11-261">有关对反序列化的影响的信息，请参阅[在反序列化时忽略 null](#ignore-null-when-deserializing)。</span><span class="sxs-lookup"><span data-stu-id="0af11-261">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="0af11-262">自定义字符编码</span><span class="sxs-lookup"><span data-stu-id="0af11-262">Customize character encoding</span></span>

<span data-ttu-id="0af11-263">默认情况下，序列化程序会转义所有非 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="0af11-263">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="0af11-264">即，会将它们替换为 `\uxxxx`，其中 `xxxx` 为字符的 Unicode 代码。</span><span class="sxs-lookup"><span data-stu-id="0af11-264">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="0af11-265">例如，如果 `Summary` 属性设置为西里尔文 жарко，则 `WeatherForecast` 对象会进行序列化，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-265">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="0af11-266">序列化语言字符集</span><span class="sxs-lookup"><span data-stu-id="0af11-266">Serialize language character sets</span></span>

<span data-ttu-id="0af11-267">若要序列化一种或多种语言的字符集而不进行转义，请在创建 <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> 的实例时指定 [Unicode 范围](xref:System.Text.Unicode.UnicodeRanges)，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-267">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="0af11-268">此代码不转义西里尔文或希腊语字符。</span><span class="sxs-lookup"><span data-stu-id="0af11-268">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="0af11-269">如果 `Summary` 属性设置为西里尔文 жарко，则 `WeatherForecast` 对象会进行序列化，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-269">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="0af11-270">若要序列化所有语言集而不进行转义，请使用 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0af11-270">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="0af11-271">序列化特定字符</span><span class="sxs-lookup"><span data-stu-id="0af11-271">Serialize specific characters</span></span>

<span data-ttu-id="0af11-272">一种替代方法是指定要允许的单个字符，而不进行转义。</span><span class="sxs-lookup"><span data-stu-id="0af11-272">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="0af11-273">下面的示例仅序列化 жарко 的前两个字符：</span><span class="sxs-lookup"><span data-stu-id="0af11-273">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="0af11-274">下面是前面代码生成的 JSON 的示例：</span><span class="sxs-lookup"><span data-stu-id="0af11-274">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="0af11-275">序列化所有字符</span><span class="sxs-lookup"><span data-stu-id="0af11-275">Serialize all characters</span></span>

<span data-ttu-id="0af11-276">若要最大程度地减少转义，可以使用 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-276">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="0af11-277">与默认编码器相比，`UnsafeRelaxedJsonEscaping` 编码器在允许字符通过而不进行转义方面更加宽松：</span><span class="sxs-lookup"><span data-stu-id="0af11-277">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="0af11-278">它不转义 HTML 敏感字符，如 `<`、`>`、`&` 和 `'`。</span><span class="sxs-lookup"><span data-stu-id="0af11-278">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="0af11-279">它不提供任何针对 XSS 或信息泄露攻击（如客户端和服务器在字符集方面不一致所可能导致的攻击）的额外深度防御保护。</span><span class="sxs-lookup"><span data-stu-id="0af11-279">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="0af11-280">仅当知道客户端将生成的有效负载解释为 UTF-8 编码的 JSON 时，才使用不安全编码器。</span><span class="sxs-lookup"><span data-stu-id="0af11-280">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="0af11-281">例如，如果服务器在发送响应标头 `Content-Type: application/json; charset=utf-8`，则可以使用它。</span><span class="sxs-lookup"><span data-stu-id="0af11-281">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="0af11-282">永远不允许将原始 `UnsafeRelaxedJsonEscaping` 输出发出到 HTML 页面或 `<script>` 元素。</span><span class="sxs-lookup"><span data-stu-id="0af11-282">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="0af11-283">序列化派生类的属性</span><span class="sxs-lookup"><span data-stu-id="0af11-283">Serialize properties of derived classes</span></span>

<span data-ttu-id="0af11-284">不支持多态类型层次结构的序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-284">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="0af11-285">例如，如果属性定义为接口或抽象类，则即使运行时类型具有其他属性，也只会序列化对接口或抽象类定义的属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-285">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="0af11-286">此部分中介绍了此行为的例外情况。</span><span class="sxs-lookup"><span data-stu-id="0af11-286">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="0af11-287">例如，假设有一个 `WeatherForecast` 类和一个派生类 `WeatherForecastDerived`：</span><span class="sxs-lookup"><span data-stu-id="0af11-287">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="0af11-288">并且假设 `Serialize` 方法的类型参数在编译时为 `WeatherForecast`：</span><span class="sxs-lookup"><span data-stu-id="0af11-288">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="0af11-289">在这种情况下，即使 `weatherForecast` 对象实际上是 `WeatherForecastDerived` 对象，也不会序列化 `WindSpeed` 属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-289">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="0af11-290">仅序列化基类属性：</span><span class="sxs-lookup"><span data-stu-id="0af11-290">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="0af11-291">此行为旨在帮助防止在运行时创建的派生类型中发生意外数据泄露。</span><span class="sxs-lookup"><span data-stu-id="0af11-291">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="0af11-292">若要序列化前面示例中派生类型的属性，请使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="0af11-292">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="0af11-293">调用 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 的重载，以便在运行时指定类型：</span><span class="sxs-lookup"><span data-stu-id="0af11-293">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="0af11-294">将要序列化的对象声明为 `object`。</span><span class="sxs-lookup"><span data-stu-id="0af11-294">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="0af11-295">在前面的示例方案中，这两种方法都会使 `WindSpeed` 属性包含在 JSON 输出中：</span><span class="sxs-lookup"><span data-stu-id="0af11-295">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="0af11-296">这些方法只为要序列化的根对象提供多态序列化，而不为该根对象的属性提供。</span><span class="sxs-lookup"><span data-stu-id="0af11-296">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="0af11-297">如果将较低级别的对象定义为类型 `object`，则可以对它们进行多态序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-297">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="0af11-298">例如，假设 `WeatherForecast` 类具有一个名为 `PreviousForecast` 的属性，该属性可以定义为类型 `WeatherForecast` 或 `object`：</span><span class="sxs-lookup"><span data-stu-id="0af11-298">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="0af11-299">如果 `PreviousForecast` 属性包含 `WeatherForecastDerived` 的实例：</span><span class="sxs-lookup"><span data-stu-id="0af11-299">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="0af11-300">序列化 `WeatherForecastWithPrevious` 的 JSON 输出不包含 `WindSpeed`。</span><span class="sxs-lookup"><span data-stu-id="0af11-300">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="0af11-301">序列化 `WeatherForecastWithPreviousAsObject` 的 JSON 输出包含 `WindSpeed`。</span><span class="sxs-lookup"><span data-stu-id="0af11-301">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="0af11-302">若要序列化 `WeatherForecastWithPreviousAsObject`，无需调用 `Serialize<object>` 或 `GetType`，因为根对象不是可能属于派生类型的对象。</span><span class="sxs-lookup"><span data-stu-id="0af11-302">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="0af11-303">下面的代码示例不调用 `Serialize<object>` 或 `GetType`：</span><span class="sxs-lookup"><span data-stu-id="0af11-303">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="0af11-304">前面的代码会正确地序列化 `WeatherForecastWithPreviousAsObject`：</span><span class="sxs-lookup"><span data-stu-id="0af11-304">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="0af11-305">将属性定义为 `object` 的相同方法适用于接口。</span><span class="sxs-lookup"><span data-stu-id="0af11-305">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="0af11-306">假设具有以下接口和实现，并且要使用包含实现实例的属性序列化类：</span><span class="sxs-lookup"><span data-stu-id="0af11-306">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="0af11-307">序列化 `Forecasts` 的实例时，只有 `Tuesday` 显示 `WindSpeed` 属性，因为 `Tuesday` 定义为 `object`：</span><span class="sxs-lookup"><span data-stu-id="0af11-307">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="0af11-308">下面的示例显示前面代码生成的 JSON：</span><span class="sxs-lookup"><span data-stu-id="0af11-308">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="0af11-309">有关多态序列化的详细信息，以及有关反序列化的信息，请参阅[如何从 Newtonsoft.Json 迁移到 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。</span><span class="sxs-lookup"><span data-stu-id="0af11-309">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="0af11-310">允许注释和尾随逗号</span><span class="sxs-lookup"><span data-stu-id="0af11-310">Allow comments and trailing commas</span></span>

<span data-ttu-id="0af11-311">默认情况下，JSON 中不允许使用注释和尾随逗号。</span><span class="sxs-lookup"><span data-stu-id="0af11-311">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="0af11-312">若要在 JSON 中允许注释，请将 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 属性设置为 `JsonCommentHandling.Skip`。</span><span class="sxs-lookup"><span data-stu-id="0af11-312">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="0af11-313">若要允许尾随逗号，请将 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="0af11-313">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="0af11-314">下面的示例演示如何允许这两者：</span><span class="sxs-lookup"><span data-stu-id="0af11-314">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="0af11-315">下面是包含注释和尾随逗号的示例 JSON：</span><span class="sxs-lookup"><span data-stu-id="0af11-315">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="0af11-316">不区分大小写的属性匹配</span><span class="sxs-lookup"><span data-stu-id="0af11-316">Case-insensitive property matching</span></span>

<span data-ttu-id="0af11-317">默认情况下，反序列化会查找 JSON 与目标对象属性之间区分大小写的属性名称匹配。</span><span class="sxs-lookup"><span data-stu-id="0af11-317">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="0af11-318">若要更改该行为，请将 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 设置为 `true`：</span><span class="sxs-lookup"><span data-stu-id="0af11-318">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="0af11-319">下面是具有 camel 大小写属性名称的示例 JSON。</span><span class="sxs-lookup"><span data-stu-id="0af11-319">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="0af11-320">它可以反序列化为具有帕斯卡拼写法属性名称的以下类型。</span><span class="sxs-lookup"><span data-stu-id="0af11-320">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="0af11-321">处理溢出 JSON</span><span class="sxs-lookup"><span data-stu-id="0af11-321">Handle overflow JSON</span></span>

<span data-ttu-id="0af11-322">反序列化时，可能会在 JSON 中收到不是由目标类型的属性表示的数据。</span><span class="sxs-lookup"><span data-stu-id="0af11-322">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="0af11-323">例如，假设目标类型如下：</span><span class="sxs-lookup"><span data-stu-id="0af11-323">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="0af11-324">要反序列化的 JSON 如下：</span><span class="sxs-lookup"><span data-stu-id="0af11-324">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="0af11-325">如果将显示的 JSON 反序列化为显示的类型，则 `DatesAvailable` 和 `SummaryWords` 属性无处可去，会丢失。</span><span class="sxs-lookup"><span data-stu-id="0af11-325">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="0af11-326">若要捕获额外数据（如这些属性），请将 [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 特性应用于类型 `Dictionary<string,object>` 或 `Dictionary<string,JsonElement>` 的属性：</span><span class="sxs-lookup"><span data-stu-id="0af11-326">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="0af11-327">将前面显示的 JSON 反序列化为此示例类型时，额外数据会成为 `ExtensionData` 属性的键值对：</span><span class="sxs-lookup"><span data-stu-id="0af11-327">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="0af11-328">Property</span><span class="sxs-lookup"><span data-stu-id="0af11-328">Property</span></span> |<span data-ttu-id="0af11-329">“值”</span><span class="sxs-lookup"><span data-stu-id="0af11-329">Value</span></span>  |<span data-ttu-id="0af11-330">说明</span><span class="sxs-lookup"><span data-stu-id="0af11-330">Notes</span></span>  |
|---
<span data-ttu-id="0af11-331">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-331">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-332">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-332">It includes sample code.'</span></span>
<span data-ttu-id="0af11-333">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-333">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-334">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-334">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-335">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-335">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="0af11-336">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-336">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-337">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-337">It includes sample code.'</span></span>
<span data-ttu-id="0af11-338">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-338">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-339">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-339">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-340">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-340">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="0af11-341">-----|--- title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-341">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-342">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-342">It includes sample code.'</span></span>
<span data-ttu-id="0af11-343">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-343">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-344">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-344">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-345">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-345">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="0af11-346">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-346">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-347">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-347">It includes sample code.'</span></span>
<span data-ttu-id="0af11-348">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-348">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-349">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-349">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-350">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-350">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="0af11-351">-----|--- title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-351">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-352">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-352">It includes sample code.'</span></span>
<span data-ttu-id="0af11-353">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-353">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-354">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-354">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-355">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-355">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="0af11-356">title: description:“本文演示如何使用 System.Text.Json 命名空间在 .NET 中对 JSON 进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="0af11-356">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="0af11-357">文中包含示例代码。”</span><span class="sxs-lookup"><span data-stu-id="0af11-357">It includes sample code.'</span></span>
<span data-ttu-id="0af11-358">ms.date: no-loc:</span><span class="sxs-lookup"><span data-stu-id="0af11-358">ms.date: no-loc:</span></span>
- <span data-ttu-id="0af11-359">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="0af11-359">'System.Text.Json'</span></span>
- <span data-ttu-id="0af11-360">'Newtonsoft.Json' helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="0af11-360">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="0af11-361">-----| | 日期    | 2019/8/1 午夜 12:00:00 -07:00|| | TemperatureCelsius| 0 | 大小写不匹配（JSON 中的 `temperatureCelsius`），因此未设置属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-361">-----| | Date    | 8/1/2019 12:00:00 AM -07:00|| | TemperatureCelsius| 0 | Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> <span data-ttu-id="0af11-362">| | 摘要 | 热 || | ExtensionData | temperatureCelsius:25 |因为大小写不匹配，所以此 JSON 属性是额外属性，会成为字典中的键值对。| || DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="0af11-362">| | Summary | Hot || | ExtensionData | temperatureCelsius: 25 |Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.| || DatesAvailable:</span></span><br>  <span data-ttu-id="0af11-363">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="0af11-363">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="0af11-364">2019/8/2 午夜 12:00:00 -07:00 |JSON 中的额外属性会成为键值对，将数组作为值对象。| | |SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="0af11-364">8/2/2019 12:00:00 AM -07:00 |Extra property from the JSON becomes a key-value pair, with an array as the value object.| | |SummaryWords:</span></span><br><span data-ttu-id="0af11-365">酷</span><span class="sxs-lookup"><span data-stu-id="0af11-365">Cool</span></span><br><span data-ttu-id="0af11-366">Windy</span><span class="sxs-lookup"><span data-stu-id="0af11-366">Windy</span></span><br><span data-ttu-id="0af11-367">Humid |JSON 中的额外属性会成为键值对，将数组作为值对象。|</span><span class="sxs-lookup"><span data-stu-id="0af11-367">Humid |Extra property from the JSON becomes a key-value pair, with an array as the value object.|</span></span>

<span data-ttu-id="0af11-368">序列化目标对象时，扩展数据键值对会成为 JSON 属性，就如同它们处于传入 JSON 中一样：</span><span class="sxs-lookup"><span data-stu-id="0af11-368">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="0af11-369">请注意，`ExtensionData` 属性名称不会出现在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="0af11-369">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="0af11-370">此行为使 JSON 可以进行往返，而不会丢失任何不会以其他方式进行反序列化的额外数据。</span><span class="sxs-lookup"><span data-stu-id="0af11-370">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="0af11-371">反序列化时忽略 null</span><span class="sxs-lookup"><span data-stu-id="0af11-371">Ignore null when deserializing</span></span>

<span data-ttu-id="0af11-372">默认情况下，如果 JSON 中的属性为 null，则目标对象中的对应属性会设置为 null。</span><span class="sxs-lookup"><span data-stu-id="0af11-372">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="0af11-373">在某些情况下，目标属性可能具有默认值，并且你不希望 null 值替代默认值。</span><span class="sxs-lookup"><span data-stu-id="0af11-373">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="0af11-374">例如，假设以下代码表示目标对象：</span><span class="sxs-lookup"><span data-stu-id="0af11-374">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="0af11-375">假设反序列化以下 JSON：</span><span class="sxs-lookup"><span data-stu-id="0af11-375">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="0af11-376">反序列化之后，`WeatherForecastWithDefault` 对象的 `Summary` 属性为 null。</span><span class="sxs-lookup"><span data-stu-id="0af11-376">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="0af11-377">若要更改此行为，请将 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> 设置为 `true`，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-377">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="0af11-378">利用此选项时，`WeatherForecastWithDefault` 对象的 `Summary` 属性在反序列化之后是默认值“No summary”。</span><span class="sxs-lookup"><span data-stu-id="0af11-378">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="0af11-379">JSON 中的 Null 值仅在有效时才会被忽略。</span><span class="sxs-lookup"><span data-stu-id="0af11-379">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="0af11-380">不可为 null 的值类型的 Null 值会导致异常。</span><span class="sxs-lookup"><span data-stu-id="0af11-380">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="0af11-381">Utf8JsonReader、Utf8JsonWriter 和 JsonDocument</span><span class="sxs-lookup"><span data-stu-id="0af11-381">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="0af11-382"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是面向 UTF-8 编码 JSON 文本的一个高性能、低分配的只进读取器，从 `ReadOnlySpan<byte>` 或 `ReadOnlySequence<byte>` 读取信息。</span><span class="sxs-lookup"><span data-stu-id="0af11-382"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="0af11-383">`Utf8JsonReader` 是一种低级类型，可用于生成自定义分析器和反序列化程序。</span><span class="sxs-lookup"><span data-stu-id="0af11-383">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="0af11-384"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 方法在后台使用 `Utf8JsonReader`。</span><span class="sxs-lookup"><span data-stu-id="0af11-384">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="0af11-385"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一种高性能方式，从常见 .NET 类型（例如，`String`、`Int32` 和 `DateTime`）编写 UTF-8 编码的 JSON 文本。</span><span class="sxs-lookup"><span data-stu-id="0af11-385"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="0af11-386">该编写器是一种低级类型，可用于生成自定义序列化程序。</span><span class="sxs-lookup"><span data-stu-id="0af11-386">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="0af11-387"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 方法在后台使用 `Utf8JsonWriter`。</span><span class="sxs-lookup"><span data-stu-id="0af11-387">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="0af11-388"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用 `Utf8JsonReader` 生成只读文档对象模型 (DOM) 的功能。</span><span class="sxs-lookup"><span data-stu-id="0af11-388"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="0af11-389">DOM 提供对 JSON 有效负载中的数据的随机访问。</span><span class="sxs-lookup"><span data-stu-id="0af11-389">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="0af11-390">可以通过 <xref:System.Text.Json.JsonElement> 类型访问构成有效负载的 JSON 元素。</span><span class="sxs-lookup"><span data-stu-id="0af11-390">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="0af11-391">`JsonElement` 类型提供数组和对象枚举器，以及用于将 JSON 文本转换为常见 .NET 类型的 API。</span><span class="sxs-lookup"><span data-stu-id="0af11-391">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="0af11-392">`JsonDocument` 公开了 <xref:System.Text.Json.JsonDocument.RootElement> 属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-392">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="0af11-393">以下部分演示如何使用这些工具读取和写入 JSON。</span><span class="sxs-lookup"><span data-stu-id="0af11-393">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="0af11-394">使用 JsonDocument 访问数据</span><span class="sxs-lookup"><span data-stu-id="0af11-394">Use JsonDocument for access to data</span></span>

<span data-ttu-id="0af11-395">下面的示例演示如何使用 <xref:System.Text.Json.JsonDocument> 类来随机访问 JSON 字符串中的数据：</span><span class="sxs-lookup"><span data-stu-id="0af11-395">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="0af11-396">前面的代码：</span><span class="sxs-lookup"><span data-stu-id="0af11-396">The preceding code:</span></span>

* <span data-ttu-id="0af11-397">假设要分析的 JSON 处于名为 `jsonString` 的字符串中。</span><span class="sxs-lookup"><span data-stu-id="0af11-397">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="0af11-398">对 `Students` 数组中具有 `Grade` 属性的对象计算平均成绩。</span><span class="sxs-lookup"><span data-stu-id="0af11-398">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="0af11-399">为没有成绩的学生分配默认成绩 70。</span><span class="sxs-lookup"><span data-stu-id="0af11-399">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="0af11-400">通过在每次迭代时使 `count` 变量递增来对学生进行计数。</span><span class="sxs-lookup"><span data-stu-id="0af11-400">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="0af11-401">一种替代方法是调用 <xref:System.Text.Json.JsonElement.GetArrayLength%2A>，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0af11-401">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="0af11-402">下面是此代码处理的 JSON 示例：</span><span class="sxs-lookup"><span data-stu-id="0af11-402">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="0af11-403">使用 JsonDocument 写入 JSON</span><span class="sxs-lookup"><span data-stu-id="0af11-403">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="0af11-404">下面的示例演示如何通过 <xref:System.Text.Json.JsonDocument> 写入 JSON：</span><span class="sxs-lookup"><span data-stu-id="0af11-404">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="0af11-405">前面的代码：</span><span class="sxs-lookup"><span data-stu-id="0af11-405">The preceding code:</span></span>

* <span data-ttu-id="0af11-406">读取 JSON 文件，将数据加载到 `JsonDocument` 中，并将格式化（进行了优质打印的）JSON 写入文件。</span><span class="sxs-lookup"><span data-stu-id="0af11-406">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="0af11-407">使用 <xref:System.Text.Json.JsonDocumentOptions> 可指定允许但会忽略输入 JSON 中的注释。</span><span class="sxs-lookup"><span data-stu-id="0af11-407">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="0af11-408">完成后，对编写器调用 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A>。</span><span class="sxs-lookup"><span data-stu-id="0af11-408">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="0af11-409">一种替代方法是让编写器在释放时自动刷新。</span><span class="sxs-lookup"><span data-stu-id="0af11-409">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="0af11-410">下面是要由示例代码处理的 JSON 输入的示例：</span><span class="sxs-lookup"><span data-stu-id="0af11-410">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="0af11-411">结果是以下进行了优质打印的 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="0af11-411">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="0af11-412">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="0af11-412">Use Utf8JsonWriter</span></span>

<span data-ttu-id="0af11-413">下面的示例演示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 类：</span><span class="sxs-lookup"><span data-stu-id="0af11-413">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="0af11-414">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="0af11-414">Use Utf8JsonReader</span></span>

<span data-ttu-id="0af11-415">下面的示例演示如何使用 <xref:System.Text.Json.Utf8JsonReader> 类：</span><span class="sxs-lookup"><span data-stu-id="0af11-415">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="0af11-416">前面的代码假设 `jsonUtf8` 变量是包含有效 JSON（编码为 UTF-8）的字节数组。</span><span class="sxs-lookup"><span data-stu-id="0af11-416">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="0af11-417">使用 Utf8JsonReader 筛选数据</span><span class="sxs-lookup"><span data-stu-id="0af11-417">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="0af11-418">下面的示例演示如何同步读取文件并搜索值：</span><span class="sxs-lookup"><span data-stu-id="0af11-418">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="0af11-419">前面的代码：</span><span class="sxs-lookup"><span data-stu-id="0af11-419">The preceding code:</span></span>

* <span data-ttu-id="0af11-420">假设 JSON 包含一个对象数组，并且每个对象都可能包含一个字符串类型的“name”属性。</span><span class="sxs-lookup"><span data-stu-id="0af11-420">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="0af11-421">对对象以及以“University”结尾的属性值进行计数。</span><span class="sxs-lookup"><span data-stu-id="0af11-421">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="0af11-422">假设文件编码为 UTF-16，并将它转码为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="0af11-422">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="0af11-423">可以使用以下代码，将编码为 UTF-8 的文件直接读入 `ReadOnlySpan<byte>`：</span><span class="sxs-lookup"><span data-stu-id="0af11-423">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="0af11-424">如果文件包含 UTF-8 字节顺序标记 (BOM)，请在将字节传递给 `Utf8JsonReader` 之前将它删除，因为读取器需要文本。</span><span class="sxs-lookup"><span data-stu-id="0af11-424">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="0af11-425">否则，BOM 被视为无效 JSON，读取器将引发异常。</span><span class="sxs-lookup"><span data-stu-id="0af11-425">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="0af11-426">下面是前面的代码可以读取的 JSON 示例。</span><span class="sxs-lookup"><span data-stu-id="0af11-426">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="0af11-427">生成的摘要消息为“2 out of 4 have names that end with 'University'”：</span><span class="sxs-lookup"><span data-stu-id="0af11-427">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="0af11-428">使用 Utf8JsonReader 从流中读取</span><span class="sxs-lookup"><span data-stu-id="0af11-428">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="0af11-429">当读取大型文件（例如，1 GB 或更大的文件）时，你可能希望避免一次性将整个文件加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="0af11-429">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="0af11-430">此时，可以使用 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="0af11-430">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="0af11-431">使用 `Utf8JsonReader` 从流中读取时，适用以下规则：</span><span class="sxs-lookup"><span data-stu-id="0af11-431">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="0af11-432">包含部分 JSON 有效负载的缓冲区必须至少与其中的最大 JSON 令牌一样大，以便读取器可以推进进度。</span><span class="sxs-lookup"><span data-stu-id="0af11-432">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="0af11-433">缓冲区的大小必须至少与 JSON 中的最大空格序列一样大。</span><span class="sxs-lookup"><span data-stu-id="0af11-433">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="0af11-434">读取器不会跟踪已读取的数据，直到它完全读取 JSON 有效负载中的下一个 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A>。</span><span class="sxs-lookup"><span data-stu-id="0af11-434">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="0af11-435">因此，当缓冲区中有剩余字节时，必须再次将它们传递给读取器。</span><span class="sxs-lookup"><span data-stu-id="0af11-435">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="0af11-436">你可以使用 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> 来确定剩余的字节数。</span><span class="sxs-lookup"><span data-stu-id="0af11-436">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="0af11-437">下面的代码演示了如何从流中读取。</span><span class="sxs-lookup"><span data-stu-id="0af11-437">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="0af11-438">本示例显示了 <xref:System.IO.MemoryStream>。</span><span class="sxs-lookup"><span data-stu-id="0af11-438">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="0af11-439">类似的代码将使用 <xref:System.IO.FileStream>，当 `FileStream` 在开头包含 UTF-8 BOM 时除外。</span><span class="sxs-lookup"><span data-stu-id="0af11-439">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="0af11-440">在这种情况下，需要先从缓冲区中去除这三个字节，然后再将剩余字节传递到 `Utf8JsonReader`。</span><span class="sxs-lookup"><span data-stu-id="0af11-440">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="0af11-441">否则，读取器将引发异常，因为 BOM 不被视为 JSON 的有效部分。</span><span class="sxs-lookup"><span data-stu-id="0af11-441">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="0af11-442">示例代码从 4KB 缓冲区开始，每当发现大小不足以容纳完整的 JSON 令牌（必须容纳完整的令牌，读取器才能推动处理 JSON 有效负载）时，就会使缓冲区大小成倍增加。</span><span class="sxs-lookup"><span data-stu-id="0af11-442">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="0af11-443">仅当设置的初始缓冲区非常小（例如 10 个字节）时，代码片段中提供的 JSON 示例才会触发缓冲区大小增加。</span><span class="sxs-lookup"><span data-stu-id="0af11-443">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="0af11-444">如果将初始缓冲区大小设置为 10，则 `Console.WriteLine` 语句会说明缓冲区大小增加的原因和影响。</span><span class="sxs-lookup"><span data-stu-id="0af11-444">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="0af11-445">在初始缓冲区大小为 4KB 时，每个 `Console.WriteLine` 都会显示整个示例 JSON，并且不必增加缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="0af11-445">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="0af11-446">前面的示例未对缓冲区大小的增长设置任何限制。</span><span class="sxs-lookup"><span data-stu-id="0af11-446">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="0af11-447">如果令牌大小太大，则代码可能会失败，并出现 <xref:System.OutOfMemoryException> 异常。</span><span class="sxs-lookup"><span data-stu-id="0af11-447">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="0af11-448">如果 JSON 包含大小约为 1 GB 或更大的令牌，则会发生这种情况，因为将 1 GB 大小加倍会导致令牌太大，无法放入 `int32` 缓冲区。</span><span class="sxs-lookup"><span data-stu-id="0af11-448">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0af11-449">其他资源</span><span class="sxs-lookup"><span data-stu-id="0af11-449">Additional resources</span></span>

* <span data-ttu-id="0af11-450">[System.Text.Json 概述](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="0af11-450">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="0af11-451">如何编写自定义转换器</span><span class="sxs-lookup"><span data-stu-id="0af11-451">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="0af11-452">[如何从 Newtonsoft.Json 迁移](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="0af11-452">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="0af11-453">[System.Text.Json 中的 DateTime 和 DateTimeOffset 支持](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="0af11-453">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="0af11-454">[System.Text.Json API 参考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="0af11-454">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
